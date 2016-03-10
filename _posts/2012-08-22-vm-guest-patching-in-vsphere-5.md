---
ID: 113
post_title: VM Guest Patching in vSphere 5
author: Jonathan Frappier
post_date: 2012-08-22 12:48:10
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vm-guest-patching-in-vsphere-5/
published: true
jabber_published:
  - "1345639691"
email_notification:
  - "1345639692"
reddit:
  - 'a:2:{s:5:"count";i:0;s:4:"time";i:1353239324;}'
dsq_thread_id:
  - "1115881261"
---
I knew it was coming, it just fell off my radar.  VMware's acquisition of Shavlik has turned into vCenter Protect Essentials Plus.  With the ability to patch VM guests from Update Manager gone, this is the integrated solution available to VMware customers.  Like the license changes for vSphere however, this now comes at an additional cost - though not horrible.  For 50 protected servers (physical or virtual) you are only in for an additional $2650 per year($53 x 50) for a centralized patch management, anti-virus, configuration management and scripting solution.  vCenter Protect Essentials Plus can also patch offline VMs and templates ensuring new VMs are already up to date when deployed from an existing template or offline VM.  There is also a standard version which does not include AV, scripting or config management for $35/protected machine.  Is anyone using vCenter Protect Essentials Plus - if so how do you like it and is it worth money you are being charged?