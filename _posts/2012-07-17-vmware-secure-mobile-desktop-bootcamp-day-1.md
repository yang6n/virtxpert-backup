---
ID: 24
post_title: >
  VMware Secure Mobile Desktop Bootcamp
  Day 1
author: Jonathan Frappier
post_date: 2012-07-17 00:48:58
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vmware-secure-mobile-desktop-bootcamp-day-1/
published: true
jabber_published:
  - "1342486139"
dsq_thread_id:
  - "1242604673"
---
The content for the first day of the VMware Secure Mobile Desktop Bootcamp is up, check it out over at <a href="http://communities.vmware.com/community/vmtn/desktop/view/msdbootcamp/video_1">http://communities.vmware.com/community/vmtn/desktop/view/msdbootcamp/video_1</a>

Notes from the first video:

VMware View Bootcamp Mobile Secure Desktop - Day 1

Overview
- Load balancing, vShield, AD, CA, Radius, View Considerations

Fully validated configuration, meant as a base to be updated to work for your needs.
- End user devices
- Connect via internal (trusted) or external networks (untrusted)
- L7 LB between networks
- Security servers send traffic to Connection Managers
- Infrastucture Services (AD DCs, DNS, SSO, CA, Radius, F&amp;P, Backup)
- vCenter, vShield, AV, VC Ops Manager
- VMware View desktop pools

Provide Mobility for VD session, Security, User Experience

<!--more-->

Items to consider
- IP Schema, VLANs, routing and DNS
- AD topology (child domains? new forest?)
- Security requirments and policies
- Application workload (what are the apps), ThinApp/AppV/XenApp or installed into image
- WAN/LAN QoS for real time/high speed access
- Compliance requirments

Load Balancing and namespace services (cap2)

vSheild - security zone around vm pools, apps, infrastructure
- Define rules in advance as part of scoping/documentation
- Remember rules for view agent/client/server communications and display
- Generate support logs from vSheild

vShield Endpoint
- AV/Malware at hypervisor level per VM host
- Tune AV strategy

Active Directory considerations
- Eval existing AD
- New domain?
- Enough resources in a site?
- Configure sites and subnets for DC/replication
- Enterprise CA needs to be configured in Forest Root Domain

Radius
- 2 Factor
- Plan for extra conection servers with redundancy
- Validated design uses MS Radius

Persona Management
- Roam user data/settings
- VMs for hosting profiles
- Use persona or roaming profiles - not both
- Folder redirection
- App specific requirments such as ThinApp
- AV strategy using persona - scanning of vSheild Endpoint

vSphere and View considerations
- Using vDS (virtual distributed switch)
- Auto-Deploy and host profiles
- DHCP and load balancing

Connection broker tagging feature in VMware View

Leverage vApps