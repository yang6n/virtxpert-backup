---
ID: 194
post_title: 'Service Level Agreements (SLAs) &#8211; A silent victim in the Consumerization of IT'
author: Jonathan Frappier
post_date: 2012-11-05 08:16:43
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/service-level-agreements-slas-a-silent-victim-in-the-consumerization-of-it/
published: true
jabber_published:
  - "1352104722"
tagazine-media:
  - 'a:7:{s:7:"primary";s:0:"";s:6:"images";a:0:{}s:6:"videos";a:0:{}s:11:"image_count";i:0;s:6:"author";s:7:"7110326";s:7:"blog_id";s:8:"38472741";s:9:"mod_stamp";s:19:"2012-11-05 08:38:41";}'
email_notification:
  - "1352104726"
publicize_twitter_user:
  - jfrappier
reddit:
  - 'a:2:{s:5:"count";i:0;s:4:"time";i:1352166818;}'
dsq_thread_id:
  - "1129179089"
---
Last week I was having a discussion with an Infrastructure as a Service (IaaS) provider and one of the questions I left with was how can I integrate your service with my existing internal infrastructure.  My thought was I could build a private-hyrbrid cloud (if that's not a term yet I own it - my definition of a private-hybrid cloud is <em>being able to provide on demand resources between an internal/traditional company owned data center and an external service provider who can dedicate private resources</em>) between my internal infrastructure and and this vendor to provide on demand infrastructure, scaling and high availability.  This got me to thinking of how I might be able to meet the sometimes unreasonable SLA's asked of technology groups from the business and further started to wonder why the SLA's have kept increasing even though IT budgets are being slashed.

I started to think back to meetings between non-technology business leaders (e.g. sales, marketing, finance, etc...) and myself as we discussed what they wanted from IT.  Typically when I am architecting a system or network design one of my first questions is to those business leaders to explain what their expectations are.  On many occasions the answer has been "100% up-time."  We all know in IT that's not really reasonable which is why we add-in scenarios about maintenance and vendor bugs not counting against that SLA.  Now, if I am an IT person and my CEO and CFO say they want 100% up-time - well great I can certainly design you a very resilient, high performance infrastructure that can even overcome poor software code to recover from application or system crashes.  One problem typically comes up however - the desire to have 100% up-time does not typically equate to the budget to build that type of infrastructure.  When we are reviewing the design and budget to try and reach that 100% up-time requirement the comment I hear quite often is something along the lines of "Why does it cost so much, Facebook/LinkedIn/other consumer based website never goes down and  I use that for free" or "Why do we have to spend so much on storage?  I can upload all the pictures I want to Facebook  and I use that for free."  Once you explain that those services you are consuming from Facebook or LinkedIn is not actually their business, their business is big-data, business intelligence and advertising I am typically able to re-focus the meetings on the real needs of the business and not a false expectation based on the perceived up-time of consumer based services and determine a real SLA for various systems and applications.

So while we typically think of the consumerization of IT in terms of BYOD and related needs such as security and monitoring or enterprise social networking, it reaches all the way through the network and infrastructure right into policies, procedures and service level agreements.  Have you had a similar experience when working on your projects or budgets?