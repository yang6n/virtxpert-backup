---
ID: 3197
post_title: Setting up the CloudBolt Appliance
author: Jonathan Frappier
post_date: 2014-11-29 08:00:06
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/setting-up-the-cloudbolt-appliance/
published: true
dsq_thread_id:
  - "3273644816"
---
It's been almost a year since I last looked at CloudBolt Software, and unfortunately other projects took me away from taking a deeper look at them at that time.  After taking a day off from blogging and having wrapped up my vRealize Automation and Application Services series I thought I'd have another look, especially now having hands on with vRealize Automation to compare it to.

Before you get started, be sure to get your license key squared away as you will need that to proceed.   You can get a license key by calling <a title="Call support" href="tel:+17036651060">(703) 665 1060</a> or by emailing <a title="Email support" href="mailto:support@cloudboltsoftware.com">support@cloudboltsoftware.com</a>

CloudBolt, as you'd expect comes as an OVF to deploy in vCenter or VMware Workstation, there are no OVF properties that are exposed in vCenter so the deployment process would be the same in either scenario.
<ul>
	<li>Deploy the OVF, this is a simple process since you are not setting anything during the setup</li>
	<li>While the VM is deploying, create your DNS records in AD</li>
	<li>Log in as root/cloudbolt; the CloudBOlt C2 Server Setup UI will open</li>
	<li>Set each of the options according to your network, then chose the Run option to configure CloudBolt.  Here is what mine looks like before selecting run</li>
</ul>
[caption id="attachment_3200" align="aligncenter" width="733"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/cloudbolt-initial-setup.png"><img class="size-full wp-image-3200" src="http://www.virtxpert.com/wp-content/uploads/2014/11/cloudbolt-initial-setup.png" alt="CloudBolt setup screen" width="733" height="418" /></a> CloudBolt setup screen[/caption]
<ul>
	<li>If you deploy the VMware Workstation, ensure your VM nic is set according to your desired configuration - NAT or Bridged</li>
	<li>Now, navigate to the IP address / FQDN of the server</li>
	<li>You will need a CloudBolt license key to continue; click on the Browse button to select your license file then click Upload License</li>
	<li>You will now be at the login screen, log in as admin / admin</li>
	<li>Accept the EULA and click Next</li>
	<li>Select your "resource handler" - in my case VMware vCenter (you can select others later if needed)</li>
</ul>
[caption id="attachment_3297" align="aligncenter" width="733"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/12/cloudbolt-resource-handler.png"><img class="size-full wp-image-3297" src="http://www.virtxpert.com/wp-content/uploads/2014/12/cloudbolt-resource-handler.png" alt="CloudBolt Resource Handler Selection" width="733" height="566" /></a> CloudBolt Resource Handler Selection[/caption]
<ul>
	<li>Provide the IP address of your vCenter server along with a username and password, typically I'd create an administrative user specific for CloudBolt such as svc_vc_cb_bind so it could be identified.</li>
	<li>CloudBolt will identify your environment; give a name to your  vCenter server, select your default datastore and which cluster to import</li>
	<li>Select which networks you want to be available for provisioning.  This would be somewhat similar to selecting the port groups in the vCAC reservation - in my case I'll select my vm port group (you can select more than one here)</li>
	<li>Select which templates you want to import</li>
	<li>Create a Cloud Bolt admin user, this is a local user account not tied to AD or LDAP services (all fields are required)</li>
	<li>Finally fill in SMTP information or just click Finish then click Start Using CloudBolt</li>
</ul>
The initial CloudBolt setup is done after that easy wizard, a few additional steps you will need to perform before turning this over to users that we will look at in future posts:
<ul>
	<li>Create new users or configure LDAP for your users to log in (Admin &gt;&gt; Users or Admin &gt;&gt; LDAP Authentication Settings &gt;&gt; New LDAP Utility)</li>
	<li>Create new groups (Groups &gt;&gt; Add a Group)</li>
	<li>Add portal (Admin &gt;&gt; CloudBolt Portals)</li>
	<li>Add a provisioning engine or confiugration manager  (currently supports Puppet, Chef, Docker, Cobbler and HP Automation)</li>
	<li>Create a Service Catalog for users to access</li>
</ul>