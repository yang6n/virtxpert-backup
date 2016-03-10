---
ID: 4077
post_title: >
  Installing Windows Server 2016 and First
  Impressions
author: Jonathan Frappier
post_date: 2015-11-11 08:28:51
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/installing-windows-server-2016-and-first-impressions/
published: true
dsq_thread_id:
  - "4309219473"
---
In this post I will be installing Windows Server 2016 Technical Preview 3, as always with a technical preview or beta release post, items may change by GA. I am installing this in VMware Workstation 11 to go along with the rest of my nested home lab.

Create a new virtual machine as you normally would, when prompted for the Guest Operating System select Windows Server Threshold and place the virtual machine on your desired drive. For a first pass at Windows 2016, I will be giving it 2 vCPU and 4GB of RAM - I don't want the OS to lag to badly because of limited resources. When Windows 2016 GAs and can use it without fear of expiration, that will be the time to push how low it can go for certain services such as DHCP or to be a Domain Controller. The rest of your selections will depend on your desired configuration, for example all of my virtual machines are using NAT, so this was placed with the other lab virtual machines. Mount the <a href="https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-technical-preview" target="_blank">Windows 2016 ISO</a> to the VM and power it on.

The following is a high level installation process:
<ul>
	<li>Select your language and keyboard type</li>
	<li>Start the installation</li>
	<li>Windows OS type; either "core" (e.g. command line) or with "Desktop Experience" (e.g. the familiar Windows desktop GUI)</li>
	<li>Accept the EULA</li>
	<li>Type of installation - upgrade or custom. In the case of a new install you select Custom (which I never thought was very obvious)</li>
	<li>Select the installation device</li>
	<li>Sit back!</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/windows2016-install.png"><img class="aligncenter size-full wp-image-4081" src="http://www.virtxpert.com/wp-content/uploads/2015/11/windows2016-install.png" alt="windows2016-install" width="651" height="492" /></a>
<ul>
	<li>When the installation completes, set a password for the local administrator account</li>
</ul>
That's it, Windows is installed. Time to poke around. If you are familiar with Windows 8.1 or Server 2012 R2, the GUI is pretty much what you would expect. You will be prompted to connect to your network, if detected and server manager will fire up so you can do the initial configuration of the OS. A few interesting items
<ul>
	<li>IE Enhanced Security Configuration is off by default, not sure if that is a PR thing or its going away and not being ported to Edge</li>
	<li>You cannot launch Edge using the local administrator account (hooray!) so create your local, limited privilege users</li>
	<li>The Start menus is Windows 10ish, but not quite</li>
	<li>While things like IE/Edge change, some things stay the same..like the tool to create local users and Computer Management</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/computer-mgmt.png"><img class="aligncenter size-full wp-image-4083" src="http://www.virtxpert.com/wp-content/uploads/2015/11/computer-mgmt.png" alt="computer-mgmt" width="999" height="713" /></a>

Post install tasks for Windows don't look like they have changed much, you likely want to rename the administrator and guest accounts, create local accounts, and review local running services to ensure they are needed  - sorry Downloaded Maps Manager, you won't be running much longer!

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/map-manager.png"><img class="aligncenter size-full wp-image-4085" src="http://www.virtxpert.com/wp-content/uploads/2015/11/map-manager.png" alt="map-manager" width="696" height="495" /></a>

Of course, this is from the GUI perspective. I'll also be installing Core (if its still called that?) and reviewing the available PowerShell cmdlets.