---
ID: 1283
post_title: 'EMC Networker NMC Not Loading &#8211; No Errors'
author: Jonathan Frappier
post_date: 2013-08-09 09:55:56
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/emc-networker-nmc-not-loading-no-errors/
published: true
dsq_thread_id:
  - "1584735138"
---
I ran into an interesting problem recently, my Networker Management Console (NMC) would no longer load (<a href="http://www.virtxpert.com/emc-networker-8-problem-contacting-server-connection-refused-connect/">Yes I did check to make sure this one was registered</a>!).  I would not get any errors (good or bad password) but I would see an error message pop up if I was "logged in" and stopped the related services.  While I think Networker is a slightly over complicated product, it is nice that the NMC is installed and maintained as a separate product.  After consulting with the company that originally did the install (I inherited the product), we elected to simply install the NMC on a different server (their best practice) and get back to work.

What I haven't been able to determine is why the NMC database became corrupt, I had logged in just a few weeks ago to reset the password and it was working then but somewhere along the way we started getting
<pre>E. 08/05 10:18:10. Fatal error: database error</pre>
In /opt/lgtonmc/logs/db_output.log

If you are running into a similar scenario where nothing loads, not even a bad password error, get a SR opened, check your logs and take the normal Java app troubleshooting steps, check your version of Java against your Networker versions compatible Java versions, clear Java cache, temp files etc..., try logging in from a different system.

If you have run into this and found a different solution (EMC support even told me to re-install) or have been able to figure out why it became corrupt in the first place please leave a comment!