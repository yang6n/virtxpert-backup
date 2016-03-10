---
ID: 1707
post_title: >
  Using Splunk to Monitor Windows Active
  Directory Events
author: Jonathan Frappier
post_date: 2013-12-19 11:59:58
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/using-splunk-monitor-windows-active-directory-events/
published: true
dsq_thread_id:
  - "2061197213"
---
Having been working on Splunk for the last few days, one of my last hurdles was to easily monitor, present and alert on Active Directory events such as account lock outs, group changes etc.  Low and behold Splunk has an app called Splunk App for Microsoft Windows Active Directory - problem solved!  Well as Lee Corso would say - "Not so fast my friend!"

<a href="http://www.virtxpert.com/wp-content/uploads/2013/12/lee-corso1.jpg"><img class="aligncenter size-full wp-image-1708" alt="lee-corso1" src="http://www.virtxpert.com/wp-content/uploads/2013/12/lee-corso1.jpg" width="371" height="260" /></a>

&nbsp;

The <a href="http://docs.splunk.com/Documentation/ActiveDirectory/latest/DeployAD/Deploymentprocess" target="_blank">documentation </a>for the Splunk App for AD starts with a warning, that its complicated to install...meh they just want PS revenue right?  The documentation starts off straight forward, mostly configuring your audit policies to log relevant information but ends up in a twisty turvey rabbit hole of horror!  So much so, that the sales rep even suggested I use another app!  So, here is how to actually monitor AD events, not using the Splunk App for AD.

The app you should look at, of course if it meets all of your requirements, is the <a href="http://apps.splunk.com/app/647/">Windows Security Operations Center</a> app.  This app is not available for direct install from the app market directly from Splunk, you will need to download it.  Also it should be noted that as of this writing its only certified to work  Splunk 5, however I am testing it with Splunk 6 and having only a few minor problems that I suspect are related to my audit policy versus the application not working.  In my limited test environment, its generating just under 100MB per day (about 75 user accounts and tests scenarios like adding/removing/deleting accounts from the domain admins group).  For purposes of this walk through, I'll assume you have a central <a title="Using Splunk to monitor Windows Event Logs" href="http://www.virtxpert.com/using-splunk-monitor-windows-event-logs/">Splunk server already installed</a> and the Universal Forwarder installed on your Domain Controller(s).
<ul>
	<li>In my test environment, I have configured a Group Policy for my domain controllers for Audit Policy to log success and failure of all defined events (logon, account management, policy change, privilege use, and system events).</li>
	<li>Download the Windows Security Operations Center app from <a href="http://apps.splunk.com/app/647/">http://apps.splunk.com/app/647/</a></li>
	<li>Log into Splunk and click on the Manage Apps button</li>
	<li>Click Install app from file and browse the location you saved the file in the first step and click Upload.</li>
	<li>Click Set up now</li>
	<li>If you have used the default installation and configuration as we've done in the Using Splunk to Monitor Windows Event Logs post, then leave index and sourcetype at their defaults and click Save.</li>
	<li>If you return to the dashboard you'll now see the Windows Security Operations dashboard, click on the Login events menu in the dashboard and click Active Directory unsuccessful logins.  If you have had any, you should now see those events.</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2013/12/splunksec-failedlogins.png"><img class="aligncenter size-full wp-image-1714" alt="splunksec-failedlogins" src="http://www.virtxpert.com/wp-content/uploads/2013/12/splunksec-failedlogins.png" width="622" height="315" /></a>

&nbsp;
<ul>
	<li>As I navigate through the other menus, I am also seeing data related to new accounts (if you recall we created an account for Splunk to read AD accounts for authentication), accounts I've unlocked and software I've installed (the Splunk UniversalForwarder specifically).</li>
</ul>
<strong>Summary</strong>

The Windows Security Operations Center App for Splunk is an easy to install and configure app, unlike the official Splunk App.  If you have a need to monitor AD events, this app should come in handy.  Of course at the end of the day its still Splunk, so if you can find it in your event log, you can find it in Splunk.