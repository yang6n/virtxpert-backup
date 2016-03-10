---
ID: 2591
post_title: Creating a new VM with EVO:RAIL
author: Jonathan Frappier
post_date: 2014-09-12 07:46:51
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/creating-new-vm-evorail/
published: true
dsq_thread_id:
  - "3011225759"
---
Creating a new VM, easy right?  Except when you consider that via the vSphere client it is somewhere in the <a title="Basic PowerCLI examples for common VMware vSphere Tasks" href="http://www.virtxpert.com/basic-powercli-examples-common-vmware-vsphere-tasks/">neighborhood of 40 mouse clicks</a>.  Log into your EVO:RAIL UI or VMware Hands-On lab at <a href="http://labs.hol.vmware.com/HOL/catalogs/lab/1503" target="_blank">http://labs.hol.vmware.com/HOL/catalogs/lab/1503</a>

<a href="http://www.virtxpert.com/wp-content/uploads/2014/09/evo-rail-login.jpg"><img class="aligncenter size-full wp-image-2593" src="http://www.virtxpert.com/wp-content/uploads/2014/09/evo-rail-login.jpg" alt="evo-rail-login" width="243" height="301" /></a>

Once logged in, familiarize your self with the UI.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/09/evo-nav.jpg"><img class="aligncenter  wp-image-2588" src="http://www.virtxpert.com/wp-content/uploads/2014/09/evo-nav.jpg" alt="evo-nav" width="827" height="467" /></a>

&nbsp;

Now that you have the basics, its time to create a VM.

<!--more-->
<ul>
	<li>Click the Create VM button (1) and enter the VM name in the "Create VM called" text box.  Now click (2) the Upload Image button.  Alternatively you could use a previously uploaded ISO or mount a network share where these are located.</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/09/evo-rail-create-vm.jpg"><img class="aligncenter  wp-image-2594" src="http://www.virtxpert.com/wp-content/uploads/2014/09/evo-rail-create-vm.jpg" alt="evo-rail-create-vm" width="748" height="359" /></a>
<ul>
	<li>The left side of the above menu will change, click the Choose File (3) button.  Double click (4,5) your ISO and click the Uplaod Image button (6).</li>
	<li>Once the image uplaods, click (7) the guest OS pull down, select (8) the appropriate OS and click (9) the continue button.</li>
	<li>Select your VM size (10) and click (11) the Select VM size button</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/09/evo-rail-select-vm-size.png"><img class="aligncenter size-full wp-image-2596" src="http://www.virtxpert.com/wp-content/uploads/2014/09/evo-rail-select-vm-size.png" alt="evo-rail-select-vm-size" width="881" height="345" /></a>

&nbsp;
<ul>
	<li>Click the check box (11) next to the network you wish to connect to and then click (12) the Select Networks button.  You can select multiple port groups here if you wish.</li>
	<li>The EVO:RAIL ui allows you to select a security profile based on the <a href="http://www.vmware.com/security/hardening-guides" target="_blank">vSphere 5.5 Security Hardening Guide </a>(nice feature add!).  Select a policy and click (13) the Create and Start a new VM.</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/09/evo-rail-vm-security.jpg"><img class="aligncenter size-full wp-image-2597" src="http://www.virtxpert.com/wp-content/uploads/2014/09/evo-rail-vm-security.jpg" alt="evo-rail-vm-security" width="941" height="455" /></a>

&nbsp;
<ul>
	<li>You'll be to monitor the progress of the new VM being created from the window you are currently in, or return to the dashboard and see that you have a new task running in the EVO:RAIL ui.</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/09/evo-rail-new-vm-monitor.jpg"><img class="aligncenter wp-image-2598" src="http://www.virtxpert.com/wp-content/uploads/2014/09/evo-rail-new-vm-monitor.jpg" alt="evo-rail-new-vm-monitor" width="506" height="245" /></a>
<p style="text-align: center;">or</p>
<p style="text-align: center;"><a href="http://www.virtxpert.com/wp-content/uploads/2014/09/evo-rail-new-vm-monitor.jpg"><img class="wp-image-2599 aligncenter" src="http://www.virtxpert.com/wp-content/uploads/2014/09/evo-rail-new-vm-monitor2.jpg" alt="evo-rail-new-vm-monitor2" width="360" height="246" /></a></p>

<ul>
	<li style="text-align: left;">Once completed you will see a message that the new VM has been created and is powering on.  Click on the VMS button in the EVO:RAIL UI to see your VM.  You rename, clone, pause, power off and can even launch the VMRC right from the EVO:RAIL UI (Or EVO:X for EVO Experience - create name Matt Brender!)</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/09/evo-rail-ui-nav-vm.jpg"><img class="aligncenter size-full wp-image-2600" src="http://www.virtxpert.com/wp-content/uploads/2014/09/evo-rail-ui-nav-vm.jpg" alt="evo-rail-ui-nav-vm" width="1009" height="388" /></a>

That's it....13 clicks.  Can't argue with the numbers; creating a VM in the EVO:RAIL really is simple!