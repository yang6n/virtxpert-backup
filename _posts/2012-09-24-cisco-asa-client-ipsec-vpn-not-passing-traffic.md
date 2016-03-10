---
ID: 154
post_title: >
  Cisco ASA client IPSEC VPN not passing
  traffic
author: Jonathan Frappier
post_date: 2012-09-24 07:47:19
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/cisco-asa-client-ipsec-vpn-not-passing-traffic/
published: true
jabber_published:
  - "1348473197"
email_notification:
  - "1348473199"
reddit:
  - 'a:2:{s:5:"count";i:0;s:4:"time";i:1359698594;}'
dsq_thread_id:
  - "1119170088"
---
Recently I needed to  setup a new VPN to replace an aging Cisco VPN Concentrator, as part of the upgrade I also wanted to add redundancy to the firewall as there was only a single older ASA 5510 setup by the previous IT team.  I decided to setup a pair of Cisco ASA 5520′s with an IPSEC VPN for users which would authenticate against Microsoft Windows Network Policy Server (previously Internet Authentication Server or IAS).  The current firewall was working well with 2 point to point VPN’s already configured and the ACL’s setup properly.  Rather than re-invent the wheel, I decided to simply forklift the configuration onto the new ASA’s and swap them out.  When the two ASA’s arrived, I setup a basic configuration and applied a pretty standard VPN configuration that would support my needs and tested with a small group of volunteers - all went swimmingly until….

I went to apply the configuration to the current production ASA 5510 – again this wasn’t rocket science - an ACL here, aaa-server there and and a few policies later and it should have been working.  I emailed a few test users and asked them to connect and boom they were on the VPN – but wait!  They were not able to pass any network traffic to the protected network.  I knew the configuration worked fine since I had tested on the new ASAs.  I setup a capture on the ASA but was not seeing any traffic so I checked all the routes, made sure the correct networks appeared in the VPN client, still nothing  - not even a single hit on the capture.  The packet tracer showed all traffic being able to flow in both directions until phase 12, being dropped by an implicit deny.  After double checking our ACL’s over and over again I opened a ticket with Cisco TAC.  So what burned me?  A <a href="http://www.cisco.com/en/US/products/ps6120/products_white_paper09186a00809fcf38.shtml">Dynamic Access Policy</a> (DAP)!  The previous IT team had tried to configure a VPN on the ASA years before, but it never worked.  They had tried to use the ASDM to configure it and created this policy which was conflicting with my VPN configuration even though we hadn’t explicitly defined the group-policy to be used on our connection.  I removed the no nat ACL entry and traffic was able to pass as expected.