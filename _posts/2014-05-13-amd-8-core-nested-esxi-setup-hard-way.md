---
ID: 2214
post_title: >
  AMD 8-Core Nested ESXi Setup (The hard
  way)
author: Jonathan Frappier
post_date: 2014-05-13 08:36:50
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/amd-8-core-nested-esxi-setup-hard-way/
published: true
dsq_thread_id:
  - "2681812854"
---
In my last post, I reviewed the <a title="8-Core, 32GB RAM, 240GB Flash Home Lab Hardware Assembly" href="http://www.virtxpert.com/8-core-32gb-ram-240gb-flash-home-lab-hardware-assembly/">hardware assembl</a>y and ESXi installation for the <a title="8-Core, 32GB RAM, 360GB Flash, 3TB, Dual-NIC Home Lab Part List" href="http://www.virtxpert.com/8-core-32gb-ram-360gb-flash-2tb-dual-nic-home-lab-part-list/">AMD 8-Core</a> home build.  I showed you at the end of that post a screenshot of Ubuntu 14.04 64-Bit installing in my virtual ESXi host.  Here, I will review the steps necessary to setup a virtual or nested ESXi host, however this process is a bit more manual.

With vCenter 5.5 setup, you would have the option via the web client to select ESXi as the guest operating system.  I wanted to see some virtual inception ASAP and didn't want to wait to get vCenter setup so I went right in and created a VM to run my first nested ESXi host.  In my next post, we will review setting up a nested ESXi host via vCenter so you can see what the differences are.

A quick note bef0re we get started.  On my physical ESXi host I have created several datastores, 1 each on each of the physical drives.  I have name the datastores so that match the name of the hosts I will use them on.  For example on one of the drives I created a datastore called v-esx01-local.  On this drive I will create a drive for my nesxted ESXi host to use for its local storage.  Do this for each of the nested ESXi hosts you plan to setup.

Connect directly to the physical ESXi host, in my case 10.11.12.100 and follow these steps:
<ul>
	<li>Create a new virtual machine, select Custom.  Selecting Custom will allow you to set the vCPU and RAM options that would otherwise be pre-set for you.</li>
	<li>Give your VM a name, I opted for v-esx## though this can follow your normal naming convention</li>
	<li>Select a datastore, I am putting all my ESXi VMDKs on p-esx01-local</li>
	<li>Select a Virtual Machine Hardware Version.  In the C# client you can only select up to 8, we will change that later by manually editing the VMX file.</li>
	<li>For the Guest Operating System select Linux, and Other Linux (64-bit)</li>
	<li>In the number of cores per virtual socket select 2.  We only have 8 cores to go around so I will be cheap here, after all this isn't a performance lab.</li>
	<li>In memory change the Memory Size drop down from MB to GB and set the size to 4GB</li>
	<li>No changes on the network or SCSI controller screens so click next</li>
	<li>Select create a new virtual disk</li>
	<li>Change the Disk Size to 1GB and set to Thin Provision</li>
	<li>Click next on the Advanced Options screen as we will not need to make any changes here and click Finish.</li>
</ul>
Now, with the VM create, navigate to the physical host Configuration tab and click Storage.
<ul>
	<li>Click Add Storage...</li>
	<li>Select Disk/LUN</li>
	<li>Select one of the physical disks.  In my case I chose to use one of the 500GB Seagate Hybrid drives</li>
	<li>Select VMFS-5 as the File System</li>
	<li>Review and click next</li>
	<li>Enter the datastore name, in my case v-esx01-local</li>
	<li>Select Maximum space available</li>
	<li>Click Finish</li>
</ul>
Browse the p-esx01-local datastore and navigate to the v-esx01 folder.  This is where we will copy the VMX file locally so we can edit in Notepad/Notepad++
<ul>
	<li>Click on the file named v-esx##.vmx and click on the icon with the green down arrow</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/05/browse-datastore.png"><img class="aligncenter size-full wp-image-2220" src="http://www.virtxpert.com/wp-content/uploads/2014/05/browse-datastore.png" alt="browse-datastore" width="545" height="401" /></a>
<ul>
	<li>Select where you want to save the file</li>
	<li>With the v-esx##.vmx file on your desktop (or whatever folder  you saved it to), right click on it and select Open With.  If, like me, you have Notepad++ installed (who doesn't on Windows?) you can also select Edit with Notepad++</li>
	<li>Make the following changes:
<ul>
	<li>Change the guestOS value to vmkernel5</li>
	<li>Change the ethernet0.virtualDev value to vmxnet3</li>
	<li>Add the following line to the bottom of the file:  vhv.enable = "TRUE"</li>
</ul>
</li>
	<li>Save the file and delete the original one from the v-esx## folder on the datastore</li>
	<li>Upload this new vmx file using the Datastore Browser, this time click the soup can with the green arrow pointing up and select Upload File</li>
	<li>Right click on v-esx02 and select Remove from Inventory and click yes</li>
	<li>Browse the datastore again, right click the vmx and select Add to Inventory accepting all defaults.</li>
</ul>
Now, if you edit your VM settings or click on the Summary tab for the VM you can see that your Guest OS Version is VMware ESXi 5.x.  Mount an ESXi 5.5 ISO to the CD-ROM device, power on the VM and install ESXi.  Once ESXi is installed, I will add a new virtual hard drive to the VM on the 500GB datastore I created on the physical host earlier.  Another option, which I will review later, is setting up FreeNAS or some other server to present iSCSI or NFS on all of the drives so you are able to mimic shared storage.

As you can see below, I have ESXi running at 10.11.12.101 and the Ubuntu VM running in it.  In my next post, I will review some "back to basics"

<a href="http://www.virtxpert.com/wp-content/uploads/2014/05/inception-achieved.png"><img class="aligncenter  wp-image-2208" src="http://www.virtxpert.com/wp-content/uploads/2014/05/inception-achieved.png" alt="inception-achieved" width="593" height="528" /></a>

You can find more information thanks to <a href="http://www.virtuallyghetto.com/2012/08/how-to-enable-nested-esxi-other.html" target="_blank">William Lam's post here</a>, including nesting Hyper-V