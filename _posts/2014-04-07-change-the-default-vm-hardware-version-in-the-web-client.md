---
ID: 2139
post_title: >
  Change the default VM Hardware Version
  in the web client
author: Jonathan Frappier
post_date: 2014-04-07 15:56:17
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/change-the-default-vm-hardware-version-in-the-web-client/
published: true
dsq_thread_id:
  - "2594155558"
---
If you are concerned over the VM Hardware Version for your vSphere 5.5 environment, you can change the setting that configures each new virtual machine with VM hardware version 10 as a default, this setting is controlled at the data center level.  For those wondering why; virtual machines using VM hardware version 10 can only be edited via the web client or command line, you cannot change the settings for those VMs via the C# client.  Now I'm not suggesting that you use the C# client, in fact I've become quite a big fan of the web client in 5.5 but you need to consider your recovery strategies should you not have access to  vCenter or the web client with certain VMs so for many, running in VM hardware version 9 may be preferable.
<ol>
	<li>To change the default VM hardware version do the following:</li>
	<li>Log into the vSphere web client</li>
	<li>Click on Hosts and Clusters.</li>
	<li>Right click the data center and select Edit Default VM Compatibility...</li>
	<li>Use the Compatible with: pull down and change the setting to  ESXi 5.1 and later which will use VM hardware version 9.</li>
</ol>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/04/vmcompat.png"><img class="aligncenter size-full wp-image-2140" alt="vmcompat" src="http://www.virtxpert.com/wp-content/uploads/2014/04/vmcompat.png" width="452" height="248" /></a>

Now, any new VMs created will use VM hardware version 9 by default.  Note, however, that features and configuration maximums that require hardware version 10 will not be available to those VMs, such as vSphere Flash Read Cache (vFRC).