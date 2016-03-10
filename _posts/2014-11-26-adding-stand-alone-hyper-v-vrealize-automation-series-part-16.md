---
ID: 3301
post_title: >
  Adding Stand Alone Hyper-V – vRealize
  Automation Series Part 16
author: Jonathan Frappier
post_date: 2014-11-26 21:34:02
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/adding-stand-alone-hyper-v-vrealize-automation-series-part-16/
published: true
dsq_thread_id:
  - "3266546937"
---
[display-posts category="vRA Home Lab" display-posts posts_per_page="16"]

A question came up on Twitter recently about how to add a stand-alone Hyper-V server as an endpoint.  What I can gather from the documentation is that you need to have an agent deployed for Hyper-V but the directions were otherwise unclear so this is an attempt to document the required steps.  First, the assumption is you have a Windows Server with the Hyper-V role at a minimum available (if you are running as a virtual machine; <a href="http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&amp;cmd=displayKC&amp;externalId=2044876" target="_blank">make sure the OS type is set to Hyper-V</a>).

First, we need to install an agent for Hyper-V.  For my lab I am doing this on my existing IaaS server
<ul>
	<li>Log into the IaaS server as your vCAC / vRA service account</li>
	<li>Download and run the IaaS installer from http://vcacappurl:5480/i as administrator</li>
	<li>When you get to the Installation Type page; select Proxy Agents</li>
</ul>
[caption id="attachment_3304" align="aligncenter" width="806"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/vra-add-hyperv-agent.png"><img class="size-full wp-image-3304" src="http://www.virtxpert.com/wp-content/uploads/2014/11/vra-add-hyperv-agent.png" alt="vRealize Automation / vCloud Automation Center add agent for Hyper-V" width="806" height="607" /></a> vRealize Automation / vCloud Automation Center add agent for Hyper-V[/caption]
<ul>
	<li>Follow the wizard until you get to the Install Proxy Agent screen; enter the following information
<ul>
	<li>Agent type:  HyperV</li>
	<li>Agent Name:  HyperV</li>
	<li>Manager / Model Manager Host Name:  Your IaaS server if you followed along in my vRA Home Lab series</li>
	<li>An administrative user for your HyperV server; then click the Add, and Next button</li>
</ul>
</li>
</ul>
[caption id="attachment_3305" align="aligncenter" width="807"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/vra-agent-configuration.png"><img class="size-full wp-image-3305" src="http://www.virtxpert.com/wp-content/uploads/2014/11/vra-agent-configuration.png" alt="vRealize Automation / vCloud Automation Center Hyper0V agent configuration" width="807" height="608" /></a> vRealize Automation / vCloud Automation Center Hyper0V agent configuration[/caption]
<ul>
	<li>Click the install button and wait for the installation to finish</li>
</ul>
Once the installation finishes, we now need to add the agent to vRA.  To do this, log into vRA as the iaasadmin user and perform the following:
<ul>
	<li>Navigate to Infrastructure &gt;&gt; Endpoints &gt;&gt; Agents</li>
	<li>Provide the FQDN for the Compute resource - your HyperV server, select the HyperV agent from the the pull down and click OK</li>
	<li>Navigate to  Infrastructure &gt;&gt; Compute Resources &gt;&gt; Compute Resources; you should see your Hyper-V server listed as "OK"</li>
</ul>
[caption id="attachment_3307" align="aligncenter" width="1241"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/vra-hyperv-compute-resource.png"><img class="size-full wp-image-3307" src="http://www.virtxpert.com/wp-content/uploads/2014/11/vra-hyperv-compute-resource.png" alt="vRealize Automation / vCloud Automation Center Hyper-V compute resource" width="1241" height="516" /></a> vRealize Automation / vCloud Automation Center Hyper-V compute resource[/caption]

If you click on the small magnifying glass icon, you should see information about your server - I can confirm these are the specs for my Hyper-V virtual machine:

[caption id="attachment_3308" align="aligncenter" width="456"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/hyper-v-resrouces.png"><img class="size-full wp-image-3308" src="http://www.virtxpert.com/wp-content/uploads/2014/11/hyper-v-resrouces.png" alt="vRealize Automation / vCloud Autoamtion Center Hyper-V resources" width="456" height="318" /></a> vRealize Automation / vCloud Autoamtion Center Hyper-V resources[/caption]
<ul>
	<li>Hover over your Hyper-V server and select New Reservation</li>
	<li>Fill in the reservation information and click the OK button; you should now see your Hyper-V server listed</li>
</ul>
This is just adding Hyper-V as a compute resource, I assume will still need virtual machines in Hyper-V (or templates?) to create blueprints from and entitlements for that blueprint - I'll try to get on that ASAP.

&nbsp;