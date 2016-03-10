---
ID: 2514
post_title: 'VMworld Day 1 &#8211; EVO:Rail and lots of vCloud Air'
author: Jonathan Frappier
post_date: 2014-08-26 10:54:02
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vmworld-day-1-evorail-lots-vcloud-air/
published: true
dsq_thread_id:
  - "2960868826"
---
<a href="http://www.virtxpert.com/wp-content/uploads/2014/08/evo-rail.jpg"><img class="alignleft  wp-image-2515" src="http://www.virtxpert.com/wp-content/uploads/2014/08/evo-rail.jpg" alt="evo-rail" width="243" height="225" /></a>Day 1 of VMworld, also my very first live VMworld brought some exciting announcements.  These announcements weren't your typical major vSphere release type announcements, these were much more strategic and for me actually pretty exciting (an hour keynote about 64 node clusters or super-duper-extreme-vMotion would have been a bit of a yawn fest, I expect enhancements like that now).  EVO:Rail and EVO:Rack were the two that were most exciting to me.  EVO:Rail is a solution for VMware partners to deliver hyper-converged infrastructure to their customers.  The boast here is customers will be able to go from zero to working environment in 15 minutes.

Each EVO:Rail hyper converged infrastructure appliance, or HCIA, will consist (at a minimum) of 4 compute nodes with a total of 192GB of RAM (48GB each), 3x 1TB+ 10K SAS drives, 400GB+ enterprise grade SSD and a certified disk controller (<a href="http://blogs.vmware.com/vsphere/2014/07/update-virtual-hardware-compatibility-guide.html">which VMware just updated the list of to ensure performance</a>) and 10Gbps networking.  A typical HCIA is expected to support +/- 100 VMs (based of course on your workload).

<a href="http://www.virtxpert.com/wp-content/uploads/2014/08/evo-rail-concept.png"><img class="aligncenter  wp-image-2517" src="http://www.virtxpert.com/wp-content/uploads/2014/08/evo-rail-concept.png" alt="evo-rail-concept" width="253" height="331" /></a>

&nbsp;

EMC is one of the first EVO:Rail partners (I will be trying to get hands on with one ASAP) along with Dell, SuperMicro, Fujitsu, Inspur, and NetOne.  As you can see above, under the covers this is a HCIA with vSphere and VSAN.  As of today, NSX is NOT included in this configuration (I need to find out if vCNS is or if it is typical virtual switches). EVO:Rail, unlike last  years VSAN announcement, was targeted at partners to enable them to deliver solutions rather than put the burden of installation and configuration on the customer.  I heard a few comments during the keynote along the lines of "there goes my job" but, while simple to deploy, EVO:Rail still needs to be supported and delivered to the customer based on their needs.

I didn't write about EVO:Rail intentionally yesterday as I wanted to really think about this and determine if I was excited because it was new, or excited because I think it will be a great solution - I am definitley excited because it is a great solution.  Chad Sakacc has an amazing write up <a href="http://virtualgeek.typepad.com/virtual_geek/2014/08/vmworld-2014-evorail-and-emcs-approach.html" target="_blank">here</a>.

Also announced was a rebranded <a href="http://www.vmware.com/products/vrealize-suite/" target="_blank">suite of products called vRealize</a> (I realize I'm not good at marketing but man what a horrible name, sorry but it is) that is available as a SaaS based offerings under the <a href="http://www.vmware.com/company/news/releases/vmw-newsfeed/VMware-Introduces-the-VMware-vCloud-Air-Network/1872190" target="_blank">recently announced vCloud</a> Air product line (formerly vCHS).  Most notable in my opinion is vCloud Automation Center, now called vRealize Automation for on-premises installs or VMware vRealize Air Automation (at least we don't have to argue over vCake, vKack, or vSee-A-See anymore).  The SaaS based offering is a somewhat new avenue for VMware.  They had a service called VMware Go but that was cattled a couple of years ago and they still have SocialCast and should be a nice offering for customers that do not have the staff to support onsite vCAC.

All these announcements, however can't match how amazing it has been to meet so many people in the VMware community, people who have become friends and people I look up to all over social media.  Last night several of us (Jon Harris, Anthony Hook and Gregg Robertson) took in a game at AT&amp;T park.  This, for me is the best part of VMworld.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/08/vmworld-baseball.jpg"><img class="aligncenter  wp-image-2519" src="http://www.virtxpert.com/wp-content/uploads/2014/08/vmworld-baseball.jpg" alt="vmworld-baseball" width="795" height="596" /></a>