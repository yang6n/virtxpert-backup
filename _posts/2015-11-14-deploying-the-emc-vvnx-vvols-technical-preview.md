---
ID: 4100
post_title: >
  Deploying the EMC vVNX VVOLs Technical
  Preview
author: Jonathan Frappier
post_date: 2015-11-14 18:24:24
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/deploying-the-emc-vvnx-vvols-technical-preview/
published: true
dsq_thread_id:
  - "4319443785"
---
<em>**Disclaimer: I am an EMC employee. This post was not requested or required by my employer, it is simply my experience getting to know the product**</em>

Back in May at EMC World, support for VMware Virtual Volumes, or VVOLs, was announced and would be supported on the Virtual VNX (vVNX) that was also relased that May (however without VVOL support). Fast forward to August and a <a href="https://www.emc.com/products-solutions/trial-software-download/vvols.htm" target="_blank">Technical Preview of VVOLs was released which anyone can download</a>. I think blog post I will be deploying the vVNX and making sure it is setup and ready to attach to a vSphere 6 cluster (future post).

Make sure you have a host that can take a VM running 12GB of RAM, I tried dropping it down to 4 and it was unnnnnhappy. I am going to try again after this post to redeploy and start it with 8GB to see if that works. After downloading the appliance, log into the vSphere web client and start the Deploy OVF Template wizard and select the local file you downloaded.
<ul>
	<li>Accept the extra configuration options and EULA</li>
	<li>Provide a name and select a folder</li>
	<li>Select whether to thin, or thick provision the appliance (you will need a bit over 2GB for thin, and 84GB for thick)</li>
	<li>Select the networks for the vVNX management and data interfaces</li>
	<li>Provide the system name and IP information for the interfaces</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/mgmt-vvnx-ip-ovf.png"><img class="aligncenter size-full wp-image-4104" src="http://www.virtxpert.com/wp-content/uploads/2015/11/mgmt-vvnx-ip-ovf.png" alt="mgmt-vvnx-ip-ovf" width="960" height="556" /></a>

Click Finish to start the deployment - do not set the virtual machine to power on after deployment. When the deployment finishes, add additional drives to the the vVNX to use for storage and then power on the virtual machine when finished.

Open a web browser and navigate to the management IP address you provided via https, so in my example it would be https://192.168.6.50 and log in with the default username and password of admin / Password123# which will launch the initial configuration wizard

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/vvnx-initial-configuration.png"><img class="aligncenter size-full wp-image-4109" src="http://www.virtxpert.com/wp-content/uploads/2015/11/vvnx-initial-configuration.png" alt="vvnx-initial-configuration" width="999" height="549" /></a>

The following are the high level steps for the vVNX initial configuration:
<ul>
	<li>Accept the EULA</li>
	<li>Change the admin password from Password123#</li>
	<li>[Optional] Set a different service password (default is to make it the same)</li>
	<li><a href="https://www.emc.com/auth/elmeval.htm" target="_blank">Register and save your vVNX license file</a> by providing the System UUID</li>
	<li>Set the DNS &amp; NTP servers for your network - note if there is a major time difference you will need to set NTP later</li>
	<li>Create storage pools and add drives - for example I added three drives to my vVNX from my Synology, so I have created a pool called vxprt-capacity</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/vvnx-drives.png"><img class="aligncenter size-full wp-image-4114" src="http://www.virtxpert.com/wp-content/uploads/2015/11/vvnx-drives.png" alt="vvnx-drives" width="1000" height="597" /></a>
<ul>
	<li>Assign tiers to the drives, I opted for capacity.</li>
	<li>During the pool creation wizard, when prompted check the box for Create VMware Capability Profile and assign tags</li>
	<li>Add iSCSi interfaces</li>
	<li>Optionally, create a NAS (I skipped this step for now)</li>
</ul>
Once the initial configuration is complete, you will be returned to the new HTML5 Unisphere client (which is pretty nice by the way!). Next up for me is getting ESXi 6 and the vSphere 6 VCSA setup in my lab.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/vvnx-dashboard.png"><img class="aligncenter size-full wp-image-4116" src="http://www.virtxpert.com/wp-content/uploads/2015/11/vvnx-dashboard.png" alt="vvnx-dashboard" width="1276" height="725" /></a>

&nbsp;