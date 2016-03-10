---
ID: 2972
post_title: 'Configure the vRealize Automation Appliance &#8211; vRealize Automation Series Part 3'
author: Jonathan Frappier
post_date: 2014-11-16 08:00:54
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/configure-vrealize-automation-appliance-vrealize-automation-series-part-3/
published: true
dsq_thread_id:
  - "3230457259"
---
[display-posts category="vRA Home Lab"]

In the last post we deployed the vCloud Automation Center / vRealize Automation appliance, while its mostly a straight forward installation I will likely hold on to the horrors (...okay horror is a storng word) of my first deployment where I could not resolve typos from the OVF wizard - take your time deploying the OVF for a smooth experience.  Now its time to configure the appliance before we move on the IaaS installation.  If you have not already done so, make sure you can resolve the FQDN of your appliance, if like me you are running the appliance behind the VMware Workstation NAT network you will need to likely add a host file entry or use your lab domain controller as your DNS server - I went with the former.
<ul>
	<li>Navigate to https://vxprt-vcac01.vxprt.local:5480 (replace with your URL)</li>
	<li>Log in as root and the password you set during the OVF deployment</li>
	<li>You will now be in the appliance VAMI with no services showing, don't work that is expected</li>
	<li>Click on the System tab &gt;&gt; Time Zone; set your time zone appropriately and click Save Settings</li>
	<li>Click on the Admin tab &gt;&gt; Time Settings; change the Time Sync Mode pull down menu to use time server then set the time server to the IP address of your domain controller (or dedicated NTP server) and click Save Settings</li>
	<li>Verify that NTP Status is Enabled: Yes, NTP Started: Yes,</li>
	<li>Click on the vCAC Settings tab; click Resolve Host Name - it should fill in the FQDN of your host, click Save Settings</li>
	<li>Click the SSL tab, from the Chose Action pull down menu select Generate Self Signed Certificate.  Fill in the Common Name with the FQDN and other fields as appropriate, here is what mine looks like:</li>
</ul>
[caption id="attachment_2978" align="aligncenter" width="831"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/vcac-appliance-ssl-self-signed-generate.png"><img class="size-full wp-image-2978" src="http://www.virtxpert.com/wp-content/uploads/2014/11/vcac-appliance-ssl-self-signed-generate.png" alt="vCAC / vRA applaince - generate self signed certificate" width="831" height="361" /></a> vCAC / vRA applaince - generate self signed certificate[/caption]
<ul>
	<li>Click the Replace Certificate button; after a few moments you will see a message that the certificate was successfully replaced</li>
	<li>Click the SSO tab - you will see the SSO status is Not Connected, because we haven't connected it yet :)  Enter your vCenter server FQDN with port 7444 appended to the end, for example I am using vxprt-vc01.vxprt.local:7444.  Now enter the SSO administrator username which if you've not created any other users in vsphere.local would be administrator@vsphere.local and the password.  Of course for production deployments I'd make an additional user account specific for this; sso_bind_vcac or similar.  Once everything is entered, click Save Settings.  When prompted click OK to accept the certificate.</li>
	<li>Don't panic here, this part takes a few minutes to complete...tick tock tick tock...</li>
</ul>
And here we are - SSO configuration updated successfully

[caption id="attachment_2981" align="aligncenter" width="830"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/vcac-sso-vsphere-connected.png"><img class="size-full wp-image-2981" src="http://www.virtxpert.com/wp-content/uploads/2014/11/vcac-sso-vsphere-connected.png" alt="vCAC / vRA using vSphere SSO" width="830" height="351" /></a> vCAC / vRA using vSphere SSO[/caption]

Errors are likely time sync related, which is why NTP is so important.  Make sure your configured your hosts to sync to your domain controller, and that the offset was such that NTP was actually able to sync.  Check the appliance date and time at Admin &gt;&gt; Time Settings to make sure your appliance time is also correct.

Just a few more steps and you'll be ready to move on to the IaaS components.
<ul>
	<li>Click on the Licensing tab and enter the license information for vCloud Automation Center / vRealize Automation then click Save Settings (this also takes a while)</li>
	<li>Click on the Database tab, here you could change to point to an external appliance just <a href="http://kb.vmware.com/kb/2083563" target="_blank">running database services as suggested in VMware KB 2083563</a>, though give our lab resources, the internal one will be fine</li>
	<li>The messaging and HA tabs are new for 6.1, <a href="http://grantorchard.com/vcac/implementation/vra-appliance-clustering-3-minutes/" target="_blank">Grant Orchard has a great video on how easy it is to setup HA</a> for the vCloud Automation Center / vRealize Automation appliance on his blog.  It appears you can also use an external RabbitMQ server as well, though curious if others are supported as well - I'll have to dig into that later</li>
</ul>
And with that, the vCloud Automation Center / vRealize Automation appliance configuration is done!  You should now be able to browse https://vxprt-vcac01.vxprt.local and click the vCloud Automation Center / vRealize Automation Console, or go directly to https://vxprt-vcac01.vxprt.local/vcac

[caption id="attachment_2982" align="aligncenter" width="889"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/vcac-login.png"><img class="size-full wp-image-2982" src="http://www.virtxpert.com/wp-content/uploads/2014/11/vcac-login.png" alt="vCloud Automation Center / vRealize Automation login page" width="889" height="449" /></a> vCloud Automation Center / vRealize Automation login page[/caption]

Because we are using vSphere SSO, your URL will redirect to the vCenter SSO URL, https://vxprt-vc01.vxprt.local:7444 for example - that is normal and as expected.  While we can't do much here yet without the IaaS components installed, log in as administrator@vsphere.local to verify all is working.  Note it may take some time for all services to fully start.

[caption id="attachment_3001" align="aligncenter" width="1087"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/vcac-61-appliance-running.png"><img class="size-full wp-image-3001" src="http://www.virtxpert.com/wp-content/uploads/2014/11/vcac-61-appliance-running.png" alt="vCloud Automation Center / vRealize Automation appliance logged in" width="1087" height="549" /></a> vCloud Automation Center / vRealize Automation appliance logged in[/caption]

If you get the dreaded "Login failed. Please contact your System Administrator and report error code xxxxxxxxx." check the time on your DC, VCSA and vCAC applaince.  You can try to force it to sync using sntp –P no –r 192.168.6.5.  Another <a href="http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&amp;cmd=displayKC&amp;externalId=1005092" target="_blank">handy article to troubleshoot NTP can be in the VMware KB</a> 1005092.