---
ID: 399
post_title: >
  Notes for installing VMware Tools in
  Ubuntu 12.10 in VMware Workstation
author: Jonathan Frappier
post_date: 2013-02-07 10:27:16
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/notes-for-installing-vmware-tools-in-ubuntu-12-1-in-vmware-workstation/
published: true
dsq_thread_id:
  - "1070539016"
---
Because why would I use the spare time to prepare for my VCAP-DCD test coming up in 2 weeks...
<ul>
	<li>When you create the VM, select "I will install the OS later"</li>
	<li>Install as you normally would (like the notification bar at the bottom says)</li>
	<li>After you reboot, click on VM, Install VMware Tools</li>
	<li>Extract to the location of your preference</li>
	<li>Open a terminal session, run sudo -passwd to set the password</li>
	<li>Navigate to the folder where you extracted VMware Tools</li>
	<li>Run sudo -c ./vmwaretoolsinstallname.pl</li>
	<li>Follow the install script</li>
</ul>
&nbsp;