---
ID: 2955
post_title: >
  Setting up NFS on the Synology
  Diskstation 1513+ for ESXi
author: Jonathan Frappier
post_date: 2014-11-15 09:00:24
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/setting-nfs-synology-diskstation-1513/
published: true
dsq_thread_id:
  - "3227532663"
---
[display-posts category="Synology NAS Series"]

I was going to do a post on NFS versus iSCSI, to be honest that is such old hat in my opinion it doesn't really matter.  Whether you use iSCSI or NFS is up to you, your application and business requirements along with any constraints in your infrastructure that may force you to lean one way or another.  Since I am an NFS networking ninja, clearly I am going to go the NFS route.  Let's get started on setting up NFS, if you are not already log into your Synology DSM.
<ul>
	<li>Click on the main menu button on the upper left and open Control Panel</li>
	<li>Click on the File Services icon</li>
	<li>I have no need for CIFS or AFP at this time so I am going to disable those; expand the Windows File Service section and uncheck Enable Windows File Service; repeat for Mac File Service</li>
	<li>Expand NFS service and check enable NFS</li>
	<li>Click the Apply button</li>
	<li>In the left navigation window click on Shared Folder</li>
	<li>Click the create button</li>
	<li>Provide the necessary details for your folder I am naming my folder vxprt-silver01-ds01 which will be on the SATA drives; click OK</li>
	<li>Click on the NFS permissions tab and click the Create button</li>
	<li>In the hostname/IP field enter the range for your ESXi hosts, in my case its all the same network so 192.168.0.0/16</li>
	<li>Click OK twice</li>
	<li>Make note of the mount path value, we'll need that later</li>
	<li>Repeat for the folder on the SSD volume, I am naming htis folder vxprt-gold01-ds01</li>
	<li>You should now have two folders created</li>
</ul>
[caption id="attachment_2962" align="aligncenter" width="1007"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/synology-nfs-shares-dsm.png"><img class="size-full wp-image-2962" src="http://www.virtxpert.com/wp-content/uploads/2014/11/synology-nfs-shares-dsm.png" alt="Synology NFS shares created in DSM" width="1007" height="581" /></a> Synology NFS shares created in DSM[/caption]

Next I need to connect to my NFS share from the ESXi hosts.  Typically I'd have NFS on its on VLAN, but sans a switch in my home lab to VLANs it will be riding with all my other network traffic.
<ul>
	<li>Log into the vCenter Web Client</li>
	<li>Click on vCenter &gt;&gt; Hosts and Clusters</li>
	<li>Select your cluster, click on the Related Objects tab &gt;&gt; Datastores</li>
	<li>Click the icon to add a new datastore, click Next</li>
	<li>Select next NFS and click Next</li>
	<li>Enter the datastore name, in my case vxprt-silver01-ds01</li>
	<li>Enter the server IP address and the path you note in the previous section, in my case /volume1/vxprt-silver01-ds01 - click next</li>
	<li>Select both/all hosts in the cluster you want to have access and click next then finish</li>
</ul>
The datastore should now be available on both hosts (Click on the host &gt;&gt; related objects &gt;&gt; datastores) as seen below.  Repeat for the gold datastore.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/synology-nfs-datastore.png"><img class="aligncenter size-full wp-image-2959" src="http://www.virtxpert.com/wp-content/uploads/2014/11/synology-nfs-datastore.png" alt="synology-nfs-datastore" width="766" height="302" /></a>

Now that the datastores are created, I am going to create an "ISO" folder on the silver datastore to hold my linux ISOs and build virtual machines in vCenter.