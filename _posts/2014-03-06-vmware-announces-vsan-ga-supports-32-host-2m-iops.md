---
ID: 2021
post_title: >
  VMware announces VSAN GA, supports 32
  host, up to 2M IOPS
author: Jonathan Frappier
post_date: 2014-03-06 14:37:42
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vmware-announces-vsan-ga-supports-32-host-2m-iops/
published: true
dsq_thread_id:
  - "2374056081"
---
VMware announced Virtual SAN (VSAN / Virtual Storage Area Network) today and I haven't been this excited about a piece of technology since the inception of VMware.  VSAN should drastically reduce the complexity of IT infrastructure for many organizations.  Up until now it was expected that VSAN v1 might only support 8 or 16 hosts but was announced today that you will be able to add 32 hosts to a VSAN cluster (also happens to be the maximum number of hosts in a vSphere 5.5 cluster) with tests delivering up to 2 Million IOPS, though I've not found the test criteria but worst case should certainly be considerably more than what traditional spinning disk SAN/NAS devices will be able to provide.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/03/vsan.png"><img class="aligncenter size-full wp-image-2022" alt="vsan" src="http://www.virtxpert.com/wp-content/uploads/2014/03/vsan.png" width="392" height="295" /></a>

VSAN is built into the hypervisor, so the ability for this to become a very intelligent storage platform is very much limitless.  Even if you do not have 32 hosts today, you can scale performance as you add more nodes, as opposed to many legacy storage systems where adding more shelves can have some negative impact on performance and latency (though generally offset by more drives/IOPS to the naked eye).  VSAN leverages a combination of local flash and spinning disk to enable high performance from from local the local server into a pool of shared storage.  Redundancy is also built in, allowing the VSAN cluster to survive through failed hardware.

After the announcement, <a href="http://www.yellow-bricks.com/2014/03/06/vmware-virtual-san-launch-book-pre-announcement/" target="_blank">Duncan Epping also announced a new book written along with Cormac Horgan on VSAN</a> which could be available by VMworld, and potentially sooner on rough cuts.  Combined they have a lot of great posts available on VSAN as I've not had the opportunity to get this into the lab.  You can find their posts <a href="http://www.yellow-bricks.com/virtual-san/" target="_blank">here </a>(yellow-bricks.com) and <a href="http://cormachogan.com/vsan/" target="_blank">here </a>(cormachorgan.com).

<strong>Summary</strong>

VSAN should be available next week, along with pricing.  If you have a storage project in the works, this should be high on your list.