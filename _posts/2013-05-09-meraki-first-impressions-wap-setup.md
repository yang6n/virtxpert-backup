---
ID: 797
post_title: 'Meraki First Impressions &#8211; WAP Setup'
author: Jonathan Frappier
post_date: 2013-05-09 20:19:32
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/meraki-first-impressions-wap-setup/
published: true
dsq_thread_id:
  - "1295924410"
---
I am finally setting up the Meraki access point I received through a promotion they were offering and wanted to share with you a bit about the setup.

For those unfamiliar with Meraki, they make a series of devices that can be managed through a "cloud" based controller - cloud being they provide a hosted management interface for you rather than requiring a hardware or software based on premise controller such as Cisco, AeroHive or Rukus.  Meraki was acquired by Cisco in November of 2012.

First I connected the access point to my network, then opened  browser and went to dashboard.meraki.com to create an account.  During the account setup, I was asked to provide the serial number of the access point and clicked create network.  Once taken to the dashboard, I was able to see the access point, identified as an MR12 with the appropriate MAC address in the dashboard.

[caption id="attachment_798" align="aligncenter" width="585"]<a href="http://www.virtxpert.com/wp-content/uploads/2013/05/meraki-dashboard.jpg"><img class=" wp-image-798 " alt="meraki-dashboard" src="http://www.virtxpert.com/wp-content/uploads/2013/05/meraki-dashboard.jpg" width="585" height="357" /></a> Meraki dashboard after account creation.[/caption]

The access point also received a basic configuration based on the information I entered during the account creation and was available, albeit as an unsecured network, for clients to connect to.<!--more-->
<p style="text-align: center;"><a href="http://www.virtxpert.com/wp-content/uploads/2013/05/ssid.jpg"><img class="aligncenter  wp-image-799" alt="ssid" src="http://www.virtxpert.com/wp-content/uploads/2013/05/ssid-576x1024.jpg" width="194" height="344" /></a></p>
<p style="text-align: left;">To configure the access point, I went to the configure section of the dashboard, and selected Access Control, here I can configure the various security options for the access point(s) including the encryption type, ability to configure/require a splash page, group policies (not AD group policies by polices defined by you), bandwidth controls and content filtering.</p>
<p style="text-align: center;"><a href="http://www.virtxpert.com/wp-content/uploads/2013/05/configureAP.jpg"><img class="aligncenter  wp-image-800" alt="configureAP" src="http://www.virtxpert.com/wp-content/uploads/2013/05/configureAP.jpg" width="704" height="374" /></a></p>
<p style="text-align: left;">I saved the configuration and sure enough after just a few moments I could see my new SSID was now secured.</p>
<p style="text-align: left;">I have been keeping an eye on Meraki for quite some time, but never had a chance to work with them prior to their acquisition by Cisco.  The setup and basic configuration of a single AP was quite easy and there are still several features which I have not tried (though hope to followed up with a blog post).  The options available at the price point is quite impressive, though I will be curious to see how Cisco manages Meraki, their products and pricing - it was certainly a much better buy for the SMB space than Linksys was.</p>