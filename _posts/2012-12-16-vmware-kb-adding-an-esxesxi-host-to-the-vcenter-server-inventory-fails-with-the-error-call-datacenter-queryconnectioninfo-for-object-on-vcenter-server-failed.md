---
ID: 290
post_title: 'VMware KB: Adding an ESX/ESXi host to the vCenter Server inventory fails with the error: Call &#8220;datacenter.queryconnectioninfo&#8221; for object on vCenter Server failed'
author: Jonathan Frappier
post_date: 2012-12-16 06:53:40
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vmware-kb-adding-an-esxesxi-host-to-the-vcenter-server-inventory-fails-with-the-error-call-datacenter-queryconnectioninfo-for-object-on-vcenter-server-failed/
published: true
jabber_published:
  - "1355658820"
reddit:
  - 'a:2:{s:5:"count";i:0;s:4:"time";i:1356721221;}'
publicize_twitter_user:
  - jfrappier
email_notification:
  - "1355658822"
dsq_thread_id:
  - "1090702449"
---
I ran into this problem while setting up my lab.  VMware has KB (link below) on this article but wasn't much help for me, though I always start with the KB.  The fix for me (I had two servers doing this) was to either restart the management agent via the DCUI and then add, or add the host via IP address then remove it from vCenter and re-add.  These may not work for you, but since the KB article didn't work for me, maybe this will help.

<a href="http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&amp;cmd=displayKC&amp;externalId=1027672#.UM22EocQZ1Y.wordpress">VMware KB: Adding an ESX/ESXi host to the vCenter Server inventory fails with the error: Call "datacenter.queryconnectioninfo" for object on vCenter Server failed</a>.