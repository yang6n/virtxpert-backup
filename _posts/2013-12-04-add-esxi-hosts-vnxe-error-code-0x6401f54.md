---
ID: 1598
post_title: 'Cannot add ESXi hosts to VNXe &#8211; Error Code: 0x6401f54'
author: Jonathan Frappier
post_date: 2013-12-04 13:17:59
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/add-esxi-hosts-vnxe-error-code-0x6401f54/
published: true
dsq_thread_id:
  - "2024560353"
---
There is a nifty bug in the VNXe code where after you upgrade a VMware host you are unable to make changes such as editing host access to a datastore or possibly other NFS shares (I'm not messing with my guest NFS shares right now).  If you attempt to make a change you are given the following:  error code: 0x6401f54

<a href="http://www.virtxpert.com/wp-content/uploads/2013/12/vnxeerror.jpg"><img class="aligncenter size-full wp-image-1600" alt="vnxeerror" src="http://www.virtxpert.com/wp-content/uploads/2013/12/vnxeerror.jpg" width="359" height="172" /></a>

This bug is caused by how the VNXe stores the host information.  The work around it so remove the upgraded host or hosts and try adding them back in.  If that works - good for you, if not you will have to remove ALL hosts from the VNXe and add them back in.  This means migrating all necessary VMs off the VNXe to another storage appliance or local storage, or shutting down all the VMs.  This has been around for a while but as the dust has been settled on the ESXi 5.5 release and more people start upgrade projects this may become a bit more of a problem.  You can find an article in the ECN here:  https://community.emc.com/thread/169794

&nbsp;