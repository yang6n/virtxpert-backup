---
ID: 2136
post_title: 'PowerCLI &#8211; Update ESXi Root Password with Password Generator'
author: Jonathan Frappier
post_date: 2014-04-07 15:03:05
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/powercli-update-esxi-root-password-password-generator/
published: true
dsq_thread_id:
  - "2594042155"
---
Working on setting up a new cluster, I'm determined to do this inPowerCLI and not through the GUI (until I have to)!
<pre># Combination of scripts from:
# <a href="http://blogs.technet.com/b/heyscriptingguy/archive/2013/06/03/generating-a-new-password-with-windows-powershell.aspx" target="_blank">http://blogs.technet.com/b/heyscriptingguy/archive/2013/06/03/generating-a-new-password-with-windows-powershell.aspx</a>
# <a href="http://www.lucd.info/2012/01/15/change-theroot-password-in-hosts-and-host-profiles/" target="_blank">http://www.lucd.info/2012/01/15/change-theroot-password-in-hosts-and-host-profiles/</a>
# <a href="http://www.definit.co.uk/2013/06/changing-esxi-root-passwords-the-smart-way-via-powercli/" target="_blank">http://www.definit.co.uk/2013/06/changing-esxi-root-passwords-the-smart-way-via-powercli/</a>
# Thank you to The ScriptingGuys, Luc Dekens, Sam McGeown

# Create password generator
# Create varialbe with multiple characters for password generation
$ascii=$NULL;

For ($a=48;$a –le 122;$a++) {$ascii+=,[char][byte]$a}

# Password generator function using Get-Random
Function Get-Temppassword() {

Param
(
[int]$length=10,
[string[]]$sourcedata
)

For ($loop=1; $loop –le $length; $loop++) 
{
$TempPassword+=($sourcedata | GET-RANDOM)
}

return $TempPassword

}

# Set PowerCLI Options
$multiState = (Get-PowerCLIConfiguration).DefaultVIServerMode
$warnings = (Get-PowerCLIConfiguration).DisplayDeprecationWarnings
Set-PowerCLIConfiguration -DefaultVIServerMode Multiple -Confirm:$false -DisplayDeprecationWarnings:$false | Out-Null
Set-PowerCLIConfiguration -InvalidCertificateAction Ignore -Confirm:$false | Out-Null

# Collect VM Cluster information
$VCSrv = Read-Host "Enter the name of the vCenter Server"
$Cluster = Read-Host "Enter the name of the cluster"
$UserAcct = Read-Host "Enter the name of the account you want to change"
$CurrentPw = Read-Host "Enter the current password for that user"

# Setup log file stored in the folder the script is run from
$LogFile = "Change-HostPasswords.csv"
# Rename the old log file, if it exists
if(Test-Path $LogFile) {
	$DateString = Get-Date((Get-Item $LogFile).LastWriteTIme) -format MMddyyyy
	Move-Item $LogFile "$LogFile.$DateString.csv" -Force -Confirm:$false
}
# Add some CSV headers to the log file
Add-Content $Logfile "Date,Host,Password,Result"

# Get host inventory from cluster
Connect-VIServer $VCSrv
$ClHost = Get-Cluster $Cluster | Get-VMHost

# Disconnect from Cluster
Disconnect-VIServer $VCSrv -Confirm:$false

# Reset Password for root on each host in the cluster
ForEach ($VMHost in $ClHost)
{
Connect-VIServer -Server $VMHost.Name -User $UserAcct -Password $CurrentPw | Out-Null
$NewPw = Get-Temppassword -length 24 -sourcedata $ascii
Write-Output "$UserAcct Password on $VMHost changed to $NewPw"
Add-Content $Logfile ((get-date -Format "dd/MM/yy HH:mm")+","+$VMHost.Name+","+$NewPw+",Success")
Set-VMHostAccount -UserAccount root -password $NewPw
Disconnect-VIServer -Server $VMHost.Name -Confirm:$False
}

# Reconnect to original Cluster
Connect-VIServer $VCSrv -Confirm:$false</pre>