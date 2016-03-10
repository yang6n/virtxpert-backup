---
ID: 4124
post_title: >
  Configure vCenter Server Appliance 6
  VCSA6 after VMware Workstation
  Deployment
author: Jonathan Frappier
post_date: 2015-11-17 11:46:09
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/configure-vcenter-server-appliance-6-vcsa6-after-vmware-workstation-deployment/
published: true
dsq_thread_id:
  - "4327176974"
---
<em>**Update: If, like me, you only have the 6.0.0 version of the VCSA available to download, <a href="http://www.settlersoman.com/how-to-update-or-patch-vcenter-6-appliance-vcsa/" target="_blank">check out this post for how to install Update 1</a> to get the VAMI back. Thank you Christian for the reminder on the VAMI being brought back**</em>

As some folks may recall from <a href="http://www.virtxpert.com/workstation-home-lab-wrap-up-on-to-vrealize-automation/">last years #vDM30in30</a>, I run my home lab on a single <a href="http://www.virtxpert.com/home-lab-1250-8-core-32gb-750gb-flash-2tb-hdd-2015-edition/">8-core AMD box</a> with all of the hosts nested. I do, however, prefer to run certain virtual machines such as my Domain Controller and vCenter Server in Workstation as well, so I can have those powered on without having to worry about host issues (after all this is a lab and I h0rked up my ESXi 5.5 hosts pretty good doing some testing).

Since the new vCenter Server Appliance (VCSA6) has a new deployment method, installing it in Workstation is not obvious, however <a href="http://www.virten.net/2015/04/how-to-install-vcenter-server-appliance-vcsa6-in-vmware-workstation/" target="_blank">Florian Grehl has a great write up on how to do just that</a> - Thanks <a href="https://twitter.com/virten" target="_blank">Florian</a>. Once you have it deployed, there are a few things to take care of that the installer would have otherwise handled.
<ul>
	<li>Log into your DNS server/Domain Controller and create an A record for the VCSA6. <a href="http://www.virtxpert.com/installing-vmware-vcenter-server-appliance-6-0-vcsa/">This has to be done in advance of a typical deployment as well</a>.</li>
	<li>Deploy the VCSA using the <a href="http://www.virten.net/2015/04/how-to-install-vcenter-server-appliance-vcsa6-in-vmware-workstation/" target="_blank">directions from virten.net</a></li>
	<li>Log into the vSphere Web Client for the VCSA you just deployed</li>
	<li>Click on System Configuration &gt;&gt; Nodes &gt;&gt; &lt;Your VCSA6 Node&gt; &gt;&gt; Networking</li>
	<li>Edit the hostname and DNS server to match your environment</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/vcsa6-change-hostname-dns.png"><img class="aligncenter size-full wp-image-4129" src="http://www.virtxpert.com/wp-content/uploads/2015/11/vcsa6-change-hostname-dns.png" alt="vcsa6-change-hostname-dns" width="959" height="558" /></a>
<ul>
	<li>Next, navigate to Active Directory and click the Join button. Enter the details for your domain</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/vcsa6-join-ad-domain.png"><img class="aligncenter size-full wp-image-4130" src="http://www.virtxpert.com/wp-content/uploads/2015/11/vcsa6-join-ad-domain.png" alt="vcsa6-join-ad-domain" width="412" height="263" /></a>

For me, using the current latest version of the VCSA6, I did not receive an acknowledgement that the join was successful, however if you check AD you should see the computer object created in the OU/CN specified.
<ul>
	<li>Reboot the VCSA6 (Right click on the node in the vSphere Web Client and select Reboot). Since this is deployed in Workstation, we can monitor the progress of the restart there.</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/vcsa-workstation-restart.png"><img class="aligncenter size-full wp-image-4131" src="http://www.virtxpert.com/wp-content/uploads/2015/11/vcsa-workstation-restart.png" alt="vcsa-workstation-restart" width="1280" height="985" /></a>

Once the VCSA6 completes the restart, you should now be able to access the vSphere Web Client by its FQDN. If you navigate back to the node, you can now see that it is joined to the domain

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/vcsa-domain-joined.png"><img class="aligncenter size-full wp-image-4133" src="http://www.virtxpert.com/wp-content/uploads/2015/11/vcsa-domain-joined.png" alt="vcsa-domain-joined" width="1198" height="368" /></a>

&nbsp;

At this point, I would normally set the NTP server as well, however I don't see an option to do so through the vSphere Web Client. There is where updating to Update 1 comes in handy, as the NTP server can be set through the new HTML5 VAMI (https://&lt;vc-fqdn&gt;:5480). <a href="http://www.settlersoman.com/how-to-update-or-patch-vcenter-6-appliance-vcsa/" target="_blank">See this post if you had to download the 6.0.0 version of the VCSA to install Update 1</a>.

Next, you will need to configure SSO. Navigate to Administration &gt;&gt; Single Sign On &gt;&gt; Configuration. Here you can update the policies, and add AD as an identity source. Time to get my lab reconfigured!