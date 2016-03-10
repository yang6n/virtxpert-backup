---
ID: 45
post_title: VMware View Mobile Secure Desktop Day 5
author: Jonathan Frappier
post_date: 2012-07-21 00:56:49
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vmware-view-mobile-secure-desktop-day-5/
published: true
jabber_published:
  - "1342832211"
email_notification:
  - "1342832212"
tagazine-media:
  - 'a:7:{s:7:"primary";s:0:"";s:6:"images";a:0:{}s:6:"videos";a:0:{}s:11:"image_count";s:1:"0";s:6:"author";s:7:"7110326";s:7:"blog_id";s:8:"38472741";s:9:"mod_stamp";s:19:"2012-07-21 00:56:49";}'
dsq_thread_id:
  - "1133082252"
---
[youtube http://www.youtube.com/watch?v=85DUsg6LcIU]

Day 5 - VMware View Mobile Secure Desktop

TrendMicro - Agentless AV

Zero footprint, agentless via VMware API

VMware vSheild end point on ESX
Trend Micro Deep Security installed, integrated with vCenter, drivers installed, Virtual appliance deployed

Profile based
- Settings/features

Mobile Secure Desktop Profiles:
- Knowledge Worker
- Power User
- KW - Traveling
Diff VMs in diff folders

<!--more-->

Automatic Profile Assignment
- Computer created task
- Assign profile
- Activate after x minutes
- Conditions

Quarantine on DSVA, not VM
No user feedback
Consider deploying deep security notifier in Master VM
- User warning balloon tips
- Config overview
- Event viewer
- VMCI needs to be enabled on guest and dsva, settings on master image

Web Reputation prevents malware from getting onto vm
- Low, medium, high, paranoid

Virtual shielding, virtual patching
- Create VM from master, install agent, run rec scan, select dpi rules, repeat for new master

File integrity monitoring
- Software updates master only
- Every system change is 'suspicious'