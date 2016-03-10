---
ID: 2407
post_title: >
  Unable to install VMware Big Data
  Extension Plug-in 1.1 after removing BDE
  2.0
author: Jonathan Frappier
post_date: 2014-07-30 13:40:20
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/unable-install-vmware-big-data-extension-plug-1-1-removing-bde-2-0/
published: true
dsq_thread_id:
  - "2885984847"
---
tl;dr Version:  Don't trust version numbers on folder names.  I somehow had 2.0 plugin files in my 1.1 folder, so no matter how many times I installed/re-installed 1.1 it continued to use the 2.0 files.  Delete ALL vsphere.bigdataextension folders from c:\ProgramData\Vmware\vSphere Web Client\vc-packages\vsphere-client-serenity

I seem to have come across an odd bug in relation to the VMware Big Data Extensions appliance.  I had installed VMware BDE 2.0  in my lab, however I needed to use just 1.1.  As BDE comes as an appliance and web client plugin this should have been fairly straight forward.  Since I had already installed BDE 2.0 I removed the plugin using the Uninstall option on the install-plugin page.  Next  installed the 1.1 plugin using https://bde11.fqdn/install-plugin and provide it with the vCenter server information

<a href="http://www.virtxpert.com/wp-content/uploads/2014/07/bde-install.png"><img class="wp-image-2408 aligncenter" src="http://www.virtxpert.com/wp-content/uploads/2014/07/bde-install.png" alt="bde-install" width="537" height="342" /></a>

As you can see here the installation was successful from my BDE 1.1 appliance.  However, when I logged into vCenter I still have the BDE 2.0 plugin

<!--more-->

<a href="http://www.virtxpert.com/wp-content/uploads/2014/07/bde2.jpg"><img class="size-full wp-image-2409 aligncenter" src="http://www.virtxpert.com/wp-content/uploads/2014/07/bde2.jpg" alt="bde2" width="559" height="376" /></a>

To test further, I installed a VCSA, moved an ESXi host to the new vCenter and deployed BDE 1.1 there.  Then I installed the client plugin from the new BDE 1.1 server to both vCenters.  As you can see here I am still getting the 2.0 plugin from somewhere (that somewhere is coming) even though I deleted the 2.0 files from the Windows server.

<img class="aligncenter  wp-image-2410" src="http://www.virtxpert.com/wp-content/uploads/2014/07/bdeahh.png" alt="bdeahh" width="783" height="397" />

I realized at this point I missed a step in the BDE directions:  <a href="http://pubs.vmware.com/bde-1-1/index.jsp#com.vmware.bigdataextensions.admin.doc/GUID-D53A05EE-0524-4EAA-A5BF-F52810148E53.html" target="_blank">http://pubs.vmware.com/bde-1-1/index.jsp#com.vmware.bigdataextensions.admin.doc/GUID-D53A05EE-0524-4EAA-A5BF-F52810148E53.html</a> to also delete the folder from the vCenter server.  Upon viewing the folder I deleted the 2.0 folder and left the 1.1 folder - after all I wanted 1.1.  At this point I was still seeing the 2.0 plugin in vCenter.

I combed the /mob directory, local file system and registry thanks to a few folks on Twitter and removed some other file references but would continually receive the same BDE 2.0 client plugin.   As a last ditch effort I removed all BDE folder instances, including the 1.1 folder

<a href="http://www.virtxpert.com/wp-content/uploads/2014/07/empty-ishfolder.png"><img class="aligncenter size-full wp-image-2412" src="http://www.virtxpert.com/wp-content/uploads/2014/07/empty-ishfolder.png" alt="empty-ishfolder" width="453" height="167" /></a>

&nbsp;

Now when I deploy the 1.1 plugin I get the correct version.  The plug-in installer appears to push the 2.0 files into the 1.1 folder even though they were/are labeled separately!

&nbsp;