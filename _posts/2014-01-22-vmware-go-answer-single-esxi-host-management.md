---
ID: 1889
post_title: >
  Could VMware Go be the answer to single
  ESXi host management?
author: Jonathan Frappier
post_date: 2014-01-22 14:11:29
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vmware-go-answer-single-esxi-host-management/
published: true
dsq_thread_id:
  - "2159722735"
---
A while back, VMware killed off a product they had been offering for free called VMware Go which allowed you to <a href="http://www.virtxpert.com/cloud-management-of-vmware-hosts-using-vmware-go-for-new-admins-and-smbs/" target="_blank">manage stand alone ESXi</a> hosts through a web interface, in the case of Go it was offered as a SaaS service.  Fast forward to VMworld, ESXi 5.5 and VM hardware version 10 and the battle between needing the C# client and using the web client.  VMware states that the web client is the future, but how can you build that first ESXi host and start importing VM's without a way to manage it (I wont go into the whole managing VMs with HW v10 problem now).

While a valid option would be installing vCenter on dedicated hardware, that flies in the face of virtualization and the recent trend of VMware pushing appliances, such as the vSphere 5.5. appliance (VCSA) which is deployed as an OVA.  Others have suggested maybe vCenter will be setup such that it can manage an unlicensed host - but if the C# client is really going away, then how would we get that first VM on our ESXi host to set that up?

Could what once existed as VMware Go end up being embedded into ESXi for single host management come ESXi 6?  Thinking through it logically, VMware offered it as a SaaS service, learned about how it was and cloud be used then pulled the plug.  I certainly liked the VMware Go interface, it was simple to use and provided several "best practice" checks out of the box, so VMware - how bout it?