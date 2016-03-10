---
ID: 2874
post_title: 'vMotion Setup &#8211; VMware Workstation Home Lab Setup Part 13'
author: Jonathan Frappier
post_date: 2014-11-12 11:00:40
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vmotion-setup-vmware-workstaion-home-lab-setup-part-13/
published: true
dsq_thread_id:
  - "3217746735"
---
[display-posts category="Lab Series" display-posts posts_per_page="15"]

So you've got vCenter up and running and hosts added, it's time to enable the cool things vCenter can do - namely vMotion, HA and DRS.  I've gone back and forth on how I wanted to present vMotion and networking in the home lab.  On one hand many existing deployments are likely running 1Gbps, though newer ones are likely to start with 10Gbps as prices have dropped.  After a quick Twitter chat I decided to move forward as I would if I had 10Gbps networking and not have separate physical interfaces in my host for different traffic types.

When we setup our ESXi templates there was only a single NIC, let's add a 2nd NIC to the VM's.  For purposes of this labs (and maybe I'm still old like this) I will keep my management network on a standard switch and my VM network and vMotion traffic on a distributed switch.
<ul>
	<li>Right click on your ESXi virtual machine and select settings</li>
	<li>Click the Add... button and select Network Adapter</li>
	<li>Select NAT, click Finish and click OK</li>
	<li>Restart the host from vCenter (right click and select reboot) or from the DCUI (F12 &gt;&gt; root password &gt;&gt; F11)</li>
</ul>
Once the ESXi virtual machine has been restarted, you should see two interfaces in the vSphere Web Client.  Repeat for your 2nd host.

[caption id="attachment_2880" align="aligncenter" width="846"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/esxi-2-nics.png"><img class="size-full wp-image-2880" src="http://www.virtxpert.com/wp-content/uploads/2014/11/esxi-2-nics.png" alt="Virtual ESXi hosts with two nics" width="846" height="423" /></a> Virtual ESXi hosts with two nics[/caption]

In the vSphere Web Client, click on the network tab in the navigator so we can create the VDS.
<ul>
	<li>Right click on dc01 and select New Distributed Port Groups...</li>
	<li>Name the port group vmotion and click next</li>
	<li>Keep the defaults and click next, then finish, we'll use this port group in a bit</li>
	<li>Right click on dc01 and select New Distributed Switch</li>
	<li>Name your switch, if you've not caught on yet I like short names so my VDS will be called vds0101 (Now wait I thought it was going to just be vds01...why 4 digits all of a sudden!  Easy, its VDS #1 (vds01) in datacenter 01 vds0101 :) )</li>
	<li>Select your VDS version, I will go with 5.5</li>
	<li>I'll keep defaults the rest of the way here even though I only have 1 uplink right now available in my hosts, next, next finish.</li>
	<li>Right click on the VDS and select Add and Manage Hosts</li>
	<li>Select Add Hosts and click Next</li>
	<li>Click the <span style="color: #00ff00;">+</span> New Hosts button</li>
	<li>Select both hosts, click OK then click Next</li>
	<li>Keep Manage Physical Adapters and Manage VMkernel adapters selected and click next</li>
	<li>If you've followed along here, you should have vmnic1 not connected to any switch so far, that is what we will use for the VDS uplink.  Select vmnic1, click assign uplink</li>
	<li>Assign to Uplink 1 and click OK; repeat for all hosts</li>
</ul>
[caption id="attachment_2881" align="aligncenter" width="663"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/vds-assign-uplink.png"><img class="size-full wp-image-2881" src="http://www.virtxpert.com/wp-content/uploads/2014/11/vds-assign-uplink.png" alt="VDS Assign Uplink" width="663" height="401" /></a> VDS Assign Uplink[/caption]
<ul>
	<li>With vmnic1 assigned to the VDS click next</li>
	<li>On step 5, Manage VMKernel network adapters, you will see that we only have the existing VMkernel adapters that are currently used for management on the standard switch, no worries we can create a VMkernel interface from this page that we will assign vMotion traffic to</li>
	<li>Select vxprt-esxi01 and click on <span style="color: #00ff00;">+</span> New Adapter</li>
	<li>Click the browse button, select vmotion and click OK, then click next</li>
	<li>Under enable services click the Enable vMotion Traffic checkbox and click Next</li>
	<li>Assign an IP address from your IP space, typically you have a separate VLAN defined for vMotion traffic on your switch so you might have a management IP address of 192.168.6.11 for vxprt-esxi01, my vMotion IP might be 192.168.7.11 (I like my last octet to match so vxprt-esx01 would always have a last octet of .11 in any VLAN it is a part of).  In this case I am going to jump into the 192.168.6.24x space so I will assign 192.168.6.141 to this interface, 192.168.6.142 for vxprt-esx02 and so on.  Again in the lab I'm not likely to have more than a few ESXi hosts so I'm not to worried about going into the 250s</li>
	<li>Repeat for vxprt-esxi02</li>
	<li>Make sure vmk0 is set to Do not migrate and click Next</li>
	<li>On the analyze impact it should be no impact, click next then finish</li>
</ul>
Your hosts will be added to the VDS and vMotion will be enabled on the newly created VMkernel adapter.  To test, I have created an empty virtual machine on vxprt-esxi02 in the silver datastore, I am going to vMotion and Storage vMotion that virtual machine to vxprt-esxi01.  Here you can see the screenshot

[caption id="attachment_2884" align="aligncenter" width="825"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/vm-esxi02.png"><img class="wp-image-2884 size-full" src="http://www.virtxpert.com/wp-content/uploads/2014/11/vm-esxi02.png" alt="vm-esxi02-before-vmotion" width="825" height="283" /></a> vm-esxi02-before-vmotion[/caption]
<ul>
	<li>Now, right click on the virtual machine and select migrate</li>
	<li>Select Change both the host and datastore (we don't have shared storage setup yet)</li>
	<li>Select the cluster and click next</li>
	<li>Select vxprt-esxi01 and click next</li>
	<li>Select vxprt-esxi01-silver-local and click next</li>
	<li>Click finish</li>
</ul>
You can see the progress of the vMotion in the Running Tasks window.  After a few minutes you should now see your virtual machine on vxprt-esxi01

[caption id="attachment_2885" align="aligncenter" width="827"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/vm-esxi01-after-vmotion.png"><img class="size-full wp-image-2885" src="http://www.virtxpert.com/wp-content/uploads/2014/11/vm-esxi01-after-vmotion.png" alt="VM on new host after vMotion" width="827" height="305" /></a> VM on new host after vMotion[/caption]