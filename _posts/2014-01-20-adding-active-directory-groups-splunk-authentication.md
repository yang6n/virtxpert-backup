---
ID: 1863
post_title: >
  Adding additional Active Directory
  Groups for Splunk Authentication
author: Jonathan Frappier
post_date: 2014-01-20 13:05:45
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/adding-active-directory-groups-splunk-authentication/
published: true
dsq_thread_id:
  - "2150763654"
---
Here is a quick guide to adding additional Windows Active Directory groups for Splunk authentication to allow users to log in.  You can see <a title="Enabling Active Directory Authentication for Splunk" href="http://www.virtxpert.com/enabling-active-directory-authentication-for-splunk/">how to configure Splunk for Active Directory here</a>.  If you have not already done so, create the Active Directory group that you want to grant access to and add the users you want to to access Splunk into the group.
<ul>
	<li>Log into Splunk as an administrative user</li>
	<li>Click on <span style="color: #3366ff;"><strong>Settings &gt;&gt; Access controls</strong></span></li>
	<li>Click on <span style="color: #3366ff;"><strong>Authentication Method</strong></span>, then <strong><span style="color: #3366ff;">Configure Splunk to use LDAP and map groups</span></strong></li>
	<li>Click on the <span style="color: #3366ff;"><strong>Map groups</strong></span> links for your AD</li>
	<li>Click on the group you want to provide access to</li>
	<li>Select the roles you want to provide to the group and click <span style="color: #3366ff;"><strong>Save</strong></span>.</li>
	<li>Log out of Splunk and log back in as a user who is part of the AD group you added.</li>
</ul>
If you are not able to log into Splunk, do the following:
<ul>
	<li>Verify the user account object you are trying to log in as is within your user base DN setting for AD</li>
	<li>Click on <span style="color: #3366ff;"><strong>Settings &gt;&gt; Access controls &gt;&gt; Authentication method</strong></span> and click <span style="color: #3366ff;"><strong>Reload authentication configuration</strong></span></li>
	<li>Click on <span style="color: #3366ff;"><strong>Settings &gt;&gt; Server Controls &gt;&gt; Restart Splunk</strong></span></li>
</ul>