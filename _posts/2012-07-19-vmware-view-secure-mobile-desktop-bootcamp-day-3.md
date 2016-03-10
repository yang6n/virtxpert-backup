---
ID: 36
post_title: >
  VMware View Secure Mobile Desktop
  Bootcamp Day 3
author: Jonathan Frappier
post_date: 2012-07-19 00:26:12
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vmware-view-secure-mobile-desktop-bootcamp-day-3/
published: true
jabber_published:
  - "1342657572"
email_notification:
  - "1342657572"
tagazine-media:
  - 'a:7:{s:7:"primary";s:0:"";s:6:"images";a:0:{}s:6:"videos";a:0:{}s:11:"image_count";s:1:"0";s:6:"author";s:7:"7110326";s:7:"blog_id";s:8:"38472741";s:9:"mod_stamp";s:19:"2012-07-19 00:26:12";}'
dsq_thread_id:
  - "1136227626"
---
[youtube http://www.youtube.com/watch?v=uV2U5VZQIj0]

VMware View Bootcamp Mobile Secure Desktop - Day 3

Overview - Storgae Considerations / Best Practices w/Nimble

Nimble - hybrid iSCSI CASL (Cache Accelerated Sequenial Layout), Tierless

Config
- Setup Nibmle Setup GUI
- Network considerations
- Multi interface - mgmt, iSCSI Discover, iSCSI data, support
- Recommend separate network for mgmt and data
- Data - round robin mpio
- Jumbo Frames for 10G end to end, host-switch-storage
- Perf Policies
- Define policy for VDI
- Block size = 4k
- Caching = Yes
- Compression = Yes

- Host connectivity
- Initiatior group, ESXi hosts/clusters
- Enable vCenter pluging

via CLI on nimble
- vmwplugin --register
--server &lt;vcenter&gt;
--username &lt;user&gt;
--password &lt;password&gt;
via CLI on vCenter
- esxcli storage nmp satp rule add
--psp=VMW_PSP_RR
--satp=VMW_SATP_ALUA
--vendor=Nimble
Makes for easy deployment/volume creation from vSphere

Protection Templates
- sync, snapshots, replication
- consistent application of policy to volumes
- 1 for core inf, 1 for vdi pools
- Efficent storage, managed at volume level or collection level

- Volume collections contain set of volumes with same mgmt properties
500gb to 1tb suggested, reserve 50% for thin provisioning

- Capacity overcommit - thin provision, compression, linked clones
- MPIO

IOPS
- read req, write req, balacne overall IOPS
- View Storage Accelerator still = cool