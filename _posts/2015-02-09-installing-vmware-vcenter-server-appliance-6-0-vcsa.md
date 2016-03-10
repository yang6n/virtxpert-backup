---
ID: 3502
post_title: >
  Installing the VMware vCenter Server
  Appliance 6.0 VCSA
author: Jonathan Frappier
post_date: 2015-02-09 08:00:04
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/installing-vmware-vcenter-server-appliance-6-0-vcsa/
published: true
dsq_thread_id:
  - "3492756242"
---
<em>**Updated based on GA 6.0 code**</em>

Generally, installing virtual appliances has been pretty straight forward - import an OVA and enter the necessary details in the deployment wizard, or access the virtual appliances management interface (such as those typically on port 5480 from VMware). However, as of the Release Candidate for VMware vSphere 6.0, the vCenter Server Appliance (VCSA) installation takes a much different approach than what you've been used to.
<h3>A few vCenter Server Appliance prerequisites</h3>
First, it should be noted that you can only install the vCenter Server Appliance (VCSA) from Windows. I was first turned onto the VCSA because I was at an all OSX/Linux shop so it made sense to use something we were accustomed to using already. For now, you'll need a Windows box to at least get the appliance deployed;  then you can punt (please note also this is based on Release Candidate (RC) code and could change in the final release).

You CAN deploy the VCSA 6.0 to both ESXi 5.5 or 6.0 host. If you currently have a 5.5 environment you can deploy the VCSA without upgrading your hosts, but if you did not take  the plunge into 5.5 you'll have to bring at least one host online running 5.5. or 6.0.

Finally, before getting started, <em><strong>you MUST create DNS records before running the installer</strong></em>. I was struggling with the new installer because I've just been used to doing my DNS records after I deployed the VCSA, but before running the setup through the management interface. However with a little help from <a href="http://emadyounis.com/" target="_blank">Emad Younis</a> (<a href="http://twitter.com/emad_younis" target="_blank">@Emad_Younis</a>) I was able to point me in the right direction. With 6.0 all of the configuration is done from the initial setup wizard. When it's finished installing, vCenter is ready to run.

<em><strong>The installation wizard will NOT give you an error if this does not exist, instead it will fail during the installation!</strong></em>

As you can see here I have my forward and reverse DNS records ready to go on .9

<a href="http://www.virtxpert.com/wp-content/uploads/2015/02/vwmare-vcsa-dns.png"><img class="aligncenter  wp-image-3508" src="http://www.virtxpert.com/wp-content/uploads/2015/02/vwmare-vcsa-dns.png" alt="vwmare-vcsa-dns" width="519" height="485" /></a>
<h3>Installing the vCenter Server Appliance</h3>
As with the older versions of the VCSA, it all starts with a download; however in this case you will be downloading an ISO image. Once the ISO image is downloaded either mount the ISO on your Windows box or extract the ISOs into a folder (as seen here).

<a href="http://www.virtxpert.com/wp-content/uploads/2015/02/vmware-vcsa-iso-extracted.png"><img class="aligncenter  wp-image-3505" src="http://www.virtxpert.com/wp-content/uploads/2015/02/vmware-vcsa-iso-extracted.png" alt="vmware-vcsa-iso-extracted" width="624" height="346" /></a>

Now that you have access to the files, drill down into the vcsa folder, there you will find the VMware-ClientIntegrationPlugin-6.0.0. Install this application on your Windows box (double click, Next, Accept/Next, Next, Install, Finish). Once the plugin finishes installing, back up one folder level and open the index file. As you can see here I am on Windows Server 2012, thus at least IE10 however opening the index in IE10 gives me a warning that I need to upgrade to at least IE10 or 11, so yea I'm going with Chrome. As with any plugin, you must enable it in Chrome. Click on the puzzle piece with the red x, then click Always allow and refresh the page and click the Allow button.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/02/vmware-vcsa-chrome-enable-plugin.png"><img class="aligncenter size-full wp-image-3507" src="http://www.virtxpert.com/wp-content/uploads/2015/02/vmware-vcsa-chrome-enable-plugin.png" alt="vmware-vcsa-chrome-enable-plugin" width="596" height="272" /></a>

Newer versions of Chrome/Client Integration Plugin may prompt you like this; click Remember my choice and then the launch Application button

[caption id="attachment_3648" align="aligncenter" width="453"]<a href="http://www.virtxpert.com/wp-content/uploads/2015/02/chrome-vcsa.png"><img class="size-full wp-image-3648" src="http://www.virtxpert.com/wp-content/uploads/2015/02/chrome-vcsa.png" alt="Chrome VCSA VMware Client Integration Plugin launch application" width="453" height="349" /></a> Chrome VCSA VMware Client Integration Plugin launch application[/caption]

You should now see the vCenter icon along with a large Install and Upgrade button, click on the Install button. You will get a UI very similar to what you would get deploying a virtual appliance.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/02/vmware-vcsa-6-installer.png"><img class="aligncenter size-full wp-image-3509" src="http://www.virtxpert.com/wp-content/uploads/2015/02/vmware-vcsa-6-installer.png" alt="vmware-vcsa-6 -installer" width="871" height="555" /></a><!--more-->

1.  After carefully reading the license agreement, printing it for your records, and having it signed by an attorney, click the <strong>I accept...</strong> check box and click Next.

2.  Now you can chose to deploy to your target server. Specify your ESXi host (5.5 or above!), username and password. Note the requirements at the bottom of the page; if you are using a vDS the port group must be ephemeral.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/02/vcsa-ephemeral.png"><img class="aligncenter size-full wp-image-3649" src="http://www.virtxpert.com/wp-content/uploads/2015/02/vcsa-ephemeral.png" alt="vcsa-ephemeral" width="625" height="112" /></a>Now click Next.

<strong><em>If you are using self signed/untrusted certificates click Yes when prompted.</em></strong>

3.  The next step is to name your appliance. In my case, like I have created in DNS, my appliance name will be vxprt-vc02.vxprt.local. Provide the OS root user password and click Next

4.  On the deployment type you can chose to install an embedded Platform Services Controller (which includes Single Sign-On in vSphere 6.0), just the the PSC, or just vCenter. You can have multiple Platform Services Controllers, and they can be different types. For example you could do a stand-alone PSC and have an embedded one with the VCSA. When the installer says "embedded" it really just means the components will be installed on the same virtual appliance as vCenter. I'll be doing embedded here. Click Next

5.  Chose whether you have an existing SSO domain or you will be creating a new one. I will do this install as a new SSO domain type deployment. Enter the administrator password, and domain. To stay consistent with what I know about SSO, I'll enter vsphere.local and Default-First-Site for the site name. Click Next.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/02/vcsa-6-new-sso.png"><img class="aligncenter size-full wp-image-3651" src="http://www.virtxpert.com/wp-content/uploads/2015/02/vcsa-6-new-sso.png" alt="vcsa-6-new-sso" width="882" height="567" /></a>

6.  Select the appliance size that supports your environment, including the new "tiny" deployment for up to 10 hosts. Click Next

7.  Select the datastore you will to install to, and whether to <strong>THIN PROVISION</strong> the vmdk (no VMware, I'm not calling it "Thin Disk Mode" - THIN PROVISION!). Click Next

8.  If you're an Oracle shop, you have a choice on step 8, otherwise just click Next.

9.  Chose a network (this will be based on the host you deployed to), and how to assign IP information including the host name - <strong>This MUST match DNS. </strong>I'll select static as that is what I would want to do for this type of server. Finally enter the NTP server and click next (I've also enabled SSH so I can connect directly to the virtual machine.

[caption id="attachment_3513" align="aligncenter" width="709"]<a href="http://www.virtxpert.com/wp-content/uploads/2015/02/vmware-vcsa-6-step-9-network.png"><img class=" wp-image-3513" src="http://www.virtxpert.com/wp-content/uploads/2015/02/vmware-vcsa-6-step-9-network.png" alt="VMware vCenter Server Appliance (VCSA) installation - Network Settings" width="709" height="455" /></a> VMware vCenter Server Appliance (VCSA) installation - Network Settings[/caption]

10.  Review the settings you've enter, make sure your IP information and host name are all correct and click Finish. The installation of vCenter and the VCSA will start. You'll even see it installing packages, that's right this is a ground up build, not just a bunch of packages pre-installed on a virtual machine!

[caption id="attachment_3514" align="aligncenter" width="879"]<a href="http://www.virtxpert.com/wp-content/uploads/2015/02/vmware-vcsa-6-installation-progress.png"><img class="size-full wp-image-3514" src="http://www.virtxpert.com/wp-content/uploads/2015/02/vmware-vcsa-6-installation-progress.png" alt="VMware vCenter Server Appliance (VCSA) installation process" width="879" height="564" /></a> VMware vCenter Server Appliance (VCSA) installation process[/caption]

Once the installation is complete, you can connect to https://fqdn/vsphere-client (no more 9443! One less question on the VCP6 I guess :) ).

<a href="http://www.virtxpert.com/wp-content/uploads/2015/02/vcsa-6-complete.png"><img class="aligncenter size-full wp-image-3656" src="http://www.virtxpert.com/wp-content/uploads/2015/02/vcsa-6-complete.png" alt="vcsa-6-complete" width="706" height="239" /></a>Log in as the user@domain you configured during the installation.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/02/vcsa-6-web-client.png"><img class="aligncenter size-full wp-image-3657" src="http://www.virtxpert.com/wp-content/uploads/2015/02/vcsa-6-web-client.png" alt="vcsa-6-web-client" width="984" height="619" /></a>

That's it, your vCenter Server Appliance is now installed, of course, now comes the fun part like creating your clusters, setting up HA, Admission Control, DRS, and other great features enabled by vCenter!