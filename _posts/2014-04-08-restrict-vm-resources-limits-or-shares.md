---
ID: 2144
post_title: 'Restrict VM resources &#8211; Limits or Shares'
author: Jonathan Frappier
post_date: 2014-04-08 16:33:41
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/restrict-vm-resources-limits-or-shares/
published: true
dsq_thread_id:
  - "2596962063"
---
A question came across Twitter today about how to limit the amount of IOPS available to any one VM.  This can be useful with VMs that are not imported, say test/dev that may share a common datastore with other, more important VMs.  Here are a few thought on how to do this.

My preferred method would be to isolate the VMs to a dedicated datastore, after all if these VMs are not that important to you I would not want them taking away IOPS (at all) from my more important VMs.  This, however, may not always be possible due to existing SAN/NAS configuration and budget.

Another option is to set a limit on the amount of IOPS on a particular VM.  Limits place a hard cap for a resource, meaning that if you limit (in this case) the VM to 100 IOPS, it will never be able to exceed this if it is required and even if your datastore is not currently under load.  In this case your VM would be struggling to complete a task even though there are available resources.

My preference would be to use shares.  Shares take a bit of planning, unplanned share configuration can lead to unexpected results.  Shares will restrict access to resources only during times of contention.  So if, for example, this test VM needed 105 IOPS it could have it unless ESXi detected resource contention in which case it would give preference to systems with a higher share value.  Doing this on a per VM basis can become unmanageable even in small environments, thats why I tend to use Resource Pools when I have a scenario that requires implementing shares because the number of shares in a resource pool is divided among the VMs in that resource pool.

Lets say for example you have two resource pools; Production and Dev.  You assign 10,000 shares to Production which has 10 VMs and 5000 shares to Dev which has 5 VMs.  It would seam at this level Production has more than twice the shares of Dev, however you also have to take into consideration how many VMs are in each resource pool.  In the scenario I described above, all of the VMs have an equal share to the resources because the Production resource pool is diving 10,000 shares among 10 VMs, and Dev is dividing 5000 shares among 5 VMs.  Also keep in mind that as the number of VMs in a resource pool changes, so to do the affects (effects? meh) of the shares.  If I divide my shares today among 10 VMs in production, but add 10 more VMs, I've now skewed my share distribution so that the VMs in the Dev resource pool actually have more per VM!

Chris Wahl has a nice looking PowerCLI script <a href="http://wahlnetwork.com/2012/02/01/understanding-resource-pools-in-vmware-vsphere/" target="_blank">here</a> (<a href="http://wahlnetwork.com/2012/02/01/understanding-resource-pools-in-vmware-vsphere/" target="_blank">http://wahlnetwork.com/2012/02/01/understanding-resource-pools-in-vmware-vsphere/</a>) that I want to test out.