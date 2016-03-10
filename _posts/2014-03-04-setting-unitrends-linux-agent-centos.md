---
ID: 2005
post_title: >
  Setting up the Unitrends Linux agent on
  CentOS
author: Jonathan Frappier
post_date: 2014-03-04 09:58:22
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/setting-unitrends-linux-agent-centos/
published: true
dsq_thread_id:
  - "2358238451"
---
A real quick how-to for setting up the Unitrends linux agent on your system.  First, ensure your Unitrends appliance is up to date, the most recent agents require version 6.2 or higher (currently 7.3).  Once you have confirmed your Unitrends system is up to date, verify whether you are using IPTables on your Linux server(s) and make note.

First install the prerequisites if necessary
<pre>sudo yum install samba-client or sudo yum install samba3x-client
sudo yum install xinetd</pre>
Download the Unitrends agent
<pre>wget http://ftp.unitrends.com/bp/latest_build/Linux/lnx32_cnt.run</pre>
Run the agent install
<pre>sh ./lnx32_cnt.run</pre>
If you are running IPTables answer yes when prompted, though you still have to manually edit your server and then
<pre>sudo vi /etc/sysconfig/iptables</pre>
Add
<pre>iptables -A INPUT -p tcp --dport 1743 -s ip.of.unitrends.server -j ACCEPT
iptables -A INPUT -p tcp --dport 1745 -s ip.of.unitrends.server -j ACCEPT</pre>
Edit the Unitrends agent configuration file
<pre>sudo vi /usr/bp/bpinit/master.ini</pre>
And change the data port from 1744 to 1745.

You should now be able to add the Unitrends Linux clients in your Unitrends Recovery Console