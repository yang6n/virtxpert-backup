---
ID: 1120
post_title: Trying out Unitrends Enterprise Backup
author: Jonathan Frappier
post_date: 2013-07-08 09:31:09
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/trying-out-unitrends-enterprise-backup/
published: true
dsq_thread_id:
  - "1469928730"
---
I was first introduced to <a href="http://www.unitrends.com/unitrends-enterprise-backup/version-comparison" target="_blank">Unitrends </a>a few years ago I was looking for a new backup solution, while it wasn't the right fit for what I needed at the time they stayed on my radar and have watched the grow.  One of the things I like most about Unitrends is their ability to backup both virtual AND physical machines by using an agent based system.  While the trend for a while was to go agentless, the solutions I have found to be most stable are those which utilize agents.  There is a free version and NFR version available for smaller environments or the Enterprise edition for those with larger needs.  Another nice "feature" of the company is that they are engaged in the community, a very smart move for companies as you become positioned as a peer rather than a sales person.

Unitrends installs as a virtual appliance in either a vSphere or Hyper-V environment, a few years ago the primary appliance was actually a physical device you purchased through Unitrends.  Now for production purposes, you will still likely need some sort of storage appliance to store your backups on but you are free to chose what that platform is.  After the vApp is imported, the VM boots to a configuration screen where you can configure the network, console access, firewall settings and advanced options.  After a simple network configuration, you can now access the web based recovery console and configure the appliance.
<p style="text-align: center;"><a href="http://www.virtxpert.com/wp-content/uploads/2013/06/unitrendsconsole.png"><img class="aligncenter  wp-image-1123" alt="unitrendsconsole" src="http://www.virtxpert.com/wp-content/uploads/2013/06/unitrendsconsole.png" width="699" height="574" /></a></p>
In just a few minutes I went from a downloaded zip file, <!--more-->to importing the OVF, configuring the  network interface to having access to the console.  Next, the wizard brings you to Unitrends site to select your license.  In my case I had a promo code I used so while I wait for the license key I am using the free version for the remainder of the setup.  The wizard was very simple, configuring time settings, administrative users, SMTP settings etc...  You have the option for adding additional storage to the appliance, which for now I am skipping.  Now you have the option to install the agent on specific operating systems, in this case I am currently backing up only Windows servers but could also backup Linux, OSX, Unix, Novell (is anyone really stil using Netware?) and even Windows 2000/NT.

Now the interesting part; configuring your agents.  When prompted, click on the Add Client icon.  Here you can choose from supported OS's included the ones you had to manually install the agent on, adding of credentials to access the system (a required step not clearly called out IMO but certainly makes sense)  and even whether to encrypt the backups (however you cannot encrypt the backup as part of the initial Wizard (should probably just make a note and not a check box, or give me the option to setup my encryption keys as part of the wizard).  Once you have your server name or IP entered and created credentials click the setup button.  The setup was very quick even though I know the VM I installed the agent is a bit on the slow side.  In addition to installing a Windows agent, I wanted to see how Unitrends worked in a VMware vSphere environment and the configuration was extremely quick as well.
<p style="text-align: center;"><a href="http://www.virtxpert.com/wp-content/uploads/2013/06/vmsetup.png"><img class="aligncenter  wp-image-1124" alt="vmsetup" src="http://www.virtxpert.com/wp-content/uploads/2013/06/vmsetup.png" width="636" height="466" /></a></p>
<p style="text-align: left;">The last step was a few backup settings around retention and dedup.  Now in the Recovery Console I can see the Windows VM I added, including discovery of SQL server installed and my vCenter server.  For both SQL and vCenter I have an option to auto-include new databases and VM's which could come in very handy, I would rather backup to much than not enough!</p>
<p style="text-align: left;"><strong>Conclusion</strong></p>
<p style="text-align: left;">The installation was fantastic, very easy, no hiccups along the way.  In just about an hour, including the time it took the write this post, take screenshots, check my fantasy baseball line-ups and check in on NBA draft rumors I have a functional backup appliance in my environment.  In my next post I will fill you in on how the backups are doing.</p>