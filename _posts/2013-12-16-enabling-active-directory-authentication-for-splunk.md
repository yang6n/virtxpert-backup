---
ID: 1690
post_title: >
  Enabling Active Directory Authentication
  for Splunk
author: Jonathan Frappier
post_date: 2013-12-16 13:36:40
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/enabling-active-directory-authentication-for-splunk/
published: true
dsq_thread_id:
  - "2054556853"
---
A quick how-to for enabling Active Directory authentication for Splunk:
<ul>
	<li>Create user for BIND, basically a service account</li>
	<li>Check the box next to LDAP</li>
	<li>Click COnfigure Splunk to use LDAP and map groups</li>
	<li>Click the New button</li>
	<li>Enter a name for your LDAP</li>
	<li>Enter your AD or LDAP host</li>
	<li>Enter the port (389 or 689)</li>
	<li>Enter the BIND DN, for example CN=Jeff Smith,OU=Sales,DC=Fabrikam,DC=COM (*If you are using default OUs such as Users change OU to CN)</li>
	<li>Enter the password for the user</li>
	<li>Fill in the User and Group settings, the help for each section should be adequate to guide you, but here is an example screenshot</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2013/12/splunkusersettingsexample.jpg"><img class="aligncenter size-full wp-image-1691" alt="splunkusersettingsexample" src="http://www.virtxpert.com/wp-content/uploads/2013/12/splunkusersettingsexample.jpg" width="842" height="421" /></a>
<ul>
	<li>Click Save</li>
	<li>You should now be taken to a page with the LDAP strategies listed.</li>
	<li>Click on Map groups</li>
	<li>Click on the group you wish to map, for example you may wish for all Domain Admins to have the admin role, or you may want to create a specific AD group to give access to splunk</li>
	<li>Select the role(s) you wish to add for that group and click save.</li>
	<li>Return to the Splunk login page and log in with your AD credentials</li>
</ul>
<strong>Summary</strong>

Enabling Active Directory authentication for Splunk is quite simple and allows you to leverage Active Directory for all user access.