---
ID: 1214
post_title: 'EMC Networker 8 &#8211; Problem Contacting Server Connection Refused: Connect'
author: Jonathan Frappier
post_date: 2013-08-05 10:25:30
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/emc-networker-8-problem-contacting-server-connection-refused-connect/
published: true
dsq_thread_id:
  - "1547713830"
---
What started off in hopes of finding some great, unknown/undocumented Networker bug turned into an annoying support experience, but even better for you the reader a funny story (funny if it doesn't happen to you!).  In trying to reverse engineer an environment, much of which was not or was poorly documented, I needed to determine how our backups were configured so off I went to review the EMC Networker 8.0 configuration, only problem was I couldn't log in.  Now I <del>knew</del> was pretty certain it was running correctly as I could see the backups from Networker getting larger in Data Domain, I would get email alerts etc.  The only, seemingly, relevant post in the support.emc.com site suggested the web server was not installed/running correctly but GST started, verified the service was installed properly by running chkconfig --list gst and I wasn't seeing any errors in the daemon.raw log about the web server not being found; so I continued my search.  Even the ECN was lacking in posts/questions on Networker (I suspect because I am not an early fan of it, probably not to many people using it).  I also tried to stopping/starting Networker by running /etc/init.d/networker stop and start - again no errors.  After my initial search turned up empty, the next step was to open a support ticket - after all I would have to wait a while anyways so kick that process into gear.

<a href="http://www.virtxpert.com/wp-content/uploads/2013/07/networker-error.png"><img class="aligncenter size-full wp-image-1215" alt="networker-error" src="http://www.virtxpert.com/wp-content/uploads/2013/07/networker-error.png" width="430" height="121" /></a>

Once my ticket was created I went back to basics; name resolution was working on the Networker servers, The resolv.conf and and interface configuration files all appeared correct, I could ping itself via name and IP, I could ping it from the Windows machine I was running the console from.  I also attempted to access the console via IP to further eliminate name resolution as the problem.  I verified that iptables was not blocking access and then proceeded to smash my head into my keyboard.  I rebooted the Networker VM (<a href="https://www.youtube.com/watch?v=W8_Kfjo3VjU" target="_blank">3 times</a>). Once on the phone with support, they had me check for an additional service not listed in the KB - the nsrd service.  You can check this in a RHEL/CentOS environment by running chkconfig --list nsrd - it found nothing.  The tech suggested that there was some problem and it needed to be re-installed, even though running ps -ef | grep nsrd showed a process running (I have never used Networker so wasn't about to argue with the support engineer).  At this point he told me to re-install the NMC and left me me for some fun.  I decided it was about time to backup the config, the following files according to the Networker 8 documentation are what you should care about:

<strong>[ultimatetables 4 /]</strong>

Additionally, there are some operating system files which are suggested to be backed up (personally I backed up these files to a separate directory because I am <a href="http://www.urbandictionary.com/define.php?term=CDO" target="_blank">CDO</a> like that)
<pre>cp /etc/rpc /etc/rpc.orig</pre>
<pre>cp /etc/ld.so.conf /etc/ld.so.conf.orig</pre>
Okay, now I have a backup and we just happened to have a consultant in the office the next day to help with a Data Domain problem we were having, he was originally involved in the design of the backup systems so he had a quick peak.  After a week plus of the support engineer not calling me back the consultant ran a simple command that shed light on the whole thing: nsrwatch and low and behold...

Registration Alert event: NetWorker evaluation mode has expired.
Regstration Alert event: Server is disabled: Install base enabler

They never finished setting up Networker - at least I only lost about 2 hours of my life chasing the support engineer down for help and its a DR site so no new data is going in.

<strong>Recap</strong>
<ul>
	<li>Check to make sure the previous person actually installed and registered it properly!</li>
	<li>Verify there are no errors in the daemon.raw log after service startup</li>
	<li>Verify DNS resolution and proper IP connectivity</li>
	<li><span style="line-height: 13px;">Check that the networker, gst and nsrd services are running, if either are missing you may need to reinstall</span></li>
	<li>If they are running, restart both by typing the command:  serivce gst stop, followed by service gst start.  Repeat for nsrd and networker.</li>
	<li>Call support and hope you don't get the engineer I had!</li>
</ul>