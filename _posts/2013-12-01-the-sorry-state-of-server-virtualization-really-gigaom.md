---
ID: 1583
post_title: >
  The sorry state of server
  virtualization? Really @Gigaom?
author: Jonathan Frappier
post_date: 2013-12-01 06:53:23
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/the-sorry-state-of-server-virtualization-really-gigaom/
published: true
dsq_thread_id:
  - "2014483716"
---
Recently Gigaom published an article called <a href="http://gigaom.com/2013/11/30/the-sorry-state-of-server-utilization-and-the-impending-post-hypervisor-era/" target="_blank">The sorry state of server utilization and the impending post-hypervisor era</a>, while I hate sending traffic to such a horribly hit targeted article, I just need to finally call out the writers at Gigaom, a site I used to really enjoy reading... one that I officially stop visiting as a matter of habit starting now.  While at least one of their writers is clearly anti-VMware, as many of her articles are misinformed at best, to put it nicely (to be fair she has had a couple that were conversation worthy) this article suggests that all server virtualization vendors have failed.  And why?  Because of low CPU utilization.

As most of my readers, I think, would agree - the bottle neck in modern x86 server virtualization is not the CPU, its more likely to be storage (of course depending on your workload).  To say that server virtualization is a failure, strictly by pointing to low CPU utilization rates is either a bold acknowledgement that this person should not be writing about virtualization, or a clear play to get hits and stir up controversy....which unfortunately I am playing right into.... DAMN.

The main point of the article, in another fairly clear anti-big-vendor angle, is that Linux containers will be the new breed of server virtualization.  If you are wondering what containers are, head over to <a href="http://blog.scottlowe.org/2013/11/25/a-brief-introduction-to-linux-containers-with-lxc/" target="_blank">Scott Lowe's blog for a great introductory</a> post.  Yes, this technology, if you are a Linux shop (and not everyone should be) is a great piece of technology and to couple this with the enterprise management features from VMware, Citrix, or Microsoft is a great way for IT departments to respond to demand.  But... that container, like its traditional virtual server relatives before it, still needs to read or write data from somewhere, the bottleneck of the entire stack will continue to be storage.

Flash based arrays and the various server side caching vendors such at <a href="http://www.infinio.com/" target="_blank">Infinio </a>and <a href="http://www.pernixdata.com/" target="_blank">PernixData</a> will start to improve the levels of CPU utilization by enabling a higher density of VMs to a single physical host.  In addition, CPU is generally not the main expense when in comes to x86 servers and virtual infrastructure, it's, you guessed it storage!