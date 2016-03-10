---
ID: 653
post_title: >
  Building a VMware Horizon Workspace Lab
  – Part 3 Web Config
author: Jonathan Frappier
post_date: 2013-04-01 11:29:28
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/building-a-vmware-horizon-workspace-lab-part-3-web-config/
published: true
dsq_thread_id:
  - "1179175518"
---
In my <a href="http://www.virtxpert.com/building-a-vmware-horizon-workspace-lab-part-2/" target="_blank">previous posts</a>, I setup a new lab environment to run VMware Horizon and configured the vApp through the console so I could access the web interface of Horizon.  I left off at the 'Begin Setup Wizard' web interface, so that is where I will pick up.

Step 1:
<ul>
	<li><span style="line-height: 13px;">Enter the license key from my.vmware.com you received when you signed up for the eval.</span></li>
	<li>Enter the admin user password you will use</li>
	<li>Click Next</li>
</ul>
Step 2:
<ul>
	<li><span style="line-height: 13px;">Click the continue with the Setup Wizard button</span></li>
	<li>Select Internal Database for lab/testing purposes.  Selecting External will prompt you for  your DB connection string but is beyond the scope of the reviewers guide.</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2013/03/configdb.jpg"><img class="aligncenter size-full wp-image-654" alt="configdb" src="http://www.virtxpert.com/wp-content/uploads/2013/03/configdb.jpg" width="722" height="264" /></a>

&nbsp;
<ul>
	<li><span style="line-height: 13px;">Enter your Active Directory information and click the Test Setting and Sync button.  The account you use for the Bind DN must have the email field filled in in your AD.  Also your base DN cannot be the entire domain (e.g. dc=domain,dc=tld) so set this to an existing OU.  I nested a group and users OU under a generic OU so I could search both from on base DN. *****MAKE NOTE OF YOUR BIND USER INFO*****</span></li>
	<li>Click Next</li>
	<li>On the map user attributes page, click next (this is where, if necessary, you could change the mappings between Horizon and AD)</li>
	<li>On the select users page, click next</li>
	<li>Add the groups you wish to have access and click Next.</li>
</ul>
<p style="text-align: center;"><a href="http://www.virtxpert.com/wp-content/uploads/2013/03/groups.jpg"><img class="aligncenter  wp-image-655" alt="groups" src="http://www.virtxpert.com/wp-content/uploads/2013/03/groups.jpg" width="1147" height="430" /></a></p>

<ul>
	<li><span style="line-height: 13px;">Select how often you wish to synchronize AD and Horizon.  This (to me) means that your new AD users will not have immediate access to Horizon, but it appears as though you can manually sync later (TBD).</span></li>
	<li>Review the users/groups being added and click Save and Continue.</li>
	<li>Click the next link.</li>
	<li>Click Next on the SSL cert page.</li>
	<li>Click enable for Data and Web Applications (I am also selecting ThinApp as I will be interested in testing that later).</li>
	<li>Click Next.</li>
	<li>Click Go to Horizon Workspace.</li>
	<li>Log into the Horizon web app</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2013/03/login.jpg"><img class="aligncenter size-full wp-image-657" alt="login" src="http://www.virtxpert.com/wp-content/uploads/2013/03/login.jpg" width="437" height="265" /></a>

&nbsp;

So I got a little hung up here, log in as...who?  I tried the admin user I created on the configurator  - no luck.  An account that is part of the AD group I added, nope that didn't work either.  It was the service account I used in the Bind setup!  Also, I received an error about time drift being off, of course I forgot to enable NTP on my servers, so I went back and enabled NTP with the same servers: 0.north-america.pool.ntp.org.

Also, now that I am logged in and can review some settings, I see that one of my user accounts that is in my Horizon_users AD group has not been given permission.  I logged into the Connector web interface and found that the user account in question did not have a last name or email set in the AD attributes:

<strong>Missing required attributes {0} for {1}:Missing required attributes [lastName, email] for CN=username,OU=LAB_USERS,OU=LAB_ACCTS,DC=lwlab,DC=local</strong>

I had to go to Directory Sync, Sync Rules to run back through the wizard once I updated the AD account.  Another problem I had, my connector-va time was off, even though NTP was running and the correct time zone was set.  I had set each of my 3 hosts to sync to an external time source but was clearly having problems.  I set my Domain Controller as an authoritative time source and pointed each of the hosts to it, this seemed to correct the problem as a restart of all of the VMs brought them within 2-5 seconds of the configurator and persisted over 60 hours.

After resolving those two problems, I am able to log in as a regular user to my (albeit empty) Horizon gateway.
<p style="text-align: center;"><a href="http://www.virtxpert.com/wp-content/uploads/2013/04/userlogin.jpg"><img class="aligncenter  wp-image-669" alt="userlogin" src="http://www.virtxpert.com/wp-content/uploads/2013/04/userlogin.jpg" width="716" height="313" /></a></p>
The next section of the guide, and probably the most fun/interesting part revolves around View integration, I am not running View so I will not be doing this (now).  Instead I will configure the 'Data' section, formerly known as Octopus (and still referenced as such in various config/setting places).

&nbsp;