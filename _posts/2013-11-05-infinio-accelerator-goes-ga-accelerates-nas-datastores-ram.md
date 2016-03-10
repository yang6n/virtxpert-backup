---
ID: 1488
post_title: 'Infinio Accelerator goes GA &#8211; accelerates your NAS datastores in RAM'
author: Jonathan Frappier
post_date: 2013-11-05 09:01:26
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/infinio-accelerator-goes-ga-accelerates-nas-datastores-ram/
published: true
dsq_thread_id:
  - "1938516509"
---
Infinio, who came out of hiding at Tech Field Day 9, announced today that they have come out of Beta and are fully GA with their Infinio Accelerator product.  For those unaware, Infinio provides a downloadable appliance which provides a distributed read cache directly in RAM.  All of this can be achieved with ZERO downtime, no migrating VMs, no maintenance mode for you host - just download and go!  Infinio has assembled a great team, and I feel fortunate that I have had the opportunity to meet and work with them during the alpha stage of their product.  I was first introduced to Infinio back in March/April, tt was hard to sit on talking about such a cool product for so long!

Version 1 of Infinio Accelerator works with NFS for VMware vSphere environments, for me their product moves me away from iSCSI to NFS (though they are working to support iSCSI in a future release...am I allowed to say that?  Oh well I did).  Once installed you can start to free IO from your NAS and storage network and deliver  reads directly from RAM, much faster than even SSD can deliver today.

You can learn more about Infinio on their website, <a href="http://www.infinio.com/" target="_blank">www.infinio.com</a> or their various social channels which they are very active on.  There is a great interactive page <a href="http://www.infinio.com/about-our-product/how-does-it-work" target="_blank">here </a>that helps you understand how it works.

<a href="http://www.virtxpert.com/wp-content/uploads/2013/11/infinio.png"><img class="aligncenter size-full wp-image-1493" alt="infinio" src="http://www.virtxpert.com/wp-content/uploads/2013/11/infinio.png" width="714" height="395" /></a>

Here is a "How it Works" video since you are already here!

<iframe src="//www.youtube.com/embed/Hce_LuxnLYY" height="315" width="420" allowfullscreen="" frameborder="0"></iframe>