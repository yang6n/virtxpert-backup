---
ID: 577
post_title: 'Building a VMware Horizon Workspace Lab &#8211; Part 1 Lab Basics [Updated]'
author: Jonathan Frappier
post_date: 2013-03-28 12:06:47
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/building-a-vmware-horizon-lab-part-1/
published: true
dsq_thread_id:
  - "1170427945"
---
**Update 1 - the reviewers guide calls for quad-core procs, thought I could get away without them but having an error importing the OVA.  Bringing a quad core proc host into my cluster now to validate**

**Update 2 - Yup, it REALLY wants quad core procs, hope you have a beefy lab.**

Many of my customers want to take advantage of mobile/remote computing, at $300/user VMware Horizon Suite is priced well even for small businesses to get these features/compatibility.  I will be  following the <a href="http://www.vmware.com/files/pdf/techpaper/vmware-horizon-workspace-reviewers-guide.pdf" target="_blank">Reviewer Guide</a> which was published by VMware.

There are 5 vApps that comprise Horizon, so we need to ensure we have an environment capable of running.  This is in addition to vCenter and other infrastructure services such as Active Directory and DNS (which may be running on your AD server internally or in lab environments.

The requirements for all 7 vApps are (included vCenter and 1 domain controller)

[ultimatetables 1 /]

&nbsp;

A description of each of the vApps can be found in the <a href="http://www.vmware.com/files/pdf/techpaper/vmware-horizon-workspace-reviewers-guide.pdf" target="_blank">Reviewer Guide</a>.  Also called out in the reviewer guide, reverse looks ups must be configured - a step I sometimes skip when setting up a quick/temporary lab so don't gloss over the system requirements.

Now that I know what I need, plus clearly a few more resources, my lab environment will consist of two DL380 G5 Xeon Dual-Cores running ESXi 5.1 and a Dell 1950 with dual quads also running ESXi <del>running FreeNAS for shared storage</del>.  The reviewers guide calls for Xeon quad-core, <del>I checked with <a href="https://twitter.com/joshuatownsend" target="_blank">s</a>ome folks who has been demoing Horizon since it was in beta and thinks you should be okay for a lab/POC setup</del>, and it really wants quad-cores as deploying the OVA would not allow me to proceed beyond host selection.  There are plenty of post/resources on installing both so I won't bore you with those details (but if you really want me to just leave a comment and I will be more than happy to oblige).

<em>**Update - I took the FreeNAS server and made it a 3rd host, then installed FreeNAS as a VM and presented that to each of the ESXi hosts to mimic shared storage**</em>

Next I registered for trial versions for VMware Horizon Workspace and downloaded the OVA files, Windows client and ThinApp tools from <a href="https://my.vmware.com/web/vmware/info/slug/desktop_end_user_computing/vmware_horizon_workspace/1_0" target="_blank">VMware's site</a>, uploaded my Windows ISO's to my host so I could spin up a domain controller and vCenter server.  Normally for lab work I would just go the vCenter appliance route, but that has burned me before so figured a little extra work can't hurt this time around.  Now that AD and <a href="http://www.virtxpert.com/vmware-vcenter-sso-5-1-installation/" target="_blank">vCenter are installed</a> and working, I made note of the DNS records I will be using for the various Horizon components (page 13 of the reviewers guide).

Our environment is now ready to starting configuring specific VMware Horizon settings.  In my <a href="http://www.virtxpert.com/building-a-vmware-horizon-workspace-lab-part-2/" target="_blank">next post</a> I will cover IP pools, importing the necessary vApps and initial configuration.