---
ID: 675
post_title: >
  Enabling ThinApp for VMware Horizon
  Workspace
author: Jonathan Frappier
post_date: 2013-04-02 15:06:13
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/enabling-thinapp-for-vmware-horizon-workspace-2/
published: true
dsq_thread_id:
  - "1182141306"
---
In my previous <a href="http://www.virtxpert.com/building-a-vmware-horizon-lab-part-1/" target="_blank">posts</a>, I reviewed how to setup a lab for testing VMware Horizon Workspace.  Now that the lab is up and running, and I can log into VMware Horizon I want to setup access to ThinApp packages.  One quick note, the ability to use ThinApps seems to be limited to Internet Explorer, ThinApps do not appear in Chrome, not sure yet if this is a bug or configuration problem.

<em>**Update 2PM - My ThinApp finally showed up in Chrome, seemed to be excessively long but its there, not sure when it showed up since this morning but it made it eventually**</em>

<strong>Initial Configuration</strong>
<ul>
	<li>First, log into the configurator, click on Module Configuration to ensure ThinApp is enabled.</li>
	<li>Click on the 'Go to Connector' link to configure the settings for ThinApp<a href="http://www.virtxpert.com/wp-content/uploads/2013/04/thinappconfig.png"><img class="aligncenter  wp-image-676" style="margin-top: 10px; margin-bottom: 10px;" alt="thinappconfig" src="http://www.virtxpert.com/wp-content/uploads/2013/04/thinappconfig.png" width="828" height="340" /></a></li>
	<li>If prompted, log into the Connector and click on ThinApp packages.</li>
	<li>You will be prompted for the share where your ThinApps are (going to be) located.  Enter the network path.<a href="http://www.virtxpert.com/wp-content/uploads/2013/04/thinappconfigd.jpg"><img class="aligncenter  wp-image-677" style="margin-top: 10px; margin-bottom: 10px;" alt="thinappconfigd" src="http://www.virtxpert.com/wp-content/uploads/2013/04/thinappconfigd.jpg" width="418" height="193" /></a></li>
	<li> Click the Sync Now button, your ThinApp(s) should be listsed.  You are now configured for ThinApps.</li>
	<li>If no apps appeared, you may not have the correct path or permissions configured (though you only need read access).</li>
</ul>
<strong>Adding ThinApps to your Workspace</strong>

Now that you have configured VMware Horizon Workspace to use ThinApps, I will add a ThinApp to my catalog.
<ul>
	<li><span style="line-height: 13px;">Log into the gateway's administration interface (https://gatewayfqdn/SAAS/admin/dashboard</span></li>
	<li>You should now see the number of ThinApps listed in the Dashboard.<a href="http://www.virtxpert.com/wp-content/uploads/2013/04/thinapp.jpg"><img class="aligncenter size-full wp-image-678" alt="thinapp" src="http://www.virtxpert.com/wp-content/uploads/2013/04/thinapp.jpg" width="350" height="280" /></a></li>
	<li>Click on the Catalog tab, then ThinApp Packages.</li>
	<li>Click on the ThinApp you wish to configure an entitlement for.</li>
	<li>Click add group, or user entitlement, enter the group or user name and click Done.</li>
</ul>
<strong>Client Access</strong>
<ul>
	<li>From the users computer, if you have not already done so, install the VMware Horizon Workspace Windows client (available on the gateway log in page)</li>
	<li>Once installed, log into the client.  You should see the client syncing the ThinApp package. <a href="http://www.virtxpert.com/wp-content/uploads/2013/04/appsync.png"><img class="aligncenter size-full wp-image-679" style="margin-top: 10px; margin-bottom: 10px;" alt="appsync" src="http://www.virtxpert.com/wp-content/uploads/2013/04/appsync.png" width="263" height="348" /></a></li>
	<li>The size and number of applications will affect how long it takes to sync.</li>
	<li>ither log into the gateway directly or click Open Horizon Web Page from the client.   You should see the ThinApp listed.<a href="http://www.virtxpert.com/wp-content/uploads/2013/04/writer.jpg"><img class="aligncenter  wp-image-680" style="margin-top: 10px; margin-bottom: 10px;" alt="writer" src="http://www.virtxpert.com/wp-content/uploads/2013/04/writer.jpg" width="368" height="259" /></a></li>
	<li>Click on the ThinApp, if prompted click the Allow button.  Your app should load!</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2013/04/writerlaunch.jpg"><img class="aligncenter size-full wp-image-681" alt="writerlaunch" src="http://www.virtxpert.com/wp-content/uploads/2013/04/writerlaunch.jpg" width="596" height="337" /></a>

&nbsp;

This post was meant to be an overview of how to setup ThinApp to work with VMware Horizon.  There is a whole other science that goes into ThinApp'ing your applications that you must also become familiar with to successfully deploy your apps.  Once you have VMware Horizon Workspace up and running, adding ThinApps is fairly easy.