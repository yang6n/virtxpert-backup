---
ID: 1318
post_title: Installing the vCenter Support Assistant
author: Jonathan Frappier
post_date: 2013-08-28 10:59:26
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/installing-vcenter-support-assistant/
published: true
dsq_thread_id:
  - "1655079743"
---
The vCenter support assistant is a free appliance from VMware that assists in submitting support cases to VMware while collecting relevant logs.  This should be installed in every environment now BEFORE you have a problem!  The installation is very easy:
<ol>
	<li>Deploy the OVF as any other and power on.</li>
	<li>Set the root password at boot</li>
	<li>Configure your network settings</li>
	<li>Navigate to the URL/IP of your vCenter Support Assisant</li>
	<li>Register the plugin via the Support Assistant web ui (should get a message that it registered successfully<a href="http://www.virtxpert.com/wp-content/uploads/2013/08/vcenterappliance.png"><img class="aligncenter size-full wp-image-1319" style="margin: 5px;" alt="vcenterappliance" src="http://www.virtxpert.com/wp-content/uploads/2013/08/vcenterappliance.png" width="222" height="276" /></a></li>
	<li>If you are still using the Windows client, you should now have a vCenter Support Assistant option under Solutions and Applications, <a href="http://www.virtxpert.com/vcenter-support-assistant-web-client-access/">if you are using the Web Client, there are some additional steps to take</a>.</li>
	<li>The vCenter support assistant checks to ensure it is working properly. <a href="http://www.virtxpert.com/wp-content/uploads/2013/08/vcentersupportnext.png"><img class="aligncenter  wp-image-1320" style="margin: 5px;" alt="vcentersupportnext" src="http://www.virtxpert.com/wp-content/uploads/2013/08/vcentersupportnext.png" width="634" height="281" /></a></li>
	<li>Click Next and log into My VMware and start creating SRs!</li>
</ol>