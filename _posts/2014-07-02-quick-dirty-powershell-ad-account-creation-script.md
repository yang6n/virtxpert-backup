---
ID: 2304
post_title: >
  Quick and dirty PowerShell AD account
  creation script
author: Jonathan Frappier
post_date: 2014-07-02 10:55:13
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/quick-dirty-powershell-ad-account-creation-script/
published: true
dsq_thread_id:
  - "2812321827"
---
I needed to setup various <del>service accounts</del> (http://technet.microsoft.com/en-us/library/ff641729%28v=ws.10%29.aspx) user account objects to run various applications and services for testing in my lab, after the 3rd right click &gt;&gt; New &gt;&gt; User I said to one of the many voices in my head - HEY SCRIPT THAT!

So, here it is, simple, basic, easy to edit.  I probably should change this to take input from a CSV file... and I probably will when I start typing service account names wrong.  Currently the OU path is hard coded, I hate typing that and I always put them in the same spot (again quick and dirty so don't judge - it gets the job done!)
<ul>
	<li>Prompts for a password to be used for all accounts created</li>
	<li>Prompts for a list a service account names to be created</li>
	<li>Loops though and creates all accounts entered, sets the password and enables the account.</li>
</ul>
Yes it is indented properly IRL, blame WordPress for the lack of indents here :)

<a href="http://www.virtxpert.com/wp-content/uploads/2014/07/powershell-new-aduser.png"><img class="aligncenter wp-image-2306 size-full" src="http://www.virtxpert.com/wp-content/uploads/2014/07/powershell-new-aduser.png" alt="powershell-new-aduser" width="881" height="250" /></a>

&nbsp;

<a href="http://www.virtxpert.com/wp-content/uploads/2014/07/powershell-new-aduser-proof.png"><img class="aligncenter size-full wp-image-2307" src="http://www.virtxpert.com/wp-content/uploads/2014/07/powershell-new-aduser-proof.png" alt="powershell-new-aduser-proof" width="485" height="336" /></a>
<pre>#Generic script to bulk create AD accounts. Prompts for service accounts and password to be used on all accounts.
#If need be, can be modified to created groups and add user accounts to groups.

#OU Path Variable, change to your desired location
$oupath = "OU=serviceaccounts,DC=lab2,DC=local"
#Password
$pw=(Read-Host "Enter the password (will be used for all accounts)")

#Get service account names
$svcaccts = @()
do
{
$input = (Read-Host "Enter service account name &amp; press enter (no value and enter to end)")
if ($input -ne '') {$svcaccts += $input}
}
until ($input -eq '')

ForEach ($svcacct in $svcaccts)
{
#Creates new account
New-ADUser -Name $svcacct -Path $oupath -CannotChangePassword $true -PasswordNeverExpires $true

#Sets account password
Set-ADAccountPassword -Identity $svcacct -NewPassword (ConvertTo-SecureString -AsPlainText $pw -Force)

#Enable account
Enable-ADAccount -Identity $svcacct
}
</pre>