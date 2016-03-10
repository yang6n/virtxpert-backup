---
ID: 2789
post_title: >
  VMware Workstation Home Lab Setup Part 7
  – Management Tools
author: Jonathan Frappier
post_date: 2014-11-08 08:00:11
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vmware-workstaion-home-lab-setup-part-7-management-tools/
published: true
dsq_thread_id:
  - "3204582958"
---
[display-posts category="Lab Series" display-posts posts_per_page="15"]

So now we've got two ESXi hosts and our domain controller running in the home lab, it's almost time to setup vCenter however, in a real world scenario you would need a way to get vCenter onto the ESXi hosts (because of course you are virtualizing vCenter).  Up until now what we have done through the DCUI would have been at a keyboard and mouse or virtual KVM (such as Cisco UCS or HP iLO) and we cannot create virtual machines via the DCUI.  So, what tools are available to manage our ESXi hosts to start creating virtual machines?

First, typically most people would start with the Windows vSphere Client.  This client can connect directly to an ESXi host and start creating virtual machines, such as a Windows virtual machine for vCenter or <a title="Installing the vCenter Server Appliance 5.5.0b #VCSA" href="http://www.virtxpert.com/installing-vcenter-server-appliance-5-5-0b/">importing virtual appliances such as the vCenter Server Appliance (VCSA)</a> which we will use in our lab set later on.  You can see all of my VCSA related posts below:

[display-posts category="VCSA"]

You can download the Windows vSphere client from the ESXi getting started page by navigating the IP address of one of your ESXi hosts (like was done in the last post at https://192.168.6.11).  If you are running Windows 8.x you will need to <a href="http://www.microsoft.com/en-us/download/details.aspx?id=15468" target="_blank">download a J++ package</a> and install it before proceeding with the Windows vSphere Client, <a href="http://itechthereforeiam.com/2013/12/quick-post-trouble-installing-vsphere-on-windows-8-1/" target="_blank">thanks to my friend Matthew Brender for reminding me</a> of that gotcha which also means you will need to turn on the .NET Framework 3.5.  To do so, open the Start menu, go to Control Panel &gt;&gt; Programs and Features and click Turn Windows features on or off.  Tick the .Net Framework 3.5 box and click OK

<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/enable-dotnet35-windows81.png"><img class="aligncenter  wp-image-2801" src="http://www.virtxpert.com/wp-content/uploads/2014/11/enable-dotnet35-windows81.png" alt="enable-dotnet35-windows81" width="360" height="315" /></a>

Once .NET 3.5 is enabled and J++ is installed, download the vSphere Client, run the installation wizard and log in to the IP address/host name of your ESXi host as root.

[caption id="attachment_2803" align="aligncenter" width="656"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/vsphere-client.png"><img class=" wp-image-2803" src="http://www.virtxpert.com/wp-content/uploads/2014/11/vsphere-client.png" alt="vSphere Client" width="656" height="510" /></a> vSphere Client[/caption]

Another option is to install <a href="http://blogs.vmware.com/PowerCLI/2014/03/new-release-vsphere-powercli-5-5-r2.html" target="_blank">PowerCLI</a>, which is based on PowerShell and <a href="http://www.slideshare.net/JonathanFrappier/providence-vmug-powercli?ref=https://www.linkedin.com/in/jonathanfrappier" target="_blank">very powerful with many options to manage both ESXi hosts, virtual machines</a> and more.  Again download and run through the PowerCLI installation wizard, it will install a few additional componenets as part of the install.  Once installed launch PowerShell as administrator (even if you are logged in as an administrator) and run
<pre>Set-ExecutionPolicy RemoteSigned</pre>
You should now be able to launch PowerCLI and run
<pre>Connect-VIServer 192.168.6.11</pre>
You will be prompted for a username and password and are then connected and can run cmdlets in PowerCLI to import or create new virtual machines.

[caption id="attachment_2805" align="aligncenter" width="671"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/powershell-powercli.png"><img class="wp-image-2805" title="PowerShell Set-ExecutionPolicy and PowerCLI" src="http://www.virtxpert.com/wp-content/uploads/2014/11/powershell-powercli.png" alt="powershell-powercli" width="671" height="475" /></a> PowerShell Set-ExecutionPolicy and PowerCLI[/caption]

Since we are using VMware Workstation, we can also use that to connect to the ESXi hosts (or a vCenter server later) as well.  In VMware Workstation, click on File &gt;&gt; Connect to server.  Enter the IP, username (root) and password to log in.  You can now create virtual machines on your virtual ESXi host running in VMware Workstation from VMware Workstation!

[caption id="attachment_2806" align="aligncenter" width="940"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/esxi-vmware-workstation.png"><img class="wp-image-2806 size-full" title="ESXi in VMware Workstation" src="http://www.virtxpert.com/wp-content/uploads/2014/11/esxi-vmware-workstation.png" alt="esxi-vmware-workstation" width="940" height="359" /></a> ESXi in VMware Workstation[/caption]

In the next post, we will use the vSphere Web Client and PowerCLI to import the vCenter Server Appliance for our home lab which will provide (obviously) vCenter, Single Sign-On (SSO) and the vSphere Web Client which is where we will do most of the work through this series.