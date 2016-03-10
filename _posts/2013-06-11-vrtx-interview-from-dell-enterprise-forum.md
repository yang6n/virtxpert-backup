---
ID: 1074
post_title: >
  VRTX Interview from Dell Enterprise
  Forum via @nerdblurt
author: Jonathan Frappier
post_date: 2013-06-11 20:35:39
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vrtx-interview-from-dell-enterprise-forum/
published: true
dsq_thread_id:
  - "1391134947"
---
I'd like to first thank <a href="https://twitter.com/nerdblurt" target="_blank">Luigi Danakos</a>, fellow <a href="http://www.nerdblurt.com" target="_blank">blogger </a>and founder at <a href="http://blurtmediagroup.com/" target="_blank">Blurt Media Group</a> for getting a few questions answered for me direct from Dell while at the Dell Enterprise Forum last week.  For those that may have missed it, Dell released a new product called the <a href="http://www.virtxpert.com/dell-vrtx-game-changer-or-just-another-product-dellef/" target="_blank">VRTX</a> which is a single 5U chassis capable of running up to 4 blades and 25 2.5" drives while running a 110V power.  After the announcement I had a few questions which Luigi got answered for me (click read more for the transcript).

I was very pleased to hear that the 25 drive array can be carved into multiple LUNS and then virtual disks which can then be presented to each blade.  This will allow a "cluster in a box" type scenario with a fully contained unit.  I was a little disappointed to hear that the VRTX is standalone in that you cannot connect two VRTX's together natively, though you could setup a hot/cold scenario with something like vSphere Replication, Veeam or even SRM though that starts to get pricey.  I was hoping to hear how Dell is positioning the product against the like of Nutanix, but the engineer did not have any information on that.  Given the outcome of some of the questions its certainly clear that right now Nutanix is more scaleable given you can create a cluster from multiple units where as the VRTX is standalone (If anyone from Dell or Nutanix would like to comment, feel free to do so below and I will update as more information is available).

<strong>Conclusion</strong>

This is certainly shaping up to be an interesting product for the SMB space or for large enterprises needing isolated infrastructure at branch offices.  I look forward to being able to get more pricing on these units.

<!--more-->

Transcript from recorded interview:
<blockquote><em>Luigi:  We're here asking questions VRTX for vExpert Jon Frappier</em>

<em>Luigi:  How is this different than the C series servers?</em>

<em>Dell:  The C series servers don't have a shared storage option on them currently.  In this case the integrated storage array thats in VRTX can be shared between the 4 sever blades that are in the box.  It's shared using PCI Express and a standard PERC RAID adapter.</em>

<em>Luigi:  Next question how do you compare to Nutanix.  The engineer was not aware of Nutanix so this question was skipped</em>

<em>Luigi:  Are all the disks shared among all 4 servers.</em>

<em>Dell:  The disk can be shared or unshared, its a full configurable option essentially what happens is you create your raid sets through the chassis management controller and then once you created a raid set you can carve that raid set up into virtual disks.  Once you have a virtual disk, you can assign a virtual disk to a server blade or share it between multiple server blades so you can have virtual disks that are dedicated to a server blade or shared between 2, 3 or 4 of them, its fully configurable.</em>

<em>The only drives that are dedicated are the two drives that are local to the blades themselves, so those are local and cannot be shared.  The 25 drive array that is in the chassis can be fully shared.</em>

<em>Luigi:  Can I connect multiple VRTX's together, the answer is no, its not clusterable at this time.</em>

<em>Luigi:  What happens if a host is pulled out.</em>

<em>Dell:  The RAID Array will see what we call a surprise removal on the PCI bus.  It will reset but come back online in 15 to 30 seconds.  The OS will not time out, the timeout on the OS side is much longer.  So you will see a hiccup in service but will come back online.</em></blockquote>