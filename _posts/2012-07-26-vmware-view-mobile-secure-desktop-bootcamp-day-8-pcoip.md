---
ID: 61
post_title: >
  VMware View Mobile Secure Desktop
  Bootcamp Day 8 PCoIP
author: Jonathan Frappier
post_date: 2012-07-26 01:12:53
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vmware-view-mobile-secure-desktop-bootcamp-day-8-pcoip/
published: true
jabber_published:
  - "1343265174"
email_notification:
  - "1343265174"
dsq_thread_id:
  - "1124508946"
---
[youtube http://www.youtube.com/watch?v=6ddJGbxpwxc]

VMware View Mobile Secure Desktop Bootcamp - Day 8

PCoIP Optimzation

Real-protocol - like VoIP
Host-based pixel encoding - onlyl change pixels are sent
UDP based - no TCP overhead, app layer reliability

PCoIP Protocol Features
"Build to lossless" - lower quality updates on images in motion until static
Utilizes multiple codec dependig on content
Adaptive bandwidth consumption - uses as much bandwidth as possilbe
Client side caching of frequent data
WMI session monitoring

Text Codec
- Lossless text
- Increased compression on ClearType
- 10-20% bandwidth savings

Disable Build-to-lossless
- Build to "preceptually" lossless, cant tell for most use cases
- 10-15% bandwidth savings

Client-Side Caching
- Store frequent content on endpoint
- Sends 'address' and 'location of content
- 30-40% bandwidth savings

PCoIP Monitoring tools
- Lakeside SysTrack
- Liquidware Labs
- Xangati

Free
- Perfmon
- PCoIP Log Viewer

SSL VPN encaps UDP in TCP packets, lose UDP benefits
Bypass WAN acceleration and IDS/IPS

Avoid usecases with round trip 300ms latency

<!--more-->

No per-packet load balancing, enable stickiness
Use VM optimization guides for visual settings

PCoIP Tunable Parameters in pcoip.adm via GPO or registry

Build to lossless set to enable in GPO + accept checkbox, 0 via registry
Client-side cache enable with cache size

When to tune
- Best practices first
- network sized/configed
- optimize desktop image
- PCoIP already adapts
- Reduce bandwidth = impact user experience

Disable build-to-lossless
Config max session bandwidth
Config session floor when..
- experiencing packet loss but network has availability
- packetloss on WiFi or 3g/4g
Config max frame rate
Config max initial image quality
Config min image quality
Config audio bandwidth limit
Config client-side cache

&nbsp;

&nbsp;