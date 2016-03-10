---
ID: 1260
post_title: >
  How to reset the administrator password
  for EMC Networker
author: Jonathan Frappier
post_date: 2013-08-02 10:11:49
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/how-to-reset-the-administrator-password-for-emc-networker/
published: true
dsq_thread_id:
  - "1561696091"
---
If you ever find yourself without the administrator password for EMC Networker, you can use the steps below to reset the password to the default so you can log in.  This is also in support.emc.com, but I have a bit of trouble with the re-directs they do to SalesForce.com from time to time.
<ul>
	<li>For a Linux OS, start a terminal session (hopefully you at least have that, maybe thats another blog post I should write)</li>
	<li>If you did not log in as root (and hopefully you didn't) type sudo -i to elevate your priviliges</li>
	<li>Type the following</li>
</ul>
<pre>export GST_RESET_PW=1</pre>
<ul>
	<li>Stop and start the GST services by typing</li>
</ul>
<pre>/etc/init.d/gst stop
/etc/init.d/gst start</pre>
<ul>
	<li>Launch the mangement console</li>
	<li>You should now be able to log in with the username administrator and default password of administrator</li>
	<li>Change the password</li>
	<li>Go back to your SSH session and type</li>
</ul>
<pre>export GST_RESET_PW</pre>
Hopefully that gets you logged in!  If your install is on Windows, check out this blog post:  <a href="http://geek-digest.blogspot.com/2013/03/how-to-reset-administrator-password-for.html">http://geek-digest.blogspot.com/2013/03/how-to-reset-administrator-password-for.html</a>