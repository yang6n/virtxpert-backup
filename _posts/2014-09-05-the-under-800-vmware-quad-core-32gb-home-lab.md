---
ID: 2553
post_title: >
  The Under $800 VMware Quad-Core 32GB
  Home Lab
author: Jonathan Frappier
post_date: 2014-09-05 21:20:33
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/the-under-800-vmware-quad-core-32gb-home-lab/
published: true
dsq_thread_id:
  - "2992332302"
---
Because I am a geek, and my needs change, and this is what I like to do I often check out new hardware, cost features etc.  One of the things I wish I did on my <a title="8-Core, 32GB RAM, 360GB Flash, 3TB, Dual-NIC Home Lab Part List" href="http://www.virtxpert.com/8-core-32gb-ram-360gb-flash-2tb-dual-nic-home-lab-part-list/">8-core lab</a> was go for a smaller form factor case.  Pricing, as always is subject to change.  I actually prefer to buy most of my hardware on Amazon because I seem to have an easier time returning items that are defective but I'll link to NewEgg.  You may be able to find a part or two for a bit less somewhere else which is always good.

Here is a run down on the parts for this VMware home lab build which should be capable of booting nested 64-bit VMs or as a stand alone ESXi host running other VMs since it is cheap (you can get almost 2 of these for the price of my 8-core build).  My goal was a slim line case, the In Win case comes equipped with a power supply and 2x internal 3.5" drive bays.  The 2x drive bays gives you the option to add 2x of the ICY drive caddys so you can mount a total of 4 drives inside this small form factor case.  In this build I opted for a single SSD and HDDs so if you build several of these you could do a VSAN lab.  Originally I had 3x HDDs in here so if you go the nested build route you can use the on-board RAID controller to configure the 3x HDDs in a RAID-0 for a total of about 1.5TB of usable datastore space stripped across the 3 drives an single SSD datastore (think "gold" and "bronze" tier - OS's on the SSD and everything else on the HDDs?).  Of course the drive configurations are just an example, I went with a single drive here for cost reasons.  You could also drop the drives all together if you were using a NAS/SAN in your home lab and just boot via USB.  The on-board NIC will need drivers, however best I can tell the Siig 2-port card uses an Intel i350 chipset which appears to be on the HCL.  You could also go with a used <a href="http://www.amazon.com/HP-NC7170-network-adapter-383738-B21/dp/B0009MWAI4" target="_blank">HP NC7170</a> as I did in my original build and drop almost $70 of the price via Amazon (http://www.amazon.com/HP-NC7170-network-adapter-383738-B21/dp/B0009MWAI4) to get a working lab setup under $750, in fact you can get down almost to $700 if you drop the drive caddys as well!  One caveat with the used NICs, they may not come with the low profile face plate, so that may send you on a bit of a hunt to find one.  According the Siig site, those NICs ship with the low profile face plate.

For the CPU I went cheapest quad-core available that is 64-bit with virtualization support with RVI - the Athlon X4 740 Trinity CPU with 2x 16GB RAM kits (each kit containing 2x 8GB memory modules) to finish out the build.  <a href="http://goo.gl/jPkUMC" target="_blank">According to AMD</a>, all Trinity series processors have the VT/RVI feature to allow you to boot 64-bit VMs in a nested hypervisor (http://goo.gl/jPkUMC) I'll assume you will boot from USB, and that you have plenty of them from conferences past to keep my price under $800 :)

[ultimatetables 7 /]