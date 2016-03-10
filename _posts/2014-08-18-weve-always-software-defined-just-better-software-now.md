---
ID: 2481
post_title: 'We&#8217;ve always been software defined, we just have better software now'
author: Jonathan Frappier
post_date: 2014-08-18 07:49:06
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/weve-always-software-defined-just-better-software-now/
published: true
dsq_thread_id:
  - "2937116822"
---
Recently I was asked to chat about several topics including Hybrid Cloud, storage and software defined.  It got me thinking about the topic and what I've come to realize is, we have always been software defined.  The difference today versus say 10 years ago is we are writing better software and better understand how technology needs to support the business now.

10 years ago, if I purchased a switch for example, from any vendor I would go out and buy something that supported the number of ports I needed as well as through put.  Without software on that switch it would be nothing but metal and circuit boards.  Additionally, the software on the switch would "define" some of the more advanced capabilities.  Depending on the switch, software might unlock features such as routing or firewall like capability.  What we have done today is moved the logic and manageability from the switch up a layer so we can be more responsive to business needs.  It doesn't mean we weren't software defined then, it just means we understand better today what needs to be done and can leverage things like NSX, ACI or OpenDaylight to achieve better results.

It's not just networking, software defined storage solutions are also getting smarter.  We can identify "hot" data and move them to faster drives or take old data and move it off to an archive service all without human intervention.  10 years ago we were probably doing that manually.  We can also use tools like ViPR or Sanbolic to manage heterogeneous storage environments rather than managing each individual piece of hardware.

Now don't forget, software still needs hardware.  If I have 48x 1Gbps ports that can run at full wire speeds, there is no software in the world that will make those ports act like 10Gbps ports.  The software, if buggy I guess could show them as 10Gbps ports, but I'll be awfully disapointed in the performance when I start trying to move data through them.  Likewise on the storage side, my software is much smarter, but it can't turn a 7200RPM SATA disk into an SSD.  I might be able to do something clever like cache it in RAM but its not changing the functionality of the underlying hardware.

What are your thoughts on SDX - marketing gimic or smarter software?