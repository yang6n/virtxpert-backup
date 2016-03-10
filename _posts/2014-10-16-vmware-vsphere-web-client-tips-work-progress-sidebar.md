---
ID: 2704
post_title: >
  VMware vSphere Web Client Tips – Work
  in Progress sidebar
author: Jonathan Frappier
post_date: 2014-10-16 11:40:44
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vmware-vsphere-web-client-tips-work-progress-sidebar/
published: true
dsq_thread_id:
  - "3123388561"
---
In the Windows vSphere Client, when a wizard comes up, you need to finish or cancel that current task - not so in the Web Client!  When start a wizard in the vSphere Web Client you can click outside of the wizard window back into the vSphere Web Client and your wizard window will disappear.  Let's take a look at an example, below is a screenshot of my lab, highlighted in red is the Work in Progress sidebar:

[caption id="attachment_2705" align="aligncenter" width="1141"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/10/vsphere-web-client-lab.png"><img class="wp-image-2705 size-full" src="http://www.virtxpert.com/wp-content/uploads/2014/10/vsphere-web-client-lab.png" alt="vSphere Web Client Work in Progress sidebar" width="1141" height="583" /></a> vSphere Web Client Work in Progress sidebar[/caption]

Now I can start a task, in this case the <strong>New Virtual Machine</strong> wizard

[caption id="attachment_2707" align="aligncenter" width="974"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/10/vsphere-web-client-new-virutal-machine.png"><img class="size-full wp-image-2707" src="http://www.virtxpert.com/wp-content/uploads/2014/10/vsphere-web-client-new-virutal-machine.png" alt="vSphere Web Client New Virtual Machine wizard" width="974" height="580" /></a> vSphere Web Client New Virtual Machine wizard[/caption]

Now, in the Windows C# classic vSphere client I would need to either finish, or cancel this task if I wanted to do something else.  In the web client, however I can simply click off the wizard back into main UI.  As you can see here, my New Virtual Machine wizard has been minimized into the Work in Progress side bar.

[caption id="attachment_2708" align="aligncenter" width="1119"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/10/vsphere-web-client-new-virutal-machine-work-in-progress.png"><img class="size-full wp-image-2708" src="http://www.virtxpert.com/wp-content/uploads/2014/10/vsphere-web-client-new-virutal-machine-work-in-progress.png" alt="vSphere Web Client New Virtual Machine wizard minimized to Work in Progress" width="1119" height="579" /></a> vSphere Web Client New Virtual Machine wizard minimized to Work in Progress[/caption]

Instead of having to restart the the wizard, I can minimize it to the Work in Progress sidebar, then click on the link in the work in progress window to bring it back, right where I left off.