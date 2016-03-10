---
ID: 3454
post_title: >
  Configuring CentOS to to send logs to
  Nagios Log Server
author: Jonathan Frappier
post_date: 2015-01-23 07:30:33
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/configuring-centos-send-logs-nagios-log-server/
published: true
dsq_thread_id:
  - "3448240349"
---
Now that Nagios Log Server is installed, it's time to get some log files in there. I got myself all fired up ready to comb through page after page of documentation to figure out how to set it up... then those nice folks over at Nagios did this...

[caption id="attachment_3455" align="aligncenter" width="902"]<a href="http://www.virtxpert.com/wp-content/uploads/2015/01/nagios-log-server-linux-setup.png"><img class=" wp-image-3455" src="http://www.virtxpert.com/wp-content/uploads/2015/01/nagios-log-server-linux-setup.png" alt="Nagios Log Server linux source setup" width="902" height="492" /></a> Nagios Log Server linux source setup[/caption]

That's right, if you click on Linux Source from the home screen, it gives you scripts to download and run to set it all up. They even pulled the IP address from the Nagios Log Server...it was like they wanted you to succeed in making this all work! It can't be that easy right? Let's try!

[caption id="attachment_3456" align="aligncenter" width="600"]<a href="http://www.virtxpert.com/wp-content/uploads/2015/01/linux-source-nagios-log-server-setup-linux.sh-script.png"><img class=" wp-image-3456" src="http://www.virtxpert.com/wp-content/uploads/2015/01/linux-source-nagios-log-server-setup-linux.sh-script.png" alt="Linux Source - Nagios Log Server setup-linux.sh" width="600" height="324" /></a> Linux Source - Nagios Log Server setup-linux.sh[/caption]

That was easy, no way there are actually logs showing up in Nagios Log Server though, right? Almost, SELinux was preventing log files from being shipped as you can see in the middle of the above screenshot. So...
<pre>cp /etc/selinux/config /etc/selinux/config.bak &amp;&amp; sed -i s/SELINUX=enabled/SELINUX=disabled/g /etc/selinux/config &amp;&amp; shutdown now -r</pre>
And BOOM goes the log file goodness after a reboot!

[caption id="attachment_3457" align="aligncenter" width="1228"]<a href="http://www.virtxpert.com/wp-content/uploads/2015/01/remote-linux-source-nagios-log-server.png"><img class=" wp-image-3457" src="http://www.virtxpert.com/wp-content/uploads/2015/01/remote-linux-source-nagios-log-server.png" alt="Remote linux source sending to Nagios Log Server - Dashboard search" width="1228" height="692" /></a> Remote linux source sending to Nagios Log Server - Dashboard search[/caption]

In probably less than 5 minutes, you can have a fully functional Nagios Log Server, based on ELK, deployed and receiving log files from a remote source - that is damn impressive. Of course in this example we haven't looked at which logs we are sending - maybe you only want specific log files being sent from Apache or Ansible for instance, but that is a finer art form that we can save for another blog post. Happy logging!