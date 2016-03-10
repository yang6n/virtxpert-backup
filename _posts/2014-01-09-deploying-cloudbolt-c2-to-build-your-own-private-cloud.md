---
ID: 1787
post_title: >
  Deploying CloudBolt C2 to build your own
  private cloud
author: Jonathan Frappier
post_date: 2014-01-09 15:47:06
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/deploying-cloudbolt-c2-to-build-your-own-private-cloud/
published: true
dsq_thread_id:
  - "2103430070"
---
With many companies having virtualized, most still haven't figured how to offer self service to various parts of the business, unless it's so critical that you paid for vCloud Director or vCAC, or maybe hired a crack team to manage OpenStack.  CloudBolt aims to remove that barrier for organizations that could benefit from having a private cloud deployment on top of their existing vSphere, Xen Server, KVM or RHEL-V virtualization platforms.  In this post we will look at deploying CloudBolt C2 in a VMware vSphere environment.  You'll need to register for the download at <a href="http://land.cloudboltsw.com/download-cloudbolt-c2-ve?virtxpert">http://cloudboltsw.com</a>, but received my approval and link fairly quickly.  You should also register for an account on their support site.  There isn't much documentation on the intergoogles yet so this will be required, however there documentation, at least through the install is very accurate and well written and laid out.

CloudBolt C2 arrives as an OVA as you might expect.  There are a few pre-setup steps you'll want to configure first.
<ul>
	<li>Setup a DNS entry for the IP you'll assign</li>
	<li>Add a CD-ROM to the VM (mine did not come with a CD drive, you'll need this later to install VMware Tools)
<ul>
	<li>Right click on the VM &gt;&gt; Edit Settings &gt;&gt; Add, select CD/DVD Drive and following the wizard.</li>
</ul>
</li>
	<li>Have a VM template handy to use for deployments</li>
</ul>
Now that you have those items complete, deploy the OVA as you normally would; there are no advanced settings exposed here - select your host, datastore, name your VM etc.
<ul>
	<li>When the OVA finishes, power on your VM.  The VM will boot to a normal console screen.</li>
	<li>Log into the console as root/cloudbolt</li>
	<li>You will need to provide IP information and its FQDN, reset the password and start the configuration script to configure CloudBolt C2.</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/01/cloudbolt-configure.jpg"><img class="aligncenter size-full wp-image-1793" alt="cloudbolt-configure" src="http://www.virtxpert.com/wp-content/uploads/2014/01/cloudbolt-configure.jpg" width="725" height="404" /></a>

&nbsp;
<ul>
	<li>Once entered, it will run through a short setup.</li>
	<li>You'll now need to install VMware tools (see http://kb.vmware.com/kb/1018414), however one problem I ran into was the OVA deployed the VM with no CD drive so you'll need to add one.  Seemingly because I had to add the CD device to the VM it was added as /dev/cdrom1, account for that with the directions from the KB above.</li>
	<li>Once complete navigate to the FQDN you created in the first step and you will be presented with the CloudBolt login screen.  Here you can log in as admin/admin.</li>
	<li>Accept the EULA then select your virtualization platform, in this case VMware vCenter.</li>
	<li>Fill in the details for your "Resource Handler" - in this case your vCenter Server.</li>
	<li>Name your Resource Handler, select the default datastore and select which clusters you wish to import.</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/01/cloudbolt-resource-setup.jpg"><img class="aligncenter size-full wp-image-1795" alt="cloudbolt-resource-setup" src="http://www.virtxpert.com/wp-content/uploads/2014/01/cloudbolt-resource-setup.jpg" width="659" height="541" /></a>
<ul>
	<li>Select your default network, IP scheme information and how to assign IP address</li>
	<li>Create your administrative user for C2 and finally enter your SMTP information.</li>
</ul>
At this point, CloudBolt C2 is configured and you will be logged in as the administrative user and can click through to the main dashboard.  Over the next few weeks I hope to test the usability of C2 out as a self service platform to request and deploy VMs.

The setup and documentation were both excellent, working as expected and laid out in a manner that is very thought out.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/01/cloudbolt-c2-dashboard.jpg"><img class="aligncenter size-large wp-image-1796" alt="cloudbolt-c2-dashboard" src="http://www.virtxpert.com/wp-content/uploads/2014/01/cloudbolt-c2-dashboard-1024x413.jpg" width="640" height="258" /></a>

&nbsp;