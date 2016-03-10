---
ID: 1830
post_title: 'VMware Memory Ballooning &#8211; Sched.Mem.MaxMemCtl versus Mem.CtlMaxPercent'
author: Jonathan Frappier
post_date: 2014-01-14 08:44:27
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vmware-memory-ballooning-sched-mem-maxmemctl-versus-mem-ctlmaxpercent/
published: true
dsq_thread_id:
  - "2121021681"
---
I was doing some research on VMware vSphere resource management techniques and was looking at Ballooning.  Ballooning is a process in which a special driver in VMware Tools can request memory from within the VM during times of host memory contention.  This allows the guest OS to determine if which memory can be made available, to what appears to be just another service to the guest OS.  In this example, Windows Server 2012 is plugging away with a certain amount of memory assigned to IIS.
<p style="text-align: center;"><a href="http://www.virtxpert.com/wp-content/uploads/2014/01/0464EN_02_04.jpg"><img class="aligncenter  wp-image-1833" alt="0464EN_02_04" src="http://www.virtxpert.com/wp-content/uploads/2014/01/0464EN_02_04.jpg" width="272" height="236" /></a></p>
However, during times of memory contention in the ESXi host, you might want to return memory from IIS so it can be shared with other, possibly more critical VMs.  This is where the ballooning process comes into play; appearing to be another service, it requests memory from the guest OS and allows the guest OS to determine which memory could be returned, in this case it takes memory from the idle IIS process.
<p style="text-align: center;"><a href="http://www.virtxpert.com/wp-content/uploads/2014/01/0464EN_02_05.jpg"><img class="aligncenter  wp-image-1834" alt="0464EN_02_05" src="http://www.virtxpert.com/wp-content/uploads/2014/01/0464EN_02_05.jpg" width="272" height="280" /></a></p>
There are two settings that were causing a bit of confusion, these definitions are from the VMware online pubs for 5.5:

<strong>Sched.Mem.MaxMemCtl</strong>:  Maximum amount of memory reclaimed from the selected virtual machine by ballooning, in megabytes (MB). If the ESXi host needs to reclaim additional memory, it is forced to swap. Swapping is less desirable than ballooning. <strong>Default</strong> = -1 (Unlimited) (VM advanced Setting)

<strong>Mem.CtlMaxPercent</strong>:  Limits the maximum amount of memory reclaimed from any virtual machine using the memory balloon driver (vmmemctl), based on a percentage of its configured memory size. Specify 0 to disable reclamation for all virtual machines. <strong>Default</strong> = 65% (Host advacned setting)

These two advanced settings seem to contradict each other; <strong>Sched.Mem.MaxMemCtl</strong> suggests that it could reclaim an unlimited amount of memory via ballooning, but <strong>Mem.CtlMaxPercent </strong>suggests it can only take up to 65%, which would make sense.

In this case, Mem.CtlMaxPercent is set at the host, so all VMs, by default could return up to 65% of the configured memory to the balloon driver.  In some instances, however, you may not wish to allow the ballooning process to reclaim any memory for critical VMs.  This is where you use <strong>Sched.Mem.MaxMemCtl </strong>which you add at the VM level.  You could set <strong>Sched.Mem.MaxMemCtl </strong>to 0 (zero) which would disable ballooning all together or set a specific amount of memory you are comfortable giving back to the balloon driver for that specific VM.