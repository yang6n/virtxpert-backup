---
ID: 23
post_title: >
  Why you should use VMWare even with one
  server
author: Jonathan Frappier
post_date: 2012-07-16 23:47:55
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/why-you-should-use-vmware-with-as-few-as-one-server/
published: true
jabber_published:
  - "1342482477"
tagazine-media:
  - 'a:7:{s:7:"primary";s:0:"";s:6:"images";a:0:{}s:6:"videos";a:0:{}s:11:"image_count";s:1:"0";s:6:"author";s:7:"7110326";s:7:"blog_id";s:8:"38472741";s:9:"mod_stamp";s:19:"2012-07-17 12:02:26";}'
dsq_thread_id:
  - "1210082351"
---
So you’re a small to medium size business, and after carefully consulting with your IT team (or me!) its been decided that you need a server – maybe its your first, maybe a replacement but in any case you only have this 1 single server.  Before you start installing or preparing Windows on this server here are a few reasons why you should consider installing VMWare ESXi first.

Most IT departments think of VMWare as a solution for having multiple “virtual” machines (or VMs) on a single physical tower or rackmount server but there are many useful features of VMWare that will give you more flexability that Windows on a bare metal server.  I did this once for a company who was replacing their Microsoft Dynamics CRM system.  They had an “admin” who thought he was a developer and would constantly break the server, which I then had to rescue.  When we upgraded I put it on the free version of VMWare ESXi and took snapshots from time to time and even got the admin to tell me when he was making changes – I was able to revert several, possibly unrecoverable servers within minutes thanks to the items below:

1.  Snapshots – even if you don’t buy into any of the other reasons, snapshots alone should be reason enough.  A snapshot allows you to take a quick, point in time image of your VM (either powered on or off, when possible I turn my server off before taking a snapshot).  Anytime I patch or make a major change to one of my VMs I take a snapshot first, if something goes wrong I can revert back to the snapshot in a matter of minutes – no software to re-install, no files to restore and minimal downtime.

2. Monitor – VMWare has some very acceptable monitoring tools, chances are if you are a small business or have only a single server you probably haven’t invested in monitoring software for that server – the monitoring feature in the free version of VMWare (ESXi) is built in, just needs to be configured.

3.  Growth – If you have 1 server, you will probably need two eventually (in fact I would argue that if you have one you should have a second for redundancy for whatever that application is).  Having the free version of VMWare ESXi gives you the ability to add a 2nd or 3rd server and only have to buy the necessary Windows/OS license and CALs without having to invest in new, additional hardware.  If your growth continues, you can add a SAN, second physical server and full VMWare license to gain even more features and functionality.