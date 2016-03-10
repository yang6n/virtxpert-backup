---
ID: 2045
post_title: VSAN all things!
author: Jonathan Frappier
post_date: 2014-03-13 09:39:49
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vsan-all-things/
published: true
dsq_thread_id:
  - "2421201405"
---
First and foremost I want to congratulate the VSAN team for an amazing product.  This technology, to me, is very exciting and has the ability to change the way many companies look at virtualization infrastructure, eliminating the need to add complexity simply for the sake of storage.  For those under a rock for the last few weeks, if not since VMworld, VSAN aggregates local server storage into a shared pool accessible to hosts within a VSAN cluster.  A host needs only an SSD and normal spinning disk to provide storage to the VSAN cluster.  Once added, new servers can be added in and have their storage aggregated into the pool.  Additionally, you can define policies for how VSAN will tolerate failures either to disks or entire servers within the cluster.  Performance, well that is not a problem either as VSAN has been able to provide up to 2,000,000 IOPS in a 32 host cluster (of course real world mileage will vary).

[caption id="attachment_2022" align="aligncenter" width="392"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/03/vsan.png"><img class="size-full wp-image-2022" alt="Basic VSAN design" src="http://www.virtxpert.com/wp-content/uploads/2014/03/vsan.png" width="392" height="295" /></a> Basic VSAN design[/caption]

My question is whether is the simplicity of VSAN enough to adopt it given its current cost structure?  Talking strictly for a server virtualization use case, VSAN costs $2495 USD per processor, so for most modern hosts the cost would be $4990 per host with 2 processors.  In the scope of a small deployment, say 10 hosts, you are looking at $49900 for your cluster just in software cost for VSAN (you are already paying for vSphere anyways so to me that is not a consideration).  Beyond the software cost there is a hardware related cost to setting up VSAN.  I know that many of the ESXi hosts I have installed over the years have gone bare bones on local storage so that I could move that cost over to my NAS or SAN to provide shared storage for the host.  Using the hardware cost in Dunan Epping's post (found <a href="http://www.yellow-bricks.com/2014/03/12/building-hyper-converged-platform-using-vmware-technology-part-3/" target="_blank">here</a>) you would be adding a $1512 in drives per host, or $15120 for your 10 host cluster bringing the total cluster upgrade cost to roughly $65,000 (assuming the disk controllers are on the HCL).  If you haven't read through the <a href="http://www.vmware.com/files/pdf/products/vsan/VSAN_Design_and_Sizing_Guide.pdf" target="_blank">VSAN Design and Sizing Guide</a> I suggest you do.

<strong>So how much space do I get?</strong>

Determining the amount of usable space is a bit different from determining space on a traditional storage device.  There are three main steps to determine the usable capacity of your VSAN cluster (yes I've left out some bits from the design guide around objects, I'm just thinking about space).

First determine the amount of cluster capacity in your VSAN cluster.  This formula is
<blockquote>Hst x NumDskGrpPerHst x NumDskPerDskGrp x SzHDD = y</blockquote>
In our case thats 10 hosts, 1 disk group, 5 disks per group and 1TB or 10*1*5*1=50TB of RAW capacity.

Next determine how many VMs there will be to determine swap space utilization, then you can determine the amount of space available for VMDKs.  The formula for determing swap space is:
<blockquote>ClusterCapacity – (VMs x vmSwp x 2)</blockquote>
For the sake of math, lets use  10 VMs per host each with 10GB of memory using no reservations.  Basic eyeball test, that seems about right for 5 hard drives (mileage obviously varies based on workload).  Again in our scenario that is 50TB-(100*10*2)=2TB leaving us with 48TB of disk capacity.  Now we can calculate the usable capacity:
<blockquote>(DiskCapacity – DskGrp x DskPerDskGrp x Hst x VSANoverhead )/(ftt+1)</blockquote>
For our setup, with failures to tolerate set to 1 we would have 48TB of disk capacity - (1 DiskGroup (assuming this is per host, its unclear in the sizing guide) * 5 disks per group * 10 hosts * 1TB overhead)/(ftt of 1+1)= 23TB of usable storage.

The other piece we have not factored in is the dedicated networking pieces to support VSAN, however this is not all that dissimilar from running a dedicated network for iSCSI or NFS, and should be less expensive than fiber channel so for the sake of this post I'm willing to call that a wash.

So the question becomes, assuming you have 10 hosts, is 23TB of space for VMDK storage for $65,000 a good value (and if we are comparing to usable space in a traditional SAN/NAS it would be 25GB (after all EMC and NetApp don't factor in losing swap space on their appliances)).  If I were to hop on over to store.emc.com I can see a VNX 5300 with 12x2TB drives is right around $50,000 (EMC does not publish pricing for their "FAST" solution except to say it starts between $50 and $100K.  FAST is an SSD cache much like VSAN uses).  Now I'd expect VSAN, if for no other reason than the read and write cache to out perform a VNX here so we are looking at a cost difference of $15,000.  I'd not be surprised to see FAST come in anywhere from $5 to $10K so, yea VSAN pricing seems about right.

Another interesting cost offset option is in your vSphere license.  With VSAN handling your storage, you might make the case that you could skip Enterprise Plus (list $3500/processor) and go with Standard ($1000/processor) for smaller environments.  You shouldn't be missing SIOC or SDRS with VSAN so maybe that's the offset in cost?  Standard + VSAN for $3500/processor instead of $3500 for Enterprise Plus + $2500 for VSAN?  Of course you will still lose DRS, Distributed Switches and Auto Deploy but for a small environment maybe that's a worthy trade off for infrastructure simplicity.

<strong>**Updated - I've been informed via the Twitters that a VSAN license gives you virtual distributed switches even on top of a vSphere standard license.  I missed this bit in the announcement but if that's the case, it really adds to the vSphere Standard + VSAN license option seem more worthwhile**</strong>

<strong>Scalability</strong>

So far it looks like VSAN is at least on part with say a VNX5300 (speed tests not withstanding) however there is another area in which VSAN can out pace traditional storage.  With most traditional storage devices you have one or two controllers handling all of your storage.  When you need to add more performance, typically IOPS you add another shelf and some more drives, however when  you do this you are typically impacting overhead for those controllers to manage additional disks.  If you need to add more throughput, in many cases you are looking at additional controllers, not just shelves which will add a major expense.  When you are expanding either capacity or performance for VSAN, its a new server which acts as that controller and the storage you need, typically at a much cheaper point of entry than a new SAN/NAS controller will cost.

<strong>Summary</strong>

There might be a little bit of VSAN sticker shock to some people, myself included.  It seems VMware has opted to not undercut EMC with VSAN through this initial release as a VNX5300 with FAST might be about inline for performance with what 5 disks per host in VSAN could do (of course that is theory, I don't have the hardware to test these numbers, if you do please let me know).  In any case, VSAN and hyper-convirged infrastructure seems to clearly be the path going forward.  I wonder what, if any, discount customers will actually see on VSAN.

<em>Equations for sizing taking directly from the Virtual SAN Design and Sizing guide.  Pricing for EMC VNX5300 and vSphere licenses taken directly from EMC and VMware online pricing.</em>