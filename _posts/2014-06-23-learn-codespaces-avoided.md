---
ID: 2287
post_title: >
  What to learn from CodeSpaces and how it
  could have been avoided
author: Jonathan Frappier
post_date: 2014-06-23 13:37:18
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/learn-codespaces-avoided/
published: true
dsq_thread_id:
  - "2789293106"
---
I'd like to state up front I have no inside knowledge on CodeSpaces, these opinions were formed based on the information they posted at http://www.codespaces.com/

I don't know any of the people at CodeSpaces, however what I do know of them drives home the point that developers are not operations people (operations people are also not developers, just to be fair) and the mindset that a developer can and should be in charge of operation decisions is wrong (no offense, go do what you are good at).

I've seen many companies who think that because developers are technical, they can do any technical job. This is simply not true. Developers are good at writing code, systems administrators and engineers are good at operations, and maybe its that clash of opposing forces that has lead business to listen to the people writing the software instead of the people trying to keep the lights on (IT is utility right? (wrong)!).  To again be fair, there are quite a few admins/engineers that still to this day do not realize they are service providers, there to help the business run efficiently.

The first item that jumped out at me was the fact that their backup systems and production systems were stored, essentially together. Any sysadmin worth his weight knows you need to keep your backups offsite. Well, you say, there backups were offsite at Amazon! True, but they were not offsite from their production systems, a massive failure to Amazon would impact their ability to operate normally as well as their ability to recover, so in this case the backups may have well as been sitting on top of the server they were running on.

Second, as a "cloud" provider, in this case a SaaS type SVN/code hosting service, should have operated on multiple IaaS or PaaS providers, not just Amazon. At the very least a disaster recovery site should have been setup on some other service. Had they set it up in just another availability zone they would have been just as easily and critically impacted.

CodeSpaces fate also shows the need for multifactor authentication. While I would consider their lack of foresight to place their backups on a separate provider unfortunate and based on poor design, not having multifactor authentication in place was downright lazy. Amazon offers a virtual "fob" which generates random codes as the second level authentication for...wait for...<strong>FREE</strong>.  Thankfully they were not storing private keys at Amazon so customer data was presumably not accessed, just completely and totally lost.

So, what can you learn from CodeSpaces?

- Offsite to you does not mean offsite to your data. If you are using a 100% cloud service for running your business, you need a SEPARATE vendor for backup and DR,
- Use other providers for general high availability where you are running your application in multiple providers, not just mutliple availability zones with the same provider.
- Use two-factor authentication everywhere possible, at the very least where ever customer data and production systems are stored.

While its sad to see all the hardwork that went into building codespaces, as well as all the hardwork their customers lost, let this be a lesson to current and future startups as well as operations teams. It may also be a handy article to give to the CFO if your request for offsite backup or multifactor auth budget is denined!