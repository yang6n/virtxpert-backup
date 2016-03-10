---
ID: 1436
post_title: >
  Constant APD Errors, Failed HA failovers
  and other weird cluster connectivity
  problems solved (kinda)
author: Jonathan Frappier
post_date: 2013-10-07 09:11:59
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/constant-apd-errors-failed-ha-failovers-weird-cluster-connectivity-problems-solved-kinda/
published: true
dsq_thread_id:
  - "1832921141"
---
<a href="http://www.virtxpert.com/wp-content/uploads/2013/10/bang-head-on-keyboard.gif"><img class="alignleft size-full wp-image-1437" style="margin: 5px;" alt="bang-head-on-keyboard" src="http://www.virtxpert.com/wp-content/uploads/2013/10/bang-head-on-keyboard.gif" width="66" height="66" /></a>You may have seen an angry tweet or two recently geared towards a new HP switch that we acquired.  The switch, in theory, was purchased to fix lots of minor network problems we were encountering - mostly POE related due to the existing switches not being able to support the power requirements from our phones.  We looked for, and seemingly found a switch that could support our VMware host, network, SAN (NFS) and phone traffic for a fairly small network; 6 hosts, 200 or so VMs and 150ish end user devices (desktops, mobile devices +  desk phones).

Right after the switch was installed, we started to see several failed HA events for various VMs.  Nothing changed in the environment, we did a switch replacement and kept the configuration the same as the previous switch (well other than going from Cisco 3560's to an HP 8212).  After a couple of days of seeing this consistently I started looking through logs, trying to find some common link to the restarts.  At first it seemed like it might be backup related, as they were generally happening late at night into the early morning, but each day it shifted a few hours (generally occurring 16-18 hours apart) until it feel outside of the backup window and into normal business hours.

We opened tickets with the VAR we purchased the switch from, as well as with HP but both were quick to point the finger at a host configuration problem(s) so I started correcting some items to match the configuration of the switch; my theory was we knew the switch config was "good" on the Cisco side so I did not want to stray to far from what was previously working.  The uplinks on the host were all active, but there was no LACP groups setup so added a vSwitch for management with an active and standby uplink and a second vSwitch for VM and vMotion traffic, also with an active and standby uplink.  At this point we were nearing 24 hours with no HA events, I was ready to declare success until those ugly red explanation points started appearing again.

At this point, I was fairly confident the cluster and storage setup was in working order (not ideal but it should be working properly).  After a 2 hour call reviewing the setup, and 2 engineers throwing their hands in the air I decided to start a ping test between 2 windows laptops connected to the same line card - hmmm losing packets; not something I'd expect on a switch of this caliber - clearly it was a switch problem!  The dropped pings were finally enough for HP to escalate the case to tier 2, after all what is more basic than a simple ICMP request dropping.  Once on the phone with the HP tech, we got into tech mode (edomtset twice in the CLI) and saw something very interesting - the switch believed that the MAC's for all of the servers were moving between their actual physical port and the port for the firewall (in this case a Sonicwall).  After packaging up logs and monitoring the MAC moves for a few days I decided to drop in a firewall (ASA 5505) on another switch port and see if were still seeing the MAC moves with the Sonicwall disconnected (the only consitent problem we were seeing was port A1 involved with the MAC moves).

As soon as I removed the Sonicwall, the MAC moves stopped, along with the failed HA and APD errors we were seeing in the VMware logs.  A firmware update to the Sonicwall "seems" to have done the trick, but nothing in the release notes suggested the Sonicwall causing this type of behavior, nor were there any hints of problems in the HP release notes for the newest firmware.

So, failed HA events at completely random intervals, on random LUNs?  Check your MAC tables and make sure they are staying put.  Can't say I had ever seen this before.