---
ID: 3205
post_title: Useful yum options I learned this week
author: Jonathan Frappier
post_date: 2014-11-27 08:00:10
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/useful-yum-options-learned-week/
published: true
dsq_thread_id:
  - "3267785099"
---
Always trying to learn new things, that's what it is all about right?  In working with Application Services and Ansible over the last few weeks there are a few things I learned about yum I did not know before.  First, an easy one that will show how much of a linux noob I am, to install multiple packages, I knew I could string commands together with an &amp;&amp; like
<pre>yum install python &amp;&amp; yum install python-setuptools</pre>
But knew there was likely a better way... which is just list each package one after another with no separators.  For example to install Python and Python tools simply run
<pre>yum install python python tools</pre>
You can see here yum went out and searched for both, I already happened to have them on my system in this case but if not the command would have installed them both

[caption id="attachment_3206" align="aligncenter" width="742"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/yum-install.png"><img class="size-full wp-image-3206" src="http://www.virtxpert.com/wp-content/uploads/2014/11/yum-install.png" alt="yum install python python-setuptools" width="742" height="204" /></a> yum install python python-setuptools[/caption]

Another excellent option I learned was using the provides options.  For example something new to me was that in CentOS7 minimal, ifconfig is not inclued; however there is no ifconfig package.  In order to find it I ran
<pre>yum provides ifconfig</pre>
Now that I knew which package I needed, I could simply run
<pre>yum install net-tools</pre>
That's it for now, Do you have any tips using yum beyond the basics of doing an install?