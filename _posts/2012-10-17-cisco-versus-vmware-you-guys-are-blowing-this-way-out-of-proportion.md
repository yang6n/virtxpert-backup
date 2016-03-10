---
ID: 177
post_title: 'Cisco versus VMware &#8211; you guys are blowing this way out of proportion'
author: Jonathan Frappier
post_date: 2012-10-17 00:26:09
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/cisco-versus-vmware-you-guys-are-blowing-this-way-out-of-proportion/
published: true
jabber_published:
  - "1350433570"
email_notification:
  - "1350433572"
reddit:
  - 'a:2:{s:5:"count";i:0;s:4:"time";i:1357795496;}'
dsq_thread_id:
  - "1159957777"
---
There is 1.05 billion reasons why there are so many blog posts about this supposed battle, struggle, whatever you want to call it between Cisco and VMware ever since VMware's acquisition of Nicera.  While I am sure there is some insider knowledge coming out in these blog posts, lets look at it from a calm, unbiased position.

Cisco and VMware are two separate companies, except from the perspective of their joint venture - VCE.  I am going to ignore VCE for the moment because the partnership still makes sense on so many levels, and what IT person wouldn't kill for a vBlock of any size in their data center.  What VMware does with the technology acquired from Nicera will go a long way towards proving my point, or blowing it up.  Before the acquisition VMware still produced virtual switching software in the form of Virtual Standard Switches (VSS) and a Virtual Distributed Switch (VDS) that companies could, and do use.  Leveraging the Cisco Nexus 1000v was always an add on to VMware so if Nicera is simply used as an upgrade to the features and functionality in the native VMware VDS nothing changes.  If VMware makes/keeps Nicera as an add-on, some might say direct competition to the Nexus 1000v nothing changes.  Now before you skip to the end and rip me for that last sentence hear me out... who is using the Nexus 1000v?  My SWAG - companies who are heavily invested in Cisco network infrastructure.  Those companies will still have a major investment in physical Cisco infrastructure which does NOT get replaced by virtual switches.  Sure virtualization might be hurting the ToR (Top of Rack) switch market like the Nexus 2000 FEX's or lower end switches like the 2900 or 3700 series but that is likely not a ton of revenue for Cisco anyway - yes its still lost revenue but it was lost with virtualization anyways and I suspect being made up nicely by Cisco UCS server/blade/accessory and licensing sales.  Now back to my original point, if you are a Cisco shop anyways are you really considering Nicera as a replacement for the 1000v?  My bet is no, at least not enough to make a difference at a few hundred dollars per socket.

Second point - Cisco and VMware have ALWAYS had to be platform/partner agnostic.  VMware was never going to shut out compatibility with HP, IBM or other brand servers just as Cisco, at least on the sever side was never going to shut out other hypervisors or operating systems such as OpenStack, Hyper-V, Xen, Windows, and *nix or even break compatibility with IEEE standards on the routing/switching side regardless of what was going on at VCE.  VMware would continue to work with other server vendors, even other storage vendors.  Do you see VMware (read EMC) blocking/breaking compatibility with HP, NetApp or other storage vendors?  No they are increasing the opportunities for new storage vendors to enter the market and build compatibility with VMware.  EMC and Vmware are also making it easier for server vendors to work with them in the form of VSPEX/reference architectures   Cisco's release of an official OpenStack implementation is nothing more than supporting a rising platform in the cloud computing space.  Cisco supports Hyper-V and XEN, so why is it that OpenStack is any more of a challenge than Cisco's public support of other hypervisors?  Did someone at Cisco get a kick out of thumbing their nose at someone from VMware they don't like working with...yea probably but its not going to change the fact that VCE is a great partnership for all parties involved.  vBlock is the best of breed, unified data center technology with a single support vendor, single purchase vendor, and single maintenance renewal vendor.