---
ID: 2781
post_title: >
  VMware Workstation Home Lab Setup Part 6
  – Cloning ESXi
author: Jonathan Frappier
post_date: 2014-11-07 08:00:57
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vmware-workstaion-home-lab-setup-part-6-cloning-esxi/
published: true
dsq_thread_id:
  - "3201444302"
---
[display-posts category="Lab Series" display-posts posts_per_page="15"]

Now that we have finished building the template for our ESXi hosts used in our home lab setup, it's time to start cloning.  The process is not all that different from cloning the Windows virtual machine we did earlier, so a quick overview:
<ul>
	<li>In VMware Workstation, right click on your ESXi template virtual machine (if you've been following along it should be vxprt-esxi-tmp) &gt;&gt; Manage &gt;&gt; Clone</li>
	<li>Follow through the wizard, selecting Clone from "An existing snapshot..." and "Create a linked clone"</li>
	<li>Name your VM accordingly and place it in the desired folder/drive.  I will name my ESXi virtual machines vxprt-esxi## so my first will be vxprt-esxi01</li>
	<li>Once the clone finishes, close the wizard, move the VM into your desired folder (if you are using folders) and power it on</li>
</ul>
After a few moments, our ESXi virtual machine will be powered on.  Once it is clone, my preference is to give my ESXi hosts static IP addresses.  Before doing that, log into your Domain Controller, open DNS manager and create A records for each of the ESXi virtual machines you plan to create by right clicking on the forward lookup zone for your domain and selecting New Host (A or AAA)...  My IP scheme will be:

192.168.6.2 - Default gateway
192.168.6.5 - Domain Controller
192.168.6.6 - vCenter / SSO
192.168.6.7 - SQL
192.168.6.8 - 10 - Open
192.168.6.11 - vxprt-esxi01 (last number matching the last number of the IP address)
192.168.6.12 - vxprt-esxi02
... and so on...
192.168.6.19 - vxprt-esxi09 (though I will likely not go this high)

With A records taken care of we now need to log into the DCUI and set the IP address.
<ul>
	<li>Click into the console of the ESXi virtual machine and press F2</li>
	<li>Log in as root</li>
	<li>Arrow down to Configure Management Network and press Enter</li>
	<li>Arrow down to IP Configuration and press Enter</li>
	<li>Arrow down to select the Set static IP option and press the space bar to select it</li>
	<li>Arrow down and set the IP Address, Subnet Mask and Default Gateway fields then press Enter</li>
	<li>Arrow down to DSN configuration and press Enter</li>
	<li>Set the primary DNS server to the IP address of your Domain Controller, in my case 192.168.6.5, change the hostname to vxprt-esxi01.vxprt.local and press Enter</li>
	<li>Press the ESC key, then press Y to confirm the changes and restart the management network</li>
	<li>Arrow down to Test Management Network and press Enter and press Enter again</li>
	<li>All 3 tests should pass successfully, if not review the previous steps to ensure you have the correct gateway, DNS IP and host name</li>
</ul>
[caption id="attachment_2784" align="aligncenter" width="611"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/esxi-dcui-test-management-network.png"><img class="size-full wp-image-2784" src="http://www.virtxpert.com/wp-content/uploads/2014/11/esxi-dcui-test-management-network.png" alt="ESXi DCUI test management network results" width="611" height="220" /></a> ESXi DCUI test management network results[/caption]

Repeat the process for at least 1 more ESXi hosts so we can form a cluster once you have installed vCenter.  You can press ESC to return to the main DCUI screen.  You should now be able to navigate with a web browser to 192.168.6.11 and download the vSphere Client.

[caption id="attachment_2787" align="aligncenter" width="640"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/esxi-web-page.png"><img class="size-large wp-image-2787" src="http://www.virtxpert.com/wp-content/uploads/2014/11/esxi-web-page-1024x418.png" alt="ESXi web page" width="640" height="261" /></a> ESXi web page[/caption]