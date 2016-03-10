---
ID: 56
post_title: >
  VMware View Mobile Secure Desktop
  Bootcamp Day 6
author: Jonathan Frappier
post_date: 2012-07-24 00:27:16
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vmware-view-mobile-secure-desktop-bootcamp-day-6/
published: true
jabber_published:
  - "1343089636"
email_notification:
  - "1343089637"
tagazine-media:
  - 'a:7:{s:7:"primary";s:0:"";s:6:"images";a:0:{}s:6:"videos";a:0:{}s:11:"image_count";i:0;s:6:"author";s:7:"7110326";s:7:"blog_id";s:8:"38472741";s:9:"mod_stamp";s:19:"2012-07-24 00:27:16";}'
dsq_thread_id:
  - "1104877141"
---
[youtube http://www.youtube.com/watch?v=P4_Eo80Jf6s]

Sorry for the lack of notes, have setup enough radius servers that it all made sense.  Still a good view though, nice to see PhoneFactor still around!!

&nbsp;

VMware View Mobile Secure Desktop Bootcamp - Day 6

Setting Up Radius 2-Factor Authentication Best Practices

- Intro to radius Auth
- Setup radius
- Config View for radius
- HA for radius
- Troubleshooting

Radius used for AAA, RFC 2865 2866
View 5.1 and newer for 2 factor auth
View user supplies credentials, view connection server talks to Radius

Setup radius
Config view for radius via view admin
- If RSA SecurID, use that instead of radius

If multiple, setup on each connection server - select/existing created for first server

&nbsp;