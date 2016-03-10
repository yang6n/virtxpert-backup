---
ID: 3055
post_title: 'Add vCenter Endpoint &#8211; vRealize Automation Series Part 8'
author: Jonathan Frappier
post_date: 2014-11-19 08:30:53
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/add-vcenter-endpoint-vrealize-automation-series-part-8/
published: true
dsq_thread_id:
  - "3241448716"
---
[display-posts category="vRA Home Lab" display-posts posts_per_page="15"]

With administrative users setup so we can actually configure various options in vRealize Automation / vCloud Automation Center - its now time to add some compute resource, so we can actually deploy things!  Endpoints in vRealize Automation / vCloud Automation Center can be several things:
<ul>
	<li>Hypervisor management platforms such as vCenter, vCenter Orchestrator, and SCVMM</li>
	<li>Cloud providers such as vCloud Air (formerly vCloud Hybrid Service), vCloud Director providers including vCloud Air, OpenStack using RHEV 3.1</li>
	<li>Physical hardware from Cisco, HP, and Dell</li>
</ul>
If you recall from the IaaS installation post, one of the options asked us to name the vCenter endpoint, now we are going to log in and configure our vCenter server as an endpoint so we can use it to deploy virtual machines through the catalog.
<ul>
	<li>Log into your vRealize Automation / vCloud Automation Center appliance (in my case https://vxprt-vcac01.vxprt.local/vcac) as.... do you recall from the last post who to log in as?  That's right iaasadmin as that user was assigned the infrastructure administrator role which can manage endpoints</li>
	<li>Once logged in, click on the infrastructure tab &gt;&gt; Monitoring &gt;&gt; Log</li>
	<li>Notice here the errors related to the <em>VRM agent</em> occurring every minute, that is because we have not added our vCenter server yet</li>
	<li>Click Back to infrastructure, then click on Endpoints &gt;&gt; Endpoints</li>
	<li>Hover over New Endpoint &gt;&gt; Virtual and click on vSphere (vCenter)</li>
</ul>
[caption id="attachment_3061" align="aligncenter" width="460"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/vra-add-endpoint.png"><img class="size-full wp-image-3061" src="http://www.virtxpert.com/wp-content/uploads/2014/11/vra-add-endpoint.png" alt="vRealize Automation / vCloud Automation Center add vSphere (vCenter) Endpoint" width="460" height="170" /></a> vRealize Automation / vCloud Automation Center add vSphere (vCenter) Endpoint[/caption]
<ul>
	<li>We will need to name the endpoint, the URL to the vCenter SDK and credentials.  Since we have not already, I would create a user account in AD called svc_vra_vcbind and add it to the vcAdmins group (assuming you followed along on the home lab build, or give it admin permission directly to your vCenter)</li>
	<li>Fill in the following information:
<ul>
	<li>Name:  vCenter (Do you recall why we are naming it vCenter?)</li>
	<li>Address:  vcenterurl/sdk (in my case https://vxprt-vc01.vxprt.local/sdk)</li>
	<li>Credentials:  Click the ellipse, then New Credentials and add a user account with permission to vCenter and click the green circle with the checkmark</li>
</ul>
</li>
	<li>With all the information filled in, click the OK button</li>
	<li>Once vCenter has been added, return to the log view, you should notice that the VRM Agent errors are no longer occurring</li>
</ul>
Now you've added resources vRealize Automation / vCloud Automation Center can use to fulfill requests, however we still need to assign those compute resources to a fabric group, which will be next in my vRealize series!