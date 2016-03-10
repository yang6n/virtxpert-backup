---
ID: 2184
post_title: 'PowerCLI &#8211; Add cluster hosts to existing virtual distributed switch'
author: Jonathan Frappier
post_date: 2014-04-25 12:00:26
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/powercli-add-cluster-hosts-to-existing-virtual-distributed-switch/
published: true
dsq_thread_id:
  - "2638476080"
---
I started writing this script for mostly greenfield deployments to add all hosts in a cluster to a virtual distributed switch, but it could also be used when adding a new group of servers to vCenter or a cluster.  I haven't added logic to check if the host already has be added to the VDS or not - I'll do that soon (maybe) so right now it will just throw an error.  I also plan on adding the creation of the VDS, maybe I'll do that in a separate script.

The script prompts for the vCenter name, the list of vmnics to add as uplinks and local ESXi user since adding the uplinks is done on a per host basis.   This script currently assumes there is one existing VDS, but could be easily(?) modified to use a specific VDS if there were more than one or add additional nested loop to add hosts to multiple VDS.

You can see here one of my hosts I used for testing with the VDS and uplinks added.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/04/vdswitch-from-powercli.png"><img class="aligncenter size-full wp-image-2185" src="http://www.virtxpert.com/wp-content/uploads/2014/04/vdswitch-from-powercli.png" alt="vdswitch-from-powercli" width="572" height="236" /></a>
<pre># Script to create, and add all hosts in a Cluster to a VDS, create port groups and add uplinks/VMkernel interfaces
# The driver behind this script is to not have to place hosts into maintenance mode as you would with host profiles
# Logging portion thanks to Sam McGeown http://www.definit.co.uk/2013/06/changing-esxi-root-passwords-the-smart-way-via-powercli/
# Config maximum notes: http://www.vmware.com/pdf/vsphere5/r55/vsphere-55-configuration-maximums.pdf
# - Max ports per host: 4096
# - Max active ports per host: 1016
# - Max port groups per vDS: 6500
# - Max ports per vDS/vCenter: 60000
# - Max VDS per vCenter: 128
# - Max VDS per hots: 16
# - Max LAG per host/vDS: 64
# - Max Uplinks per LAG: 32
# - NIOC Resource Pools per vDS: 64

# Set PowerCLI Options
Set-PowerCLIConfiguration -InvalidCertificateAction Ignore -Confirm:$false | Out-Null

# Collect information
$VCSrv = Read-Host "Enter the name of the vCenter Server"
$VCCl = Read-Host "Enter the name of the cluster"

#Connect to vCenter for inventory
Connect-VIServer $VCSrv
$ClHost = Get-Cluster $VCCl | Get-VMHost
$VDSw = Get-VDSwitch
$UserAcct = Read-Host "Enter the host user account to connect directly to ESXi hosts (typically root)"
$UplinkCount = $VDSw.NumUplinkPorts

Write-Host "$VDSw currently has $UplinkCount uplinks"
# Collect vmnics to add as uplinks into an array
$VMNICS = @()
do {
$input = (Read-Host "Enter the VMNIC name and press enter (just enter to end)")
if ($input -ne '') {$VMNICS += $input}
}
until ($input -eq '')

# Setup log file stored in the folder the script is run from
$LogFile = "Update-HostNetworking.csv"
# Rename the old log file, if it exists
if(Test-Path $LogFile) {
$DateString = Get-Date((Get-Item $LogFile).LastWriteTIme) -format MMddyyyy
Move-Item $LogFile "$LogFile.$DateString.csv" -Force -Confirm:$false
}
# Add some CSV headers to the log file
Add-Content $Logfile "Date,Host,Status"

# Add each host in the Cluster to the Distributed Switch
ForEach ($VMHost in $ClHost)
{
# Add hosts to the VDS
Get-VDSwitch -Name $VDSw | Add-VDSwitchVMHost -VMHost $VMHost
}

# Disconnect from Cluster as commands to add uplinks are per host
Disconnect-VIServer $VCSrv -Confirm:$false

# Add uplinks for each host to VDS
ForEach ($VMHost in $ClHost)
{
# Get Host Password
$HostPW = Read-Host "Enter the $UserAcct password for $VMHost.Name"

# Connect to host, host PW in quotes to account for special characters
Connect-VIServer -Server $VMHost.Name -User $UserAcct -Password "$HostPW" | Out-Null

# Add uplinks for the host to the VDS
ForEach ($VMNIC in $VMNICS)
{
$vmhostNetworkAdapter = Get-VMHost $VMHost | Get-VMHostNetworkAdapter -Physical -Name $VMNIC
Get-VDSwitch $VDSw | Add-VDSwitchPhysicalNetworkAdapter -VMHostNetworkAdapter $vmhostNetworkAdapter -Confirm:$false
}

# Update log file
Add-Content $Logfile ((get-date -Format "dd/MM/yy HH:mm")+","+$VMHost.Name+",Success")

# Disconnect from host
Disconnect-VIServer $VMHost.name -Confirm:$false
}
</pre>