---
ID: 295
post_title: 'My first written &#8220;design&#8221; proposal &#8211; can you help me rip this design apart?'
author: Jonathan Frappier
post_date: 2012-12-20 08:16:40
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/my-first-written-design-proposal-can-you-help-me-rip-this-design-apart/
published: true
jabber_published:
  - "1356009400"
tagazine-media:
  - 'a:7:{s:7:"primary";s:0:"";s:6:"images";a:0:{}s:6:"videos";a:0:{}s:11:"image_count";i:0;s:6:"author";s:7:"7110326";s:7:"blog_id";s:8:"38472741";s:9:"mod_stamp";s:19:"2012-12-20 13:16:40";}'
publicize_twitter_user:
  - jfrappier
email_notification:
  - "1356009403"
reddit:
  - 'a:2:{s:5:"count";i:0;s:4:"time";i:1356987946;}'
dsq_thread_id:
  - "1116136373"
---
For the past 12 years I have straddled design, administration and management for various systems including VMware and never having the opportunity to really master any one specific aspect.  As I have decided to focus on VMware design, I am hoping all the VMware gurus can (nicely) rip this apart.  I think my ego is ready for a butt-kicking - its the only way I will get better.  While this first written design happens to be a very basic setup - a small business wanting to have some CAPEX spend before the end of 2012, I'd still love your feedback.  This is also written as part of a proposal, and more detailed documentation would be created as part of the actual implementation.  Dell is the vendor of choice for most (if not all) of the hardware so if you don't like Dell that is certainly fine but would appreciate your feedback on the high level aspects of what I have written and how I can improve.  Also, storage is intentionally light right now as I am still going back and forth with a few vendors.  Here it goes...

Company X wishes to purchase and implement the necessary servers, storage and networking devices to support their business and future needs, including the ability to host Microsoft Dynamics GreatPlains.  The network will be built on two physical servers with shared storage to support the necessary Windows and VMware Operating Systems.  An initial system design was provided, however updated based on the 12/17/2012 meeting.  This design factors in the ability for additional capacity to support the growth of the company.

<strong>Phase 1: Infrastructure Design</strong>

The following items needs to be considered as part of the design to ensure performance and availability:
<ul>
	<li>Storage</li>
	<li>Networking</li>
	<li>VMware Host (ESXi)</li>
	<li>VMware vCenter</li>
	<li>Virtual Machines (VMs)</li>
	<li>Backup and Disaster Recovery</li>
	<li>Expansion</li>
</ul>
<b>Requirements</b>:  Provide basic network services (Active Directory, DNS, DHCP) and security (Group Policy) and the capacity to run Microsoft Dynamics GreatPlains during 2013 (possibly during Q2) and support future growth.

<b>Assumptions</b>:  Power, cooling, space and internet access will be provided and available.

<b>Constraints</b>:  While the driving factor is to purchase the best available platform by the end of 2012, budget is a constraint in building a true n+1 configuration.

The current server room may be too small for a server rack and there is currently no dedicated AC to maintain &lt; 70deg F temperature.

<b>Risks</b>:  Several single points of failure including:  internet access, core network switch and storage.  A failure to any of these services may result in extended down time.  There is no generator available, power outages (unplanned or building maintenance) will result in down time.

<b>Current State Analysis</b>:  There is currently a Sonicwall TZ170 Wireless firewall connected to RCN and two unmanaged switches for computers and phones.

<b>Stakeholders</b>:  Owner of Company X and Company Y (a provider of managed services for ongoing support of the environment).

<b>Storage</b>:  A single, 12 drive enclosure will be used connected via iSCSI and a single dedicated switch for iSCSI traffic.

<b>Networking</b>:  A total of 4 switches will be used.  Rather than use a single 48 port POE switch for both phones and computers, 2 separate 24 port switches will be used.  The reason for this change is to provide redundancy in the event of a switch failure.  With a single switch, all connectivity (servers, computers and phones) would be lost, with 2 switches a failure to either the phone or computer switch would not impact the other services.  The server switch is still a single point of failure in this design.

Dell 6224 24 port switches will be used, one each for servers/core networking and one for desktops.  A 6624P 24 port Power Over Ethernet (POE) will be used for phones.  Finally a Dell 5524 24 port switch will be used for storage connectivity to the host servers.

<b>VMware vCenter</b>:  The VMware vCenter appliance will be deployed.  This will eliminate Microsoft Windows licensing requirements and still allow the cluster to grow to up to 5 hosts or 50 virtual machines.  Proposed vSphere licensing will limit the cluster to only 3 hosts.

<b>Cluster</b>:  There will be 2 host configured in the cluster.  DRS will<del> be set to manual due to the small number of virtual machines to reduce complexity</del> not be used as it is not available with this edition of vSphere.  HA will be configured, this will allow for Virtual Machines to be power on by the remaining host should there be a hardware failure.  HA performs a reboot, so there will be a period where services will be unavailable as they are restarted.  Fault Tolerance (FT)  <em>is not available with the proposed edition of vSphere</em> and could be used on VMs with only a single vCPU however FT will not be an option for vCenter, the Microsoft Dynamics GreatPlains application or database server as they require multiple vCPUs.

<b>Virtual Machines (VMs)</b>:  The following VMs will be needed at a minimum:

-  2x Windows Servers for Active Directory, DNS, and DHCP
<ul>
	<li>Approximate specifications:  Single vCPU, 2GB vRAM, 30GB thin formatted VMDK for OS, single vNIC connected to the VM Network.  Suggest using memory reservation to reduce disk consumption.</li>
	<li>An additional 166MB of memory is required for Virtual Machine overhead memory.  Should 2 vCPUs and 4GB of vRAM be required, 243MB of overhead memory would be required.</li>
</ul>
-   1x VMware vCenter Appliance for vCenter
<ul>
	<li>Approximate specifications:  Dual vCPU, 8GB vRAM, 60GB thin formatted VMDK, single vNIC connected to the VM Network.  Suggest using memory reservation to reduce disk consumption.</li>
	<li>An additional 332MB of memory is required for Virtual Machine overhead memory.  Should 16GB of vRAM be required, 509MB of overhead memory would be required.</li>
</ul>
Because the vCenter appliance will be used, Update Manager will not be available to update the hosts.  Manually patching will be required, however this is manageable because there are only 2 host (maximum of 3 based on proposed vSphere license).

- 1x Windows server for Microsoft Dynamics GreatPlains application remote access
<ul>
	<li>Specifications will be dependent on the number of concurrent users running the Dynamics GreatPlains client.</li>
	<li>Estimated specifications:  Dual vCPU, 8GB vRAM, 30GB think formatted VMDK for OS, 60GB thin formatted VMDK for application installation (exact requirements to be determined with Dynamics consultant)</li>
	<li>An additional 332MB of memory is required for Virtual Machine overhead memory.  Should 16GB of vRAM be required, 509MB of overhead memory would be required.</li>
</ul>
- 1x Windows server for Microsoft Dynamics GreatPlains database
<ul>
	<li>Specifications will be dependent on the number of concurrent users running the Dynamics GreatPlains client and size of the database</li>
	<li>Estimated specifications:  Dual vCPU, 8GB vRAM, 30GB think formatted VMDK for OS, 60GB thin formatted VMDK for database installation (exact requirements to be determined with Dynamics consultant).  Additional space may be required based upon the size of the database to store backups.</li>
	<li>An additional 332MB of memory is required for Virtual Machine overhead memory.  Should 16GB of vRAM be required, 509MB of overhead memory would be required.</li>
</ul>
<b>VMware Host (ESXi)</b>: Two physical servers will be built on Dell PowerEdge R720.  The R720xd was not selected as the increased cost provides additional drive bays which are being moved to an iSCSI storage appliance.

The Dell R720 with the Intel Xeon E50-2600 Series CPU is supported on ESXi 5.1 as of 12/19/2012 on the VMware Hardware Compatibility List (<a href="http://www.vmware.com/resources/compatibility/detail.php?deviceCategory=server&amp;productid=14966&amp;deviceCategory=server&amp;partner=23&amp;releases=171&amp;keyword=720&amp;systemTypes=2&amp;page=1&amp;display_interval=10&amp;sortColumn=Partner&amp;sortOrder=Asc" target="_blank">HCL</a>).

The <b>Intel Xeon E5-2620</b> is recommended; the incremental cost per server is $900 (retail) over the base model CPU and provides two additional processing cores as well as Hyper-Threading.  This processor provides a cost savings of $3533 (retail) over the originally proposed E5-2670.  While there are performance differences, I do not feel  as though these warrant a $3533 price increase per server.

28GB of memory is required for the 5 necessary virtual machines.  An additional 2GB of memory is required to support the VM overhead memory for a total of 30GB required.  Because this is only a 2 host cluster, in order to support running all 5 VMs on a single host I would suggest <b>32GB of RAM per host</b>.  RDIMMs are suggested because there will be multiple DIMMS per memory channel.  The cost of 16GB of RAM per host would be $320, the cost for 32GB of RAM per host would be $640.  4x 8GB, with 2x 8GB DIMMs per channel (CPU) will be used.

ESXi will be installed and configured locally on each host.  <b>2x 500GB 7200RPM SATA</b> drives will be used.  <b>2x 1TB SATA</b> drives will be added to perform backups of the VMs to each host.  An additional 4 SATA drives can be added per host at a later date to support new storage requirements.  Local storage in each host would be used for archives, one-off backups or other not critical data only.

Typically multiple NICs and switches are used for various functions – management, VM network, vMotion, and FT.  Because FT is not likely to be useful in this environment and because there is only a single server switch in this environment we will setup 3 interfaces – management, VM network and vMotion though all 3 will traverse the same physical switch.  Separate VLANs will be created for the vMotion network to isolate and broadcast traffic that could impact the management and VM network.  <b>Three Broadcom 5720 Dual Port (DP) 1Gb cards</b> are suggested.  While only 1 port will be used initially, the additional ports will already be available should they be needed for increased performance or availability.

One <b>Broadcom 57810 Dual Port (DP) 10Gb </b>card is suggested for iSCSI connectivity as they provide hardware iSCSI offload capabilities.

<b>Licensing</b>:

-  VMware vSphere Essentials Plus Kit for 3 hosts will be used.
<ul>
	<li>Maximum number of hosts 3 – each with up to 2 processors.</li>
	<li>Includes HA, vMotion and VMware Replication</li>
	<li>Current promotion includes VMware Go Pro for VM patch management.</li>
</ul>
- Microsoft Windows Standard licenses will be used.
<ul>
	<li>As the company grows, suggest investigating Windows Data Center edition license for unlimited Windows VM deployments.</li>
</ul>
<b>VM Backup and Disaster Recovery</b>:  VMware Data Protection will be used which is part of the vSphere Essentials Plus Kit.  For disaster recovery, the storage appliance can replicate data to a second offsite appliance.

<b>Expansion</b>:  The limiting factor in the current configuration (performance only) will be:
<ul>
	<li>Storage and disk I/O per second (IOPS) - Additional VM density per host can be achieved by adding additional storage shelfs and drives.  Also if IOPS becomes a limiting factor, a storage appliance replacement that supports Solid State Disk (SSD) or Serial Attached SCSI (SAS) drives can be performed.</li>
	<li>Hosts – There are currently only two hosts in this configuration, adding a 3<sup>rd</sup> would allow for more VMs, greater redundancy and the ability to enable DRS for automatic workload provisioning.</li>
	<li>Licensing – VMware licensing allows for a third host with up to two processors be added.  Additional licensing will be needed to add more than 3 hosts.</li>
	<li>Memory – The host are configured with 32GB of memory each.  Assuming both hosts are functional this would allow for additional VMs to be added, however additional memory can be added to each of the host.</li>
</ul>