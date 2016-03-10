---
ID: 1961
post_title: >
  Enabling EVC when vCenter is a virtual
  machine
author: Jonathan Frappier
post_date: 2014-02-12 08:51:57
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/enabling-evc-vcenter-virtual-machine/
published: true
dsq_thread_id:
  - "2256380761"
---
Well this was a chicken and egg kind of brain tease.  I was building a new cluster with hosts that had different CPUs, so I needed to enable EVC on my cluster.  Problem was since vCenter was running, and needed for cluster management so I couldn't exactly shut it down.  Here were the steps I used to bring vCenter up in an EVC enabled cluster.

What you'll need:  two hosts, vCenter running as a VM, some sort of shared storage accessible to both host, a Windows computer to run the C# client (another use case where the web client doesn't work)
<ul>
	<li>Create your cluster and enable EVC as needed</li>
	<li>Add the host(s) without the vCenter VM to the EVC cluster</li>
	<li>Storage vMotion the vCenter to the shared storage accessible by both the host in EVC cluster and the one running the vCenter VM</li>
	<li>Power off the vCenter VM</li>
	<li>Connect using the C# to each of the hosts</li>
	<li>Remove the vCenter VM from the original hosts inventory</li>
	<li>Browse to the shared data store on the host already in the EVC enabled cluster, add the vCenter VM to inventory and power on</li>
	<li>Switch to the VM summary tab to answer the Virtual Machine Message and select "I moved it", the VM will boot.  (Thank you to <a href="https://twitter.com/Hazenet" target="_blank">Mads Fog Albrechtslund</a> at<a href="http://hazenet.dk/about/" target="_blank"> http://hazenet.dk/about</a>/for pointing out it should have been 'moved', not copied)</li>
</ul>
The VCSA took a little while to initialize the web client but it finally came up and I was able to place the host in maintenance mode and add it to the EVC enabled cluster.  I hope if you ran into this you did so before the 20 something steps in <a href="http://kb.vmware.com/kb/1013111" target="_blank">http://kb.vmware.com/kb/1013111</a>.  Also, this might have been avoided if I created the VM on the host with the lesser CPU so that the VM was not expecting CPU features that were hidden by EVC.

<em>Featured image via The Blaze</em>