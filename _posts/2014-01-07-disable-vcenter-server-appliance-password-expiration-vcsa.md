---
ID: 1779
post_title: 'How to disable the vCenter Server Appliance Password Expiration #VCSA'
author: Jonathan Frappier
post_date: 2014-01-07 09:01:24
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/disable-vcenter-server-appliance-password-expiration-vcsa/
published: true
dsq_thread_id:
  - "2097732426"
---
It seems over the past few weeks, a folks have started to get burned by the vCenter Server Appliance (VCSA) password expriation, and I suppose that about lines up with the release of vSphere 5.5 coming just about 90 days ago.  There are a few options you can take:
<ol>
	<li>Disable the password expiration</li>
	<li>Configure a notification email to ensure you are notified before it expires</li>
</ol>
I will review both here, and suggest you strongly consider number 2 as your option as maintaining passwords indefinitely is not a good practice.

<strong>Disable the VCSA Password Expiration</strong>
<ul>
	<li>Log into the VCSA configuration UI at https://url_of_your_vcsa:5480</li>
	<li>Click on the <strong>Admin</strong> tab</li>
	<li>Select "<strong>No</strong>" for <strong>"Administrator password expires"</strong></li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/01/vcsa-password-expiration.png"><img class="aligncenter size-full wp-image-1780" alt="vcsa-password-expiration" src="http://www.virtxpert.com/wp-content/uploads/2014/01/vcsa-password-expiration.png" width="562" height="261" /></a>

&nbsp;

<strong>Set VCSA Password Expiration Notice</strong>

The password expiration notice relies on the SMTP server configuration in vCenter, lets check that first.
<ul>
	<li>Log into vCenter at https://url_of_your_vcsa:9443</li>
	<li>Click on <strong>vCenter</strong> in the navigation menu, click on <strong>vCenter Servers</strong></li>
	<li>Click on the vCenter server you wish to configure SMTP settings for</li>
	<li>Click on <strong>General</strong>, then click the <strong>Edit</strong> button</li>
	<li>Click on <strong>Mail</strong> and enter the SMTP server IP or FQDN and "From" address</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/01/vcenter-smtp-settings.png"><img class="aligncenter size-full wp-image-1781" alt="vcenter-smtp-settings" src="http://www.virtxpert.com/wp-content/uploads/2014/01/vcenter-smtp-settings.png" width="645" height="193" /></a>
<ul>
	<li>Now that your SMTP server details are set in vCenter, you can setup the VCSA to notify you of upcoming password expirations</li>
	<li>Log into the VCSA configuration UI at https://url_of_your_vcsa:5480</li>
	<li>Click on the Admin tab</li>
	<li>Enter the email address in the <strong>Email for expiration warning</strong> field that you wish to receive these notifications</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/01/vcsa-password-email-notification.png"><img class="aligncenter size-full wp-image-1784" alt="vcsa-password-email-notification" src="http://www.virtxpert.com/wp-content/uploads/2014/01/vcsa-password-email-notification.png" width="562" height="378" /></a><strong>Summary</strong>

Disable, or not to disable - only your organizations security policies can tell you the right answer, but I'd suggest getting a warning and resetting it in line with your standard password expiration period.

&nbsp;