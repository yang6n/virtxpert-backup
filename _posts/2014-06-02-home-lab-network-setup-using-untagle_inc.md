---
ID: 2243
post_title: >
  Home lab network setup using
  @Untagle_Inc
author: Jonathan Frappier
post_date: 2014-06-02 09:39:08
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/home-lab-network-setup-using-untagle_inc/
published: true
dsq_thread_id:
  - "2724444850"
---
This is the next post in my home lab setup.  When I set out to build the <a title="8-Core, 32GB RAM, 240GB Flash Home Lab Hardware Assembly" href="http://www.virtxpert.com/8-core-32gb-ram-240gb-flash-home-lab-hardware-assembly/">8-core/32GB</a> nested home lab my goal was to have as little equipment as possible yet still allow me have at least a couple of host running ESXi (1 physical, n virtual) along with vCenter.  For me, connecting my host to the internet wasn't the easiest because I wanted access to the physical host running my nested hosts and other VMs for "console" access and my router is in the basement and the person who built my house screwed up the CAT6 wiring.

In my office I have my "home" computer which has a single physical LAN adapter as well as a WLAN adapter which is how the computer connects to the internet.  My physical host has multiple multi-port LAN adapters but no way for me to connect it to the physical network without putting it next to the router (which I wanted to avoid) so I decided to setup a virtual router running in VMware Workstation on my home computer.  In this setup, my requirements were quite basic - I wanted my "isolated" lab network to have internet access.  Speed was a secondary concern, I can live with it being a bit slow.

When all is setup, the network will look something like:

<a href="http://www.virtxpert.com/wp-content/uploads/2014/05/lab-network.jpg"><img class="aligncenter  wp-image-2245" src="http://www.virtxpert.com/wp-content/uploads/2014/05/lab-network.jpg" alt="lab-network" width="678" height="509" /></a>

The first step was to configure networking properly in VMware workstation so I could connect the virtual NICs to the correct network; the "isolated" lab network and my "external" home network which then routed to the internet.  To configure VMware Workstation do the following:
<ul>
	<li>Click on Edit &gt;&gt; Virtual Network Editor...</li>
	<li>You should have VMnet0, VMnet1 and VMnet8 (I'll go over adding VMnet8 just in case)</li>
	<li>Click on VMnet0 and select the "Bridged" radio button</li>
	<li>In the "Bridge to:" pull down select your LAN adapter, in my case an Intel 1GbE Network Connection</li>
	<li>If VMnet8 already exists, click on and select the "Bridge" radio button
<ul>
	<li>If not click the Add Network... button</li>
	<li>Select VMnet8 (or any one really) and click OK</li>
</ul>
</li>
	<li>In the "Bridge to:" pull down select your LAN adapter, in my case a Linksys AE1000</li>
	<li>The Virtual Network Editor window should resemble this:</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/05/vne.png"><img class="aligncenter size-full wp-image-2247" src="http://www.virtxpert.com/wp-content/uploads/2014/05/vne.png" alt="vne" width="601" height="538" /></a>

With the networking setup properly in VMware Workstation, you can now move on to downloading the <a href="http://www.untangle.com/store/get-untangle/" target="_blank">Untangle ISO</a> and create a new VM.
<ul>
	<li>In VMware Workstation, click on File &gt;&gt; New Virtual Machine</li>
	<li>Using Typical is fine, click Next</li>
	<li>Select Installer disc image file (iso) and browse to where you saved the <a href="http://www.untangle.com/store/get-untangle/" target="_blank">Untangle ISO</a>, with the ISO path selected, click Next</li>
	<li>Name your VM to whatever your preference is, I named my v-gw01 (virtual gateway #1) and click Next</li>
	<li>I prefer to keep my VMDK's as a single file, but whatever works for you here, click Next</li>
	<li>Click the Customize Hardware... button</li>
	<li>Click on Network Adapter / NAT, select Custom: Specific virtual network and select VMnet8 which is the home network that has access to the internet</li>
	<li>Click on the Add... button, select Network Adapter; click Next, select Custom: Specific virtual network and select VMnet0 which is our isolated lab network; click Finish</li>
	<li>Click Close, make sure Power on this virtual machine after creation is selected (nothing else to do so why not) and click Finish.</li>
</ul>
The VM will now boot and start the Untagle installation.  The Untangle installation is quite simple; by default it assigns eth0 as the "External" network which, in this case, is my home 192.168.1 network and eth1 as the "Internal" network which in my setup is my LAN port connected to a switch with my physical host on the 10.11.12.x/24 network.  For my Untangle VM I used 192.168.1.254 as the eth0 IP and 10.11.12.254 as the eth1 IP.  Once finished, set the  VMkernel Default Gateway to 10.11.12.254 (<strong>vSphere Client &gt;&gt; Host &gt;&gt; Configuration &gt;&gt; DNS and Routing</strong>).  With the Default Gateway of the host configured, I can now ping resources on the internet as seen from my SSH session to my host.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/05/ping-host-8888.png"><img class="aligncenter size-full wp-image-2248" src="http://www.virtxpert.com/wp-content/uploads/2014/05/ping-host-8888.png" alt="ping-host-8888" width="672" height="169" /></a>

Depending on how fancy I get with networking on the ESXi side, I will likely setup another Untangle VM on the host with interfaces for each of my VLANs/networks.  Any VM (nested ESXi or otherwise) connected to the 10.11.12.x/24 network needs to just have the gateway set as 10.11.12.254 in order to access the internet (of course with working DNS).