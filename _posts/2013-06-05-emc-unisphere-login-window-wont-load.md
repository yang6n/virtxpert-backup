---
ID: 1024
post_title: 'EMC Unisphere Login Window Won&#8217;t Load'
author: Jonathan Frappier
post_date: 2013-06-05 12:49:24
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/emc-unisphere-login-window-wont-load/
published: true
dsq_thread_id:
  - "1365096916"
---
Okay so let me start by saying I am a total noob when it comes to EMC best practices, maybe this is normal maybe its not but in the interest of "if it happens to me it could happen to you" I wanted to share.  As I am digging around in my new environment I wanted to look into a few errors I was getting from my Celerra, one problem - the UI would not load.  For all my EMC friends out there, I wouldn't not turn down any sort of best practice guide you may have or can point me to on ECN.  Now its using the default certificates (e.g. not a public/trusted one) which may be my problem (after all I don't know what I don't know yet) and I accepted all the warnings as I launched Unisphere.  What I had to do, maybe you will to, was select the following option:

First, click the 'Show Options' link

<a href="http://www.virtxpert.com/wp-content/uploads/2013/06/showoptions.png"><img class="aligncenter size-full wp-image-1028" alt="showoptions" src="http://www.virtxpert.com/wp-content/uploads/2013/06/showoptions.png" width="480" height="276" /></a>

Second, click the 'Always trust...' check box.

<img class="aligncenter size-full wp-image-1027" alt="checkbox-works" src="http://www.virtxpert.com/wp-content/uploads/2013/06/checkbox-works.png" width="482" height="298" />

<strong>Conclusion</strong>

If you inherited some sort of EMC storage and you can't log in, I hope this helps you out.  I hope to be doing a lot more digging and learning on the storage side so hopefully I can provide some more useful information.