---
ID: 1058
post_title: 'Cisco UCS Chassis Discovery Protocol &#8211; Useless?'
author: Jonathan Frappier
post_date: 2013-06-10 11:59:58
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/cisco-ucs-chassis-discovery-protocol-useless/
published: true
dsq_thread_id:
  - "1384823896"
---
Recently we added a new Cisco UCS chassis, our Chassis Discovery Protocol is set to 4 however we only had 1 uplink from each FEX (Fabric Extender) or IOM/IO Module as its referred to in the documentation to the Fabric Interconnect on the new chassis.  According to the UCS documentation the chassis should NOT have been discovered:
<blockquote><em>Chassis cannot be discovered by Cisco UCS Manager and is not added to the Cisco UCS domain.</em></blockquote>
There is very little available beyond the documentation so I opened a ticket with TAC to confirm the behavior of changing the Chassis Discovery Policy.
<blockquote><em>Changing the Chassis Discovery Policy from 4 to 1 will have no effect on chassis #1.  The discovery policy is only used when a new chassis is added, changing the policy to one will allow the 2<sup>nd</sup> chassis with 1 uplink to be discovered properly.  If you were to add a third chassis with 4 uplinks in the future the chassis would only bring up one uplink due to the policy but all that you would do is re-acknowledge the chassis and all uplinks would be added.</em></blockquote>
Based on the documentation and feedback from TAC I expected to have to change the policy in order for the chassis to be discovered, which I interpreted as SEEN by UCS Manager.  The wording in the documentation does not seem to be clear on this particular setting as my new chassis with only 1 uplink was SEEN by UCS Manager, however it was in a warning state due to "Unsupported Connectivity."

I selected the option to "Acknowledge Chassis" which brought the configuration state to "Up," however UCS Manager seemingly could not detect any information about the chassis.  At this point I changed the Chassis Discovery Policy to 1.  As TAC said, nothing changed with my first chassis, all 4 uplinks still appeared as up however I lost connectivity from my FEX to the FI on chassis #2, odd so I changed the policy back to 4, reset the FEX and they came back online, the chassis was discovered and registered with UCS Manager.

<strong>Conclusion/Question</strong>

So my question, what is the point of the Chassis Discovery Policy?  With it set to 4 from the original configuration the chassis was seen when I enabled the server port on the FI, when I changed the policy to 1 which should have matched chassis 2 it was no longer able to detect the chassis.  Now in hindsight, I may have just been able to reset my FEX/IOM after changing the policy to 1 (downfall of late night maintenance, your brain isnt always firing on all cylinders).  Has anyone had experience with this that cares to share any information?