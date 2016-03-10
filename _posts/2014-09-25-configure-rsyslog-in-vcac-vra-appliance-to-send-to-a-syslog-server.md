---
ID: 2650
post_title: >
  Configure rsyslog in vCAC / vRA
  appliance to send to a syslog server
author: Jonathan Frappier
post_date: 2014-09-25 10:35:00
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/configure-rsyslog-in-vcac-vra-appliance-to-send-to-a-syslog-server/
published: true
dsq_thread_id:
  - "3052953878"
---
One option not available in the vCloud Automation Center (vCAC) appliance VAMI is the ability to send logs to a syslog server, such as Splunk or LogInsight (does anyone know if this has been exposed in vRA 6.1?), thankfully since the appliance is built on linux, its just a matter of configuring rsyslog.  If you are using LogInsight you can use the <a href="https://solutionexchange.vmware.com/store/products/vcac-log-insight-content-pack#.VCQi0_ldXYE" target="_blank">LogInsight Content Pack</a>.  While I have LogInsight, I want to do this manually to send logs as if I were using a generic syslog server.  As you can see here, none of my vCAC logs are here (my appliance is named vcacapp)

<a href="http://www.virtxpert.com/wp-content/uploads/2014/09/vcacapp-loginsight-search.jpg"><img class="aligncenter size-full wp-image-2653" src="http://www.virtxpert.com/wp-content/uploads/2014/09/vcacapp-loginsight-search.jpg" alt="vcacapp-loginsight-search" width="890" height="173" /></a>

&nbsp;

Here is how to configure the vCAC appliance to send logs:
<ul>
	<li>SSH to your vCAC / vRA appliance</li>
	<li>Type vi /etc/rsyslog.conf</li>
	<li>At the end of the file enter</li>
</ul>
<pre>*.*    loginsight.fqdn.tld:port</pre>
<ul>
	<li>For example loginsight.test.lab:514</li>
	<li>Save the file and restart syslog by typing</li>
</ul>
<pre>service syslog restart</pre>
Now if you go back to LogInsight or whatever syslog server you are using you can see logs being collected.  Logging, like monitoring involves a bit of science instead of just dumping logs into your syslog server.  If you have LogInsight, check out their content packs as that would be the preferred option in my opinion.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/09/vcacapp-loginsight-search-setup.jpg"><img class="aligncenter size-full wp-image-2655" src="http://www.virtxpert.com/wp-content/uploads/2014/09/vcacapp-loginsight-search-setup.jpg" alt="vcacapp-loginsight-search-setup" width="889" height="239" /></a>