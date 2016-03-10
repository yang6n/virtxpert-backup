---
ID: 2012
post_title: >
  Infinio launches version 1.2, supports
  ESXi 5.5 @InfinioSystems
author: Jonathan Frappier
post_date: 2014-03-03 09:01:26
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/infinio-launches-version-1-2-supports-esxi-5-5-infiniosystems/
published: true
dsq_thread_id:
  - "2351431682"
---
<em>Disclaimer:  Infinio is a sponsor of virtxpert.com and notified me of the upcoming release.  This post has not been reviewed or altered in any way by Infinio and is strictly my opinion.</em>

Today Infinio (<a href="http://twitter.com/infiniosystems">@InfinioSystems</a>) announced version 1.2 of Infinio Accelerator, adding official support for vSphere / ESXi 5.5.  If you haven't heard of Infinio, they make a software only read caching system to help improve the performance of your Network Attached Storage (NAS) systems.   While there are many caching solutions available today, Infinio serves the NAS / NFS market with a no hardware solution; there is no PCI or SSD flash that you need to purchase and install.  The Infinio Accelerator creates a de-duplicated read cache across all active servers directly in memory.  The product installs a management VM and an one Accelerator VM per host (as seen below) very simply and with no down time.  The Accelerator VM needs just 8GB of memory from your ESXi host and quickly start handling read requests for cached data directly from RAM.

<a href="http://www.virtxpert.com/wp-content/uploads/2013/11/infinio.png"><img class="aligncenter size-full wp-image-1493" alt="infinio" src="http://www.virtxpert.com/wp-content/uploads/2013/11/infinio.png" width="714" height="395" /></a>

You can see here, <a href="http://blog.infinio.com/bid/371475/Content-based-caching-video-series" target="_blank">in this video from Vishal Misra</a> that by reducing just a small chunk of requests from an oversubscribed NAS you can drastically improve performance.

With news of the 1.2 release, Infinio is also offering a limited number of free lab use licenses.  You can register for the lab license at <a href="http://info.infinio.com/ssd-class-performance-without-ssds-PR" target="_blank">http://info.infinio.com/ssd-class-performance-without-ssds-PR</a>

<strong>Summary</strong>

If you use NAS/NFS based solutions for presenting shared storage to your vSphere environment I would highly recommend checking them out and putting their product to the test against other solutions.  I was excited to meet with Infinio last winter before their official launch and am excited about their continued growth as a product and team.