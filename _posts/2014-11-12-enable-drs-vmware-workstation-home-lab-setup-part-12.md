---
ID: 2887
post_title: 'Enable DRS &#8211; VMware Workstation Home Lab Setup Part 12'
author: Jonathan Frappier
post_date: 2014-11-12 08:00:52
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/enable-drs-vmware-workstation-home-lab-setup-part-12/
published: true
dsq_thread_id:
  - "3217240371"
---
[display-posts category="Lab Series" display-posts posts_per_page="15"]

vCenter is built, now we can start doing some of the cooler things VMware vSphere has to offer; up first - Dynamic Resource Scheduler.  DRS can be run in either manual, partially automated or fully automated mode.  Partially automated will make initial placements of new virtual machines and virtual machines during power on operations and suggest how to rebalance the cluster.  Fully automated, well its fully automated.  It will balance cluster resources based on how aggressive you want it to be.  For a deeper dive into DRS, <a href="http://www.amazon.com/VMware-vSphere-5-1-Clustering-Deepdive-ebook/dp/B0092PX72C/ref=tmm_kin_swatch_0?_encoding=UTF8&amp;sr=&amp;qid=" target="_blank">check out the Clustering Deep Dive book</a>, basically the bible for all things HA and DRS.

To enable DRS, log into the vSphere web client and perform the following steps:
<ul>
	<li>Click on vCenter &gt;&gt; Hosts and Clusters</li>
	<li>Right click the cluster you created, in my case CL01 and select Settings</li>
	<li>Click on vSphere DRS and click the Edit button</li>
	<li>Click the Turn ON vSphere DRS checkbox</li>
</ul>
[caption id="attachment_2914" align="aligncenter" width="974"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/vsphere-cluster-drs-on.png"><img class="size-full wp-image-2914" src="http://www.virtxpert.com/wp-content/uploads/2014/11/vsphere-cluster-drs-on.png" alt="vSphere - Enable DRS" width="974" height="572" /></a> vSphere - Enable DRS[/caption]
<ul>
	<li>Give I have only two hosts, I have left DRS Automation to "Partially Automated" - in a real use case, there is little reason not to set it to "Fully Automated" - of course you need to understand your environment and its impact before making that decision</li>
	<li>If you Click on DRS Automation you can see advanced features and further explanation on the various settings.</li>
	<li>When finished, click OK.  The cluster will be reconfigured.</li>
</ul>
So enabling DRS - not to hard; understanding all of the settings and how it impacts your environment - well that is typically the harder part.  As for our home lab setup, we are ready to setup vMotion - a requirement for DRS to be fully automated!