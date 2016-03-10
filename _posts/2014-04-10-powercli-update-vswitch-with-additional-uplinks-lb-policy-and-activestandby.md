---
ID: 2149
post_title: 'PowerCLI &#8211; Update vSwitch with additional uplinks, LB Policy and active/standby'
author: Jonathan Frappier
post_date: 2014-04-10 09:59:11
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/powercli-update-vswitch-with-additional-uplinks-lb-policy-and-activestandby/
published: true
dsq_thread_id:
  - "2601378923"
---
Trying to configure some vSwitches via PowerCLI, as I am trying to learn I am looking a the command references and walking through each one by one, and found one that needs a bit of stringing together.  So in this scenario I have the basics setup on each ESXi host with the management network configured on vmic0 via the DCUI post the initial installation .  With that done, each were added to vCenter so now I wanted to add  another uplink for redundancy.
<pre>Get-VMHost hostname | Get-VirtualSwitch -name vSwitch0 | Set-VirtualSwitch -Nic vmnic0, vmnic1</pre>
All looked swimmingly well, but I expected my warnings about not having management network redundancy to disappear - it did not.  Looking at the vSwtich, the Management Network port group, vmnic1 was unused for the management network port group since the Failover order override box was ticked, presumably done during the initial setup since I selected vmnic0 via the DCUI.  So adding the vmnics was pretty easy, but setting the failover order and load balancing policy not quite as straight forward.

The command to change the failover order, and update the load balancing policy looks like this:
<pre>Get-VirtualSwitch -VMHost $VMHost -name $VSSName | Get-VirtualPortGroup | where {$_.Name -like "$PortGroupName"} | Get-NicTeamingPolicy | Set-NicTeamingPolicy -MakeNicActive $ActUplink -MakeNicStandby $StdByUplink -LoadBalancingPolicy $LBPol</pre>
So, first I am getting the virtual switch from a specific host, get the virtual port group for the specified port group, then getting the NIC teaming policy before setting it.  Here is the script I used which looped through all the hosts in my cluster to configure this.   It should be re-usable for any port group, on any vSwitch with any type of load balancing policy but I've not tested so use at your own risk!  I also want to update the logging logic a bit but time, reasons, and things.
<pre># Script to create update default vSphere Standard vSwitch on all hosts in a cluster to have redundant uplinks in an Active/Standby configuration
# Logging portion thanks to Sam McGeown http://www.definit.co.uk/2013/06/changing-esxi-root-passwords-the-smart-way-via-powercli/

# Set PowerCLI Options
Set-PowerCLIConfiguration -InvalidCertificateAction Ignore -Confirm:$false | Out-Null

# Collect VM Cluster information
$VCSrv = Read-Host "Enter the name of the vCenter Server"
$VCCl = Read-Host "Enter the name of the cluster"
$VSSName = Read-Host "Enter the name of the vSwitch containing the Management Network port group"
$ActUplink = Read-Host "Enter the name of the vmnic that will be active"
$StdByUplink = Read-Host "Enter the name of the vmnic that will be standby"
$LBPol = Read-Host "Enter the load balance policy (LoadBalanceIP, LoadBalanceSrcMac, LoadBalanceSrcId, ExplicitFailover)"
$PortGroupName = Read-Host "Enter the name of the port group you wish to update"

# Setup log file stored in the folder the script is run from
$LogFile = "Change-HostvSwitch.csv"
# Rename the old log file, if it exists
if(Test-Path $LogFile) {
$DateString = Get-Date((Get-Item $LogFile).LastWriteTIme) -format MMddyyyy
Move-Item $LogFile "$LogFile.$DateString.csv" -Force -Confirm:$false
}
# Add some CSV headers to the log file
Add-Content $Logfile "Date,Host,Status"

# Get host inventory from cluster
Connect-VIServer $VCSrv
$ClHost = Get-Cluster $VCCl | Get-VMHost

# Change the uplinks and load balancing policy on each host in the cluster with the provided information
ForEach ($VMHost in $ClHost)
{
# Set uplinks for the vSwitch
Get-VMHost $VMHost | Get-VirtualSwitch -Name $VSSName | Set-VirtualSwitch -Nic $ActUplink,$StdByUplink -Confirm:$false

# Set active and standby uplinks
Get-VirtualSwitch -VMHost $VMHost -name $VSSName | Get-VirtualPortGroup | where {$_.Name -like "$PortGroupName"} | Get-NicTeamingPolicy | Set-NicTeamingPolicy -MakeNicActive $ActUplink -MakeNicStandby $StdByUplink -LoadBalancingPolicy $LBPol

# Update log file
Add-Content $Logfile ((get-date -Format "dd/MM/yy HH:mm")+","+$VMHost.Name+",Success")

}</pre>