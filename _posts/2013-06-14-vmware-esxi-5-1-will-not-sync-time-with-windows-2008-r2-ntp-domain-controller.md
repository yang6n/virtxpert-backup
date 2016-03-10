---
ID: 1077
post_title: >
  VMware ESXi 5.1 will not sync time with
  Windows 2008 R2 NTP Domain Controller
author: Jonathan Frappier
post_date: 2013-06-14 14:04:16
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vmware-esxi-5-1-will-not-sync-time-with-windows-2008-r2-ntp-domain-controller/
published: true
dsq_thread_id:
  - "1401366282"
---
I ran into a problem yesterday that I know I have never had before, which now makes me wonder about my last couple of vSphere installs.  I was building a new cluster, set my first ESXi server up and built my first Domain Controller, configured it to sync with pool.ntp.org servers and set my host to sync with it.  Done right?  No not in this case.   Since checking the KB is always my first stop, I found <a href="http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&amp;cmd=displayKC&amp;externalId=1035833" target="_blank">KB1035833</a> which pointed me to two configuration files I had to edit manually (e.g. via SSH not the vSphere Client).

First, make sure this is actually the problem you are having.  Make sure your Windows firewall and ESXi firewall are set to allow UDP123.  There is also a handy little utility to check if everything is setup correctly that you can download <a href="http://bchavez.bitarmory.com/archive/2009/12/21/how-to-setup-a-windows-2008-r2-sntp-ntp-server.aspx" target="_blank">here</a>.  Now if all seems correct, start SSH on your ESXi host if you have not already done so by doing the following:
<ul>
	<li>Go to Security Profile and click Properties.</li>
	<li>On the top right corner (in the services section) click Properties...</li>
	<li>Find and click on SSH and click the Options button and click the Start button.</li>
	<li>Open PuTTY or your preferred terminal client and connect to your host.</li>
	<li>Accept the certificate and type the following commands to make a copy and edit your ntp.conf file:</li>
</ul>
<code> cp /etc/ntp.conf /etc/ntp.conf.bak
vi /etc/ntp.conf
</code>
<ul>
	<li><span style="line-height: 13px;">Using the arrow keys, position the cursor at the end of the last line and hit i on your keyboard.  This will place you in edit mode in VI.</span></li>
	<li>Enter a new line and type tos maxdist 30</li>
	<li>Hit ESC on your keyboard to come out of edit mode then type a : and press X to save and exit.</li>
	<li>Now type the following to edit the lsassd.conf file:</li>
</ul>
<code> cp /etc/likewise/lsassd.conf /etc/likewise/lsassd.conf.bak
chmod +w /etc/likewise/lsassd.conf
vi /etc/likewise/lsassd.conf
<code></code></code>
<ul>
	<li><span style="line-height: 13px;">Using the arrow keys, find  #sync-system-time</span></li>
	<li>Position your cursor on the s of sync, hit i, hit the backspace button to delete the #</li>
	<li>Hit ESC</li>
	<li>Hit ESC on your keyboard to come out of edit mode then type a : and press X to save and exit.</li>
	<li>Type the following command</li>
</ul>
<code>/sbin/auto-backup.sh</code>
<ul>
	<li><span style="line-height: 13px;">This will ensure all changes persist after a restart.</span></li>
	<li>Now at this point the time on my host updated though for good measure restart the two services</li>
</ul>
<code> ./etc/init.d/lsassd restart
./etc/init.d/ntpd restart
</code>

Finally, I would stop the SSH service until the next time you need it, or if you security policies allow make sure its set to start automatically.

<strong>Conclusion</strong>

I know I have never had to do this before, this isn't an extra check box.  I will certainly be going back to check my other hosts but I know this has worked without these additional changes before.  Hope this helped if you are having problems!