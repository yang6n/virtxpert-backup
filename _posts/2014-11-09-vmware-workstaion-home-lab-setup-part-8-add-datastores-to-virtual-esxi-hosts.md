---
ID: 2808
post_title: 'VMware Workstation Home Lab Setup Part 8 – Add &#8220;Datastores&#8221; to virtual ESXi hosts'
author: Jonathan Frappier
post_date: 2014-11-09 08:00:56
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vmware-workstaion-home-lab-setup-part-8-add-datastores-to-virtual-esxi-hosts/
published: true
dsq_thread_id:
  - "3207358138"
---
[display-posts category="Lab Series" display-posts posts_per_page="15"]

Now that we know some of the tools that are available to manage ESXi hosts, lets use one to create a virtual machine, in this case importing a virtual appliance available as an OVF.  Before we do that, one tiny piece of business to take care of; creating a datastore for our virtual ESXi hosts.  In our home lab environment, adding a local datastore to an ESXi host is as easy as editing the virtual machine properties in VMware Workstation.  Right click on the ESXi virtual machine and select Settings; click the Add.. button at the bottom of the Settings window and select hard disk.  Follow the wizard to place the file in the desired location.

In my case I am going to create two additional drives on vxprt-esxi01 - one on my SSD Windows volume (40GB) , and 1 on the RAID0 (100GB), they will be named "gold" and "silver" in ESXi to represent performance of each.  Once each of the new hard disks have been added in VMware Workstation, we can launch the vSphere Client to create the datastores which could be used to store virtual machines.
<ul>
	<li>Open the vSphere Client, connect to 192.168.6.11 as root</li>
	<li>Select the host in the left navigation pane and then click the configuration tab</li>
	<li>Under Hardware, click on Storage</li>
	<li>Click on Rescan All... then click OK</li>
	<li>Click on Add Storage</li>
	<li>When the wizard launches, select Disk/LUN and click Next</li>
	<li>You should see your 40GB and 100GB LUNs you added in VMware Workstation (or whatever size you selected)</li>
	<li>Select the 40GB SSD LUN and click Next</li>
	<li>Select VMFS-5 and click Next, and Next again</li>
	<li>Enter a name for the datastore, I am using vxprt-esxi01-gold-local and vxprt-esxi01-silver-local</li>
	<li>Use the Maximum space available and click Next, then finish</li>
</ul>
Repeat the steps again for the 100GB "silver" LUN, you should now have two datastores available to your ESXi host.

[caption id="attachment_2814" align="aligncenter" width="821"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/esxi-local-datastore.png"><img class="size-full wp-image-2814" src="http://www.virtxpert.com/wp-content/uploads/2014/11/esxi-local-datastore.png" alt="ESXi Local Datastores" width="821" height="347" /></a> ESXi Local Datastores[/caption]

Later on this series we will see how to turn those into VSAN storage, for now its a location to review importing OVF's and creating other virtual machines.