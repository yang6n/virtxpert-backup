---
ID: 3029
post_title: 'Install vRealize Automation IaaS Installation &#8211; vRealize Automation Series Part 6'
author: Jonathan Frappier
post_date: 2014-11-17 10:00:05
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/install-vrealize-automation-iaas-installation-vrealize-automation-series-part-6/
published: true
dsq_thread_id:
  - "3234080126"
---
[display-posts category="vRA Home Lab" display-posts posts_per_page="15"]

With SQL now installed, it's time to download and install the IaaS or Infrastructure-as-a-Service components.  Log into your IaaS server as the service account you created and provided to the PreReq script - in my case svc_vra_iaas.  Once you are logged in, close Server Manager, open a web browser and navigate to the URL of your vCloud Automation Center / vRealize Automation appliance, for example in my case https://vxprt-vcac01.vxprt.local.  You should now be at the VMware vCloud Automation Center Appliance page where we can get started

[caption id="attachment_3034" align="aligncenter" width="1023"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/vcac-appliance-iaas-download.png"><img class="size-full wp-image-3034" src="http://www.virtxpert.com/wp-content/uploads/2014/11/vcac-appliance-iaas-download.png" alt="vCloud Automation Center Appliance IaaS download page" width="1023" height="459" /></a> vCloud Automation Center Appliance IaaS download page[/caption]
<ul>
	<li>Click on the vCloud Automatin Center IaaS installation page link</li>
	<li>Click the link to download the IaaS installer - do not rename the installer</li>
	<li>Once downloaded, launch the installer by right clicking and select Run as Administrator - The vCloud Automation Center Configuration wizard will launch.</li>
	<li>On the Welcome page, click Next</li>
	<li>Accept the license terms and click Next</li>
	<li>Provide the username and password for the appliance, typically root, and click Next</li>
	<li>Here you could do either a Complete install which will put everyone on one server (our option) or a Custom install which allows you to install specific components on specific servers and build an HA configuration.  See the reference architecture document in the introduction post to learn more.  Click Next</li>
	<li>The PreReq checker will run.  Oddly enough in my case it says that Java is not okay, though when I ran the PreReq PowerShell script it said it downloaded and ran it fine.  If you run into any errors here cancel the install and re-run that script.  After re-running the PreReq script all tests passed, click Next</li>
</ul>
[caption id="attachment_3037" align="aligncenter" width="808"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/vcac-iaas-installer-prereq-check-passed.png"><img class="size-full wp-image-3037" src="http://www.virtxpert.com/wp-content/uploads/2014/11/vcac-iaas-installer-prereq-check-passed.png" alt="vCloud Automation Center / vRealize Automation IaaS prerequisites passed" width="808" height="608" /></a> vCloud Automation Center / vRealize Automation IaaS prerequisites passed[/caption]
<ul>
	<li>Enter the password for your user account, a passprhase you wish to use for the database encryption key and verify the SQL server is the correct server.  If you were using a separate SQL server, here is where you would change that.  Since we configured SQL for Mixed Mode and provided the svc_vra_iaas user with sysadmin rights, we can leave Use Windows Authentication checked.  Once everything is filled in, click Next</li>
	<li>On the DEM and Agent page, make note of the values here, we will need them later when adding vCenter as an endpoint; click Next</li>
</ul>
[caption id="attachment_3044" align="aligncenter" width="807"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/vcac-dem-agent-default-values.png"><img class="size-full wp-image-3044" src="http://www.virtxpert.com/wp-content/uploads/2014/11/vcac-dem-agent-default-values.png" alt="vCloud Automation Center DEM Agent default values" width="807" height="607" /></a> vCloud Automation Center DEM Agent default values[/caption]
<ul>
	<li>On the component registry page, click the Load button, vsphere.local should be filled into the field automatically</li>
	<li>Click on the Download button, once filled in click the Accept Certificate checkbox</li>
	<li>Fill in the SSO username and password, administrator@vsphere.local, then click the Test button</li>
	<li>Confirm the IaaS server FQDN was filled in properly, click the Test button</li>
	<li>With everything filled in and tested passed, click Next</li>
</ul>
[caption id="attachment_3045" align="aligncenter" width="808"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/vcac-iaas-component-registration.png"><img class="size-full wp-image-3045" src="http://www.virtxpert.com/wp-content/uploads/2014/11/vcac-iaas-component-registration.png" alt="vCloud Automation Center component registration" width="808" height="607" /></a> vCloud Automation Center component registration[/caption]
<ul>
	<li>On the Ready to Install page, click the Install button</li>
</ul>
The installation of the IaaS components, like some of the configuration on the appliance can take some time.  Watch the installation screen to see what it is doing - or get a cup of coffee :)  After a few minutes, you should get a message that the Installation completed - congratulations you have finished the easy part!
<ul>
	<li>Click the Next button</li>
	<li>On the Configuration is complete page, uncheck the Guide me through the initial system configuration box and click finish</li>
	<li>Return to you workstation or normal means of access the appliance web pages and log into your appliance (https://vxprt-vcac01.vxprt.local)</li>
	<li>Click on Tenants &gt;&gt; vsphere.local &gt;&gt; Administrators - notice anything different here?</li>
</ul>
Before installation of the IaaS components we couldn't assign any accounts to be infrastructure administrators because??? Yup - the Infrastructure-as-a-Server components were not installed!  With the vCloud Automation Center / vRealize Automation Appliance and IaaS components installed, we can now start to get everything configured.

&nbsp;

&nbsp;