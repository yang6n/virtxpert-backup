---
ID: 1682
post_title: >
  Using Splunk to monitor Windows Event
  Logs
author: Jonathan Frappier
post_date: 2013-12-17 10:44:55
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/using-splunk-monitor-windows-event-logs/
published: true
dsq_thread_id:
  - "2056490578"
---
A few posts ago I reviewed a product called <a title="Auditing Active Directory with Netwrix Auditor 5.0" href="http://www.virtxpert.com/auditing-netwrix-auditor-5-0/">Netwrix </a>which you can use to easily monitor your Windows and AD event logs.  The installation was easy because it was purpose built for motioning such logs, but what about if this wasn't an option for you and you needed to centrally collect logs via some syslog type service?  In this post I'll review setting up Windows to send its logs to Splunk which you can download <a href="http://www.splunk.com/download" target="_blank">here</a>.  You can use the Enterprise Edition for up to 60 days, indexing 500MB of data, or the free version with some limitations on features such as no alerting withe the same 500MB restriction (<a href="http://www.splunk.com/view/SP-CAAAE8W" target="_blank">Free vs Enterprise</a>).

First, let's install Splunk a server.  I am downloading for CentOS but Splunk has long installed easily on Windows as well.  The tracking they do makes direct download via wget a bit annoying, so I had to download and them move into my VM.
<ul>
	<li>After running splunk-ver.rpm I had to navigate to /opt/splunk/bin and ran ./splunk enable boot-start because I wanted this to start automatically</li>
	<li>Agree to the license agreeemnt</li>
	<li>You should now see Splunk as a service if you run chkconfig --list</li>
	<li>Start Splunk</li>
</ul>
<pre>Service splunk start</pre>
<ul>
	<li>Now you should be able to navigate to http://url:8000 (if you are running iptables you'll need to add port 8000)</li>
	<li>The default username and password is admin/changeme which you'll be forced to change.</li>
</ul>
<p style="text-align: center;"><a href="http://www.virtxpert.com/wp-content/uploads/2013/12/splunkfirstlogin.jpg"><img class="aligncenter  wp-image-1686" alt="splunkfirstlogin" src="http://www.virtxpert.com/wp-content/uploads/2013/12/splunkfirstlogin.jpg" width="563" height="307" /></a></p>

<ul>
	<li>From here, for production purposes you should secure as you normally would, Splunk supports its own user database or LDAP.  Navigate to Settings &gt;&gt; Access Control &gt;&gt; Authentication Methods to enable and configure LDAP.  For now I'll just just use the built in splunk users, or see my post on <a title="Enabling Active Directory Authentication for Splunk" href="http://www.virtxpert.com/enabling-active-directory-authentication-for-splunk/">configuring Splunk for AD Authentication</a>.</li>
	<li>Next we need to configure Splunk to listen before we can start forwarding new data.</li>
	<li>Navigate to Settings &gt;&gt; Data &gt;&gt; Forwarding and Receiving</li>
	<li>Under Receive Data click 'Add New' and set the port number, default is 9997 which seems swell to me.</li>
</ul>
Now that Splunk is up and running, lets install the Universal Forwarder for Windows.  An early tip, check the size of your Event Log files, if they are set to rotate at a fairly small size you'll be fine, otherwise as soon as we finish this install stop the Splunk Universal Forwarder service so you can change the default current_only setting which is set to 0 (zero).  This mean it will send all historical logs which may quickly meet your 500MB quota.  Alternatively you could wipe your log files if you did not need the historical data.
<ul>
	<li>Download the Universal Forwarder for Windows</li>
	<li>Next, Accept the license agreement, select your install location or accept the default and click next</li>
	<li>We did not setup a Deployment Server, so leave this page blank</li>
	<li>Enter the hostname or IP of your server and the port you setup the receiver on</li>
	<li>We did not setup certificates so leave this blank</li>
	<li>Select whether you want to send only local data, or data from remote machines as well.  This would allow you to only install the Universal Forwarder on one machine but requires the service run as a privileged account.  The various Splunk services on Windows take up somewhere around 60MB of memory, at least on a fairly low usage system.  For purposes of this test, just select Local Data Only</li>
	<li>Now you can select which logs you wish to send to Splunk as well as any additional log files in the 'Path to monitor' box.  I've enabled all Event Logs plus AD Monitoring.</li>
	<li>Use the packaged Splunk Technology Add-on so it can map events in a <a href="http://en.wikipedia.org/wiki/Common_Information_Model_(computing)" target="_blank">CIM </a>format for Splunk</li>
	<li>And click Install... and click Finish</li>
	<li>Now stop the SplunkForwarder service (if you want to change the default logging behavior)</li>
</ul>
Now that the service is stopped, edit C:\Program Files\SplunkUniversalForwarder\etc\apps\Splunk_TA_windows\local\inputs.conf to and change
<pre>[WinEventLog://Setup] and [WinEventLog://ForwardedEvents]
checkpointInterval = 5
current_only = 1
disabled = 0
start_from = oldest</pre>
You can find more detailed information on the various configuration options in the inputs.conf file <a href="http://docs.splunk.com/Documentation/Splunk/6.0/admin/inputsconf" target="_blank">here</a>.  Now you can restart the SplunkForwarder service.  If you log into Splunk you should be able to search for something similar to host=domaincontrollername and start seeing logs.
<p style="text-align: center;"><a href="http://www.virtxpert.com/wp-content/uploads/2013/12/splunksearch.png"><img class="aligncenter  wp-image-1697" alt="splunksearch" src="http://www.virtxpert.com/wp-content/uploads/2013/12/splunksearch.png" width="566" height="305" /></a></p>
<p style="text-align: left;"><strong>Summary</strong></p>
<p style="text-align: left;">This was a bit more involved than the next...next...next setup of Netwrix, but so far haven't had to pay anything, assuming we can keep the logs under 500MB a day.  At this point, we can add more servers and search all of our logs in one place, though the free version does not allow us to setup Alerts so its not a straight trade off between Netwrix and Splunk.  In my next post, I hope to review the Splunk App for Windows and Active Directory.</p>