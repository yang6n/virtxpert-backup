---
ID: 621
post_title: VMware vCenter SSO 5.1 Installation
author: Jonathan Frappier
post_date: 2013-03-26 19:05:13
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vmware-vcenter-sso-5-1-installation/
published: true
dsq_thread_id:
  - "1166615101"
---
I know vCenter SSO has been hashed out by 1000 other blogs, but not in the format I prefer to read so here it goes.  I am setting up a lab to demo VMware Horizon Workspace so this documentation is good for small or lab environments, but you should consult the <a href="http://www.vmware.com/support/pubs/vsphere-esxi-vcenter-server-pubs.html" target="_blank">documentation</a> or professional services for more advanced needs.  I am setting this up on a single server, but didn't want to just take the simple setup option so I am installing each component individually.

First, I will install MS SQL 2008 R2 Advanced Express edition, configured for mixed mode authentication, then SSO, followed by the inventory service and finally vCenter server.  I validated the network configuration by running the <a href="http://www.virtxpert.com/running-vcenter-sso-5-1-pre-install-check-script/" target="_blank">vSphere 5.1 Pre-Install Script/fling</a> so in theory I am in good shape (so far anyways).
<ul>
	<li>Launch the SSO setup from the CD (or navigating to the Single Sign On folder and launching VMware-SSO-Server.exe)</li>
	<li>Select your language, after a few minutes its next, next, accept+next to get through licensing agreements</li>
	<li>Select your installation type, since this is the first SSO server I will be selecting "Create the primary node for a new vCenter SSO installation."  If this were an additional server for HA or in a multi-site environment you would select "Join and existing vCenter SSO install" and click next</li>
	<li>Next, select whether this is a basic install where you will only have a single server/node or if it will be the primary node for a multinode environment.  From a flexibility stand point, I can't see why you wouldn't always select the 2nd option.</li>
	<li>Provide your default admin password.</li>
	<li>In my case, I am using an existing database so you need to run the rsaIMSLiteMSSQLSetupTablespaces.sql file to create the database.</li>
	<li>Fill in the appropriate database information (don't forget to verify that TCP/IP and Named Pipes are enabled)</li>
	<li>Verify the FQDN or IP</li>
	<li>Enter your service account</li>
	<li>Select the install directory, the HTTPS port and let it rip and if all goes well you will finish up your SSO install.</li>
</ul>
Next up is the Inventory Service.
<ul>
	<li><span style="line-height: 13px;">Launch the Inventory Service setup from the CD (or navigating to the Inventory Service folder and launching VMware-inventory-service.exe)</span></li>
	<li>Next, Next, Accept+Next</li>
	<li>Select the install folder</li>
	<li>Verify the FQDN</li>
	<li>Verify the port information</li>
	<li>Select the inventory size</li>
	<li>Enter the password for the admin@System-Domain account you setup in the SSO setup and click next</li>
	<li>Click Install Certificates then Install</li>
	<li>Once again, assuming all goes well click on Finish.</li>
</ul>
Finally, lets install vCenter Server.
<ul>
	<li><span style="line-height: 13px;">Launch the vCenter Server setup from the CD (or navigating to the vCenter Server folder and launching VMware-vcserver.exe)
</span></li>
	<li>Select your language</li>
	<li>Next, Next, Accept+Next</li>
	<li>Enter your license key</li>
	<li>In my case, I am selecting to use an existing DB</li>
	<li>Launch SQL and create a DB for vCenter.  Since I did not create a DSN, I need to do so before I can continue.  When <a href="http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&amp;cmd=displayKC&amp;externalId=2032885" target="_blank">creating your DSN</a>, make sure to change to your vCenter SQL database.</li>
	<li>Enter your vCenter service account</li>
	<li>You will likely select Create a standalone vCenter instance here</li>
	<li>Verify the ports, in my case because I am installing everything on the same server I had to change the HTTP port, I changed it to 8181.</li>
	<li>Select the inventory size, this is likely the same setting you selected previously.</li>
	<li>Enter the SSO credentials</li>
	<li>Select the admins for vCenter.  The administrators group may be adequate for you, I opted to create a new group called vCenter_admins</li>
	<li>Select where to install vCenter and click Install</li>
	<li>Fingers crossed, you should be all set pretty soon.</li>
</ul>
Now that my install is finished, I can log in with my AD user account I created and placed in my vCenter_admins group!

<a href="http://www.virtxpert.com/wp-content/uploads/2013/03/vCenterSSO.jpg"><img class="aligncenter size-full wp-image-625" alt="vCenterSSO" src="http://www.virtxpert.com/wp-content/uploads/2013/03/vCenterSSO.jpg" width="898" height="661" /></a>