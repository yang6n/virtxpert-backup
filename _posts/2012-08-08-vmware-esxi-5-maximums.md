---
ID: 87
post_title: VMware ESXi 5 Maximums
author: Jonathan Frappier
post_date: 2012-08-08 17:44:48
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vmware-esxi-5-maximums/
published: true
email_notification:
  - "1344447890"
jabber_published:
  - "1344447889"
reddit:
  - 'a:2:{s:5:"count";i:0;s:4:"time";i:1359268514;}'
dsq_thread_id:
  - "1205159713"
---
As I am studying for the VCP5, I will have some random posts here so I can look back and review quickly!  Might be boring stuff to some folks.

Number of virtual CPUs per host:  2048

Number of cores per host:  160

Number of logical CPUs:  160

Number of virtual CPUs per core:  25

Amount of RAM per host:  2TB

VMs per host:  512 (up from 100)

VMs per cluster:  3000 (up from 1280)

Number of vSwitches:  248

Ports per vSwitch:  4088 (8 reserved by ESXi = 4096)

Maximum ports per host:  4096 (yes 1 vSwitch maxed out would be the max per host)

Port groups / vSwitch:  256

Uplinks / vSwitch:  32

VMkernel NICs:  16

Maximum active ports per host:  1016

vDS per vCenter:  32

Maximum vDS ports per host:  4096

vDS ports per vCenter instance:  30,000

ESXi Hosts per vDS:  350

Static Port groups per vCenter instance:  5,000

Ephemeral port groups per vCenter instance:  256

VM CPUs:  32 (64 as of 5.1)

VM RAM:  1TB

VM SCSI Adapters:  4 with 15 devices per

Ports:  Parallel 3, Serial 4, IDE 4, Floppy 2, USB 1 controller / 20 Devices