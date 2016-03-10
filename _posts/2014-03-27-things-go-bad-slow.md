---
ID: 2104
post_title: When things go bad, slow down
author: Jonathan Frappier
post_date: 2014-03-27 14:55:19
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/things-go-bad-slow/
published: true
dsq_thread_id:
  - "2526303737"
---
Read an interesting blog post this morning about problems that traced back to some configuration problems, in talking with the blogger it very much boiled down to a bit of pressure and time crunch and missing something which caused problem.  This afternoon I've run into a problem and had to remind myself sometimes you just need to slow down.  In my particular case, it was a clean vCenter Server Appliance deployment but the AD join portion of the wizard failed.  As I was trying to fly through the install steps I didn't wait for the new service account I setup to replicate to the local DC.  After troubleshooting a few other problems I decided it was quicker to just put the VM out of its misery and start from scratch...cattles, nachos, whatever you like to call it but the VM meant nothing to me.  Now, trying to rush to get it done I started making some foolish errors having felt like I just wasted some time, putting the default gateway into the NETMASK field in the ifcfg-eth0 file, troubleshooting routing issues when I hadn't added the default gateway yet.

I had to remember that sometimes it is better, regardless of whatever deadline to just stop, take a deep breath, slow down and go back to your deployment checklists and make sure you are ticking all your boxes.  In the long run, that will take LESS time that troubleshooting silly errors that I was causing!
<p style="text-align: center;"><a href="http://www.virtxpert.com/wp-content/uploads/2014/03/slow.gif"><img class="aligncenter  wp-image-2105" alt="slow" src="http://www.virtxpert.com/wp-content/uploads/2014/03/slow.gif" width="320" height="320" /></a></p>