---
ID: 1101
post_title: 'Infinio &#8211; Improving NAS datastore performance in a few clicks'
author: Jonathan Frappier
post_date: 2013-06-25 07:44:29
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/infinio-improving-nas-datastore-performance-in-a-few-clicks/
published: true
dsq_thread_id:
  - "1431548601"
---
For those that follow me, you have probably heard about <a href="http://www.virtxpert.com/infinio-why-cache-to-disk-when-you-can-cache-to-ram/" target="_blank">Infinio</a> who had their first public demo at Tech Field Day 9, today I finally had the opportunity to get my hands on an early Alpha version of the product.  Before I get to the actual install, a couple of things you should know; first Infinio makes a software appliance to help accelerate read performance of NFS datastores by caching data directly into RAM (read my previous post for a bit more detail).  Second, the people behind the product are very passionate about what they do and want to deliver a truly great customer experience, it seems like such an easy concept but so many companies just don't get it - Infinio gets it.

The install, even for an early Alpha was very smooth.  The installation steps were clear all the way through, the navigation back and forth between steps was flawless, oh and on the technical side it worked exactly as I would have expected.  Before I go on, let me tell you a bit about the lab I installed in.  Its a 2 host "cluster", each host has dual Xeon Dual-Core processors (one 5110 and one 5120) in a cluster with EVC enabled.  Each host has a NIC dedicated for NFS traffic and one for VM, Management and vMotion traffic.  Connected to one host was an NFS datastore and a local datastore, the 2nd host had only a local datastore.

The install prompted for my vCenter connection information as you might expect and was successful in identifying the host with the NFS datastore for which it would accelerate.  It also was able to see both hosts in the cluster and gave me the option to install the management VMs to other datastores (for which it found the local datastores on each host).  Once the wizard finished collecting information, it proceeded though a hands free download and a system configuration.  Once finished, I now had access to the Infinio management interface so I could view the statistics of the Accelerator VM and the performance gains for my environment.  Below is a mock up of what the management interface will look like, and the Alpha has a good head start on getting here.

<a href="http://www.virtxpert.com/wp-content/uploads/2013/06/Image2.jpg" target="_blank"><img class="aligncenter size-full wp-image-1107" alt="Image2thumb" src="http://www.virtxpert.com/wp-content/uploads/2013/06/Image2thumb.jpg" width="534" height="600" /></a>

<strong>Conclusion</strong>

As I mentioned previously, the team at Infinio is very passionate.  If what I am seeing is an Alpha build I am even more excited about the final product.  Their Alpha build install process and early management UI rivals products in production release.  Stayed tuned as a public Beta is expected at VMworld!