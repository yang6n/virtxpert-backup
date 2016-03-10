---
ID: 1873
post_title: >
  How to change Splunk alerts from Real
  time to scheduled
author: Jonathan Frappier
post_date: 2014-01-21 07:59:23
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/how-to-change-splunk-alerts-from-real-time-to-scheduled/
published: true
dsq_thread_id:
  - "2153469108"
---
Splunk allows you to create either real time or scheduled alerts, and while real time alerts would seem logical they can be quite CPU intensive.  In fact, some suggest limiting to 1 real time search per CPU core even though the default limits will be about 3 per core.  You can see more on the limits.conf and how to change it <a href="http://docs.splunk.com/Documentation/Splunk/5.0.3/Admin/Limitsconf" target="_blank">here</a>.  Rather than creating real time alerts, you can set or change existing alerts to run on a schedule.  In reality, most monitoring software works on a polling interval anyways so this is not far from what you are likely doing today with something like Nagios.

The process for creating or changing Splunk alerts from real time to scheduled is fairly straight forward.  By default, however, the shortest time period Splunk provides is 1 hour.  If you want to schedule Splunk alerts to run more frequently you will need to use the "Run on CRON scheduler" option.  Cron schedule examples give me a bit of a headache, but since we only have to worry about a per minute time interval since Splunk provides other options here is a quick how to on how to set these up, or change them.

Changing a Splunk Alert from Real Time to Scheduled
<ul>
	<li>Log into your Splunk server</li>
	<li>Under Search and Reporting click on Alerts</li>
	<li>Find the Alert you wish to change and click<span style="color: #3366ff;"><strong> Edit &gt;&gt; Edit Alert type and trigger</strong></span></li>
	<li>Under Alert type click on <span style="color: #3366ff;"><strong>Scheduled</strong></span></li>
	<li>Change the time range to <span style="color: #3366ff;"><strong>Run on CRON schedule</strong></span>, or one of the other options if those better suit your need</li>
	<li>The "<strong><span style="color: #3366ff;">earliest</span></strong>" text box should be a negative number that matches how often you will run the alert.  For example if you want it to run every 5 minutes, set this to <span style="color: #993366;"><strong>-5m</strong></span></li>
	<li>In the "latest" box enter <span style="color: #993366;"><strong>Now</strong> </span>so that it will search logs between 5 minutes ago and run time</li>
	<li>In the <span style="color: #3366ff;"><strong>CRON Expression</strong> </span>box enter
<pre>*/5 * * * *</pre>
</li>
	<li>You can find more information about alert schedules <a href="http://docs.splunk.com/Documentation/Splunk/6.0.1/Alert/Definescheduledalerts" target="_blank">here</a></li>
	<li>Your alert window should look something like:</li>
</ul>
<p style="text-align: center;"><a href="http://www.virtxpert.com/wp-content/uploads/2014/01/splunk-alert.png"><img class="aligncenter  wp-image-1874" alt="splunk-alert" src="http://www.virtxpert.com/wp-content/uploads/2014/01/splunk-alert.png" width="472" height="358" /></a></p>

<ul>
	<li>Click <span style="color: #3366ff;"><strong>Next</strong> </span>and configure the Actions you want to enable, such as email subject, recipients and how to include information (inline, CSV or PDF) or even options such as running a script</li>
	<li>Click <span style="color: #3366ff;"><strong>Save</strong></span>.  Your alert will now run at the defined schedule.</li>
</ul>
<strong>Summary</strong>

While alerts can be swell, they will have an impact on your server and, if you have to many alerts, you might not actually receive any of them, which would be bad.  Scheduling alerts is an easy way to make sure your Splunk server is not resource constrained.