---
ID: 1737
post_title: Installing EMC Avamar Virtual Edition
author: Jonathan Frappier
post_date: 2013-12-31 13:32:27
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/installing-emc-avamar-virtual-edition/
published: true
dsq_thread_id:
  - "2084099681"
---
Folks who know me are aware of my fondness for Networker, as such I'm looking at what the right platform is given our requirements, backup some VMs and backup some CIFS shares - pretty basic stuff which EMC Avamar should support.  Deploying Avamar Virtual Edition is actually pretty easy, however EMC won't give out the keys so you need to do this through an EMC POC or your VAR.

<strong>This is my plead to EMC, open it up, let people get their hands on it.  I can download trials of Veeam, Unitrends, Backup Exec - let people get their hands on your software.  Document it well and you are golden!</strong>

The install as I said, while not completely documented here because of some information only EMC/VARs have, was very straight forward.  The only gotcha is Avamar VE supports about 4TB of total backup size and, to deploy the Avamar VE appliance you'll need at least <strong>750GB</strong> of available disk space.  I couldn't convince the engineer I was working with to let me do thin provisioned, maybe he knows something I don't but in any case its been added to the VM.
<ul>
	<li>Download the OFV template from EMC (you'll need EMC or your VAR for this)</li>
	<li>While this is downloading, identify the necessary IP information.  Avamar VE deploys with a single virtual NIC, so 1 IP on your network and create the DNS entries on your server</li>
	<li>Deploy the OVF, selecting Thick provision, lazy zeroed for your initial 100GB disk</li>
	<li>Once the OVF deploys, verify the memory and vCPU sizing for your deployment (again, info my VAR had)</li>
	<li>In my case, I added 3 250GB thick provisioned, lazy zeroed disk to the initial 100GB needed for the install.</li>
	<li>Once completed, power on your VM and log into the console</li>
	<li>Once logged in as root, run yast to configure the IP settings - IP, subnet mask, DNS and host name
<ul>
	<li>*IP configuration is not part of the OVF deployment, though in theory it could be which is something I'd suggest for a future release.</li>
</ul>
</li>
	<li>Reboot the VM and log back in as root</li>
</ul>
My apologies here as this is where it gets a little grey because I do not have the documentation on deploying Avamar but the last few steps are essentially:
<ul>
	<li>2-3 shell scripts to build and install the Avamar software on the VM</li>
	<li>Log into the Avamar GUI at https://hostname:8543/avi/avigui.html and click on the lock icon in the upper right hand corner.  You'll need a tech support password here (again from EMC or your VAR)</li>
	<li>Avamar downloads some packages, updates and starts a configuration wizard.</li>
	<li>Fill in the items marked with an exclamation point and click save/continue.</li>
</ul>
<strong>Summary</strong>

At this point, Avamar runs through a setup and configuration process, roughly 1-2 hours.  That might be one of the easier installs I have ever had to do.  I hope someone in the EMC Backup and Recovery group gives some serious consideration to making what looks to be their best backup product (at least from the marketing website) available for people to use.  They have apparently made quite a bit of headway in autoamting the installation process from older versions, which I hope is a step towards making this product available for others to test.  In my next post (it's still installing right now) I'll configure Avamar to backup VMs, hopefully CIFS shares and hopefully add an alternate backup location other than the local disks.