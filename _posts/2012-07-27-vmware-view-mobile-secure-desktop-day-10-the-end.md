---
ID: 65
post_title: 'VMware View Mobile Secure Desktop &#8211; Day 10 &#8211; The End&#8230;.'
author: Jonathan Frappier
post_date: 2012-07-27 16:10:32
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vmware-view-mobile-secure-desktop-day-10-the-end/
published: true
jabber_published:
  - "1343405434"
email_notification:
  - "1343405437"
dsq_thread_id:
  - "1231951038"
---
Not really the end, time to implement!

[youtube http://www.youtube.com/watch?v=PoO8iLPF22w]

VMware View Mobile Secure Desktop - Day 10

Install and Config of vCenter Ops Manager for View

'vCOps'

Capacity mgmt, monitoring ensuring end user experience

Based on VCOps Manager 5, optimized for View
vCOps for view is stand alone

Reactive problem solving &amp; Proactive monitoring
- Monitor, isolate, remediate problems
- Plan, optimize, automate maintenace

Solves slow view deployments, move form pilot to prod.

Requirements<!--more-->

Single instance of vCOps for view v1
- vcenter ops manager vapp
- view adapter on windows server
- support max 2000 remote view desktop sessions
- single vcops can monitor single view
- up to 1000 desktops - dual core
- up to 2000 desktops - quad core
- DRS cluster
- Local admin on all desktops
- Remote registry and wmi started
- Create IP pools

See install walk through in video