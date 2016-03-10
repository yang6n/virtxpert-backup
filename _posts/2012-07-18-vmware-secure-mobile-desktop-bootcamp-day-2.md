---
ID: 33
post_title: >
  VMware Secure Mobile Desktop Bootcamp
  Day 2
author: Jonathan Frappier
post_date: 2012-07-18 01:12:34
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vmware-secure-mobile-desktop-bootcamp-day-2/
published: true
jabber_published:
  - "1342573955"
email_notification:
  - "1342573955"
tagazine-media:
  - 'a:7:{s:7:"primary";s:0:"";s:6:"images";a:0:{}s:6:"videos";a:0:{}s:11:"image_count";s:1:"0";s:6:"author";s:7:"7110326";s:7:"blog_id";s:8:"38472741";s:9:"mod_stamp";s:19:"2012-07-18 01:12:34";}'
dsq_thread_id:
  - "1132995240"
---
[youtube http://www.youtube.com/watch?v=itxnL9W2_oY]

VMware View Bootcamp Mobile Secure Desktop - Day 2

Overview
- Storage Tips and Best Practices
- VDI Storage Challenges
- Understand IO requirments
- Assessments
- Solutions

It's not rocket science...but it might be model rocket science
- Think in terms of performance, not storage (IOPS)
- Size doesnt matter (okay it matters a bit)
- Hard to correct later, PR problem
- Need good user experience, good performance

No one knows average and peak IOPS for desktops, desktops have dedicate spindles
In virtual world, IO is important, must know info

RPM / IOPS
SSD / 6000
15K / 175
10K / 125
7200 / 75
5400 / 50

<!--more-->

Min IOPS
Total IOPS divided by # of desktops (theory worse case scenario)

Max IOPS
Total IOPS for 1 desktop

Average IOPS
IOPS divided by # of desktops over time

Random IO

Linked clones conserves space, more storage than IOPS
- 1.25TB usable space = 300 (60GB/4GB Linked Clone) to 615 (20GB/2GB Linked Clone)
- Plenty of space, not enough IOPS
- Capacity for many, performance for much fewer

How do you figure out? Get usable numbers?
- Rules of thumb
- Calculator
- Assessment

VMware View Planner
myvirtualcloud.net
Lakeside software and LiquidwareLabs to do assessments of physical environment

View Storage Accelerator = cool...enable it
vShield Endpoint instead of standard AV