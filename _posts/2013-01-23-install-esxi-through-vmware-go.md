---
ID: 381
post_title: Install ESXi through VMware Go
author: Jonathan Frappier
post_date: 2013-01-23 15:58:47
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/install-esxi-through-vmware-go/
published: true
jabber_published:
  - "1358974727"
email_notification:
  - "1358974744"
reddit:
  - 'a:2:{s:5:"count";i:0;s:4:"time";i:1359052849;}'
publicize_twitter_user:
  - jfrappier
dsq_thread_id:
  - "1081767668"
---
Since the folks over at the VMware Go team liked my first post so much, I figured I'd oblige and write up an article about how to install ESXi through VMware Go since they tweeted about it before I actually wrote it :)

VMware Go, for those that missed the last post, is a cloud based service for small businesses and new VMware admins to help manage and setup their VMware environment.  There are "two" ways to install ESXi from VMware go - by converting an existing Windows server/machine or downloading the ISO and installing manually.  The later isn't really installing "through" VMware Go but certainly a viable path, and then you can simply add the host once your install is finished.

Once logged into VMware Go, click on the Virtual tab and select Install an ESXi Hypervisor from the drop down menu.

<a href="http://jonathanfrappier.files.wordpress.com/2013/01/installesxi.jpg"><img class="aligncenter size-large wp-image-382" alt="installesxi" src="http://jonathanfrappier.files.wordpress.com/2013/01/installesxi.jpg?w=1024" width="1024" height="557" /></a>

Click the Get Started button on the next screen and provide the IP address of the Windows server you wish to convert and click the Next button.

<a href="http://jonathanfrappier.files.wordpress.com/2013/01/installip.jpg"><img class="aligncenter size-large wp-image-383" alt="installIP" src="http://jonathanfrappier.files.wordpress.com/2013/01/installip.jpg?w=1024" width="1024" height="427" /></a>

VMware Go will connect to the IP address of the computer to determine if it is compatible, when prompted enter the username and password for that server.  The machine I tried to install on failed the compatibility check as you can see here:

<a href="http://jonathanfrappier.files.wordpress.com/2013/01/hardwarefail.jpg"><img class="aligncenter size-full wp-image-384" alt="hardwarefail" src="http://jonathanfrappier.files.wordpress.com/2013/01/hardwarefail.jpg" width="628" height="645" /></a>

Thankfully I am doing this in a VM so one second while I go reconfigure that machine...and we are back and the machine passed the test this time as you can see:

<a href="http://jonathanfrappier.files.wordpress.com/2013/01/hardwarepass.jpg"><img class="aligncenter size-full wp-image-385" alt="hardwarepass" src="http://jonathanfrappier.files.wordpress.com/2013/01/hardwarepass.jpg" width="825" height="588" /></a>

I popped in my hostname and opted for DHCP config.  Make sure you pay attention to the warning - Windows will be gone!  Make sure you backed up your data, settings etc... if you need anything from this server and click next.  You will see a summary of the actions to be taken.  If you are ready to take the plunge, click the Start ESXi Hypervisor Installation!

<a href="http://jonathanfrappier.files.wordpress.com/2013/01/start.jpg"><img class="aligncenter size-large wp-image-386" alt="start" src="http://jonathanfrappier.files.wordpress.com/2013/01/start.jpg?w=1024" width="1024" height="341" /></a>After confirming you will blow away your Windows install, you will be prompted for the ESXi password you wish to set, and then need to enter the Windows credentials again.  You can see the task/download/install progress at the top of the screen:

<a href="http://jonathanfrappier.files.wordpress.com/2013/01/download.jpg"><img class="aligncenter size-full wp-image-387" alt="download" src="http://jonathanfrappier.files.wordpress.com/2013/01/download.jpg" width="628" height="339" /></a>

Queue on hold music in your head....daaa na na naa naa na.  Less than 20 minutes and a few reboots later I had an ESXi screen where my Windows login screen once appeared and can see the task completed in VMware Go.

<a href="http://jonathanfrappier.files.wordpress.com/2013/01/taskdone.jpg"><img class="aligncenter size-full wp-image-389" alt="taskdone" src="http://jonathanfrappier.files.wordpress.com/2013/01/taskdone.jpg" width="298" height="286" /></a>

&nbsp;

VMware Go was even nice enough to add it to its inventory for me!  So thats it, without ever touching an ISO I nuked my Windows server and turned it into a functional ESXi server!.