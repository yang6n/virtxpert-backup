---
ID: 2508
post_title: 'Introducing EMC RecoverPoint for VMs #VMworld #EMCElect'
author: Jonathan Frappier
post_date: 2014-08-26 10:13:11
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/introducing-emc-recoverpoint-vms-vmworld-emcelect/
published: true
dsq_thread_id:
  - "2960753740"
---
How do you handle DR? If you are a storage admin you are likely focused on array, LUN or storage pool replication and ensuring all that data is replicated.  However with so much storage, whether local, DAS, SAN, NAS or VSAN you may not need to replicate an entire LUN or array.  Additionally, what if your mission critical VMs span multiple datastores that reside on different LUNs, as they are likely to do for performance and workload reasons?  Keeping track of where each VM is physically stored would be a manual process if you were replicating at a LUN level - imagine storage DRS migrating a VMDK to a different datastore and you weren't replicating the LUN backing it - you could lose an entire mission critical VM.

Now that virtual machines are "first class citizens" on the array, there is a need to be able to identify and protect at the VM level, not just the the back-end storage.  Today EMC is announcing RecoverPoint for VMs.  The same advanced technology used to protect storage, can now be applied granularly to VMs.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/08/recoverpoint-box.png"><img class="aligncenter size-full wp-image-2509" src="http://www.virtxpert.com/wp-content/uploads/2014/08/recoverpoint-box.png" alt="recoverpoint-box" width="662" height="340" /></a>

&nbsp;

vAdmins may be aware of something like vSphere Replication (if its still called that?), and it is similar to that in that both can replicate specific VMs.  RecoverPoint is designed to be easy to install, and manage.  Once installed, you can make changes to the VM such as adding or removing VMDKs from a VM.  Those changes are automatically updated so there is no need to update replication tools.  Additionally, moving a VM to a new host or using storage vMotion/SDRS to migrate VMDKs to a datastore requires no changes - your VM is still protected.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/08/recoverpoint-vms-install.png"><img class="aligncenter size-large wp-image-2512" src="http://www.virtxpert.com/wp-content/uploads/2014/08/recoverpoint-vms-install-1024x503.png" alt="recoverpoint-vms-install" width="640" height="314" /></a>

RecoverPoint for VMs will be available in October and can (should) be able to be downloaded for you to try.  It is licensed on a per VM basis with a minimum of 15 licenses required.    You can watch a technical overview <a href="https://community.emc.com/videos/12056" target="_blank">here </a>(<a href="https://community.emc.com/videos/12056" target="_blank">https://community.emc.com/videos/12056</a> - note I've not watched as the wifis here in my apartment at VMworld is horrible)