---
ID: 2231
post_title: 'Example design consideration &#8211; Company culture'
author: Jonathan Frappier
post_date: 2014-05-19 08:34:44
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/example-design-consideration-company-culture/
published: true
dsq_thread_id:
  - "2696686294"
---
<a href="http://twitter.com/josh_odgers" target="_blank">Josh Odgers</a> had another great post over at <a href="http://www.joshodgers.com/2014/05/19/enterprise-architecture-avoiding-tunnel-vision/" target="_blank">CloudXC</a> where he talked about the need for architects to <a href="http://www.joshodgers.com/2014/05/19/enterprise-architecture-avoiding-tunnel-vision/" target="_blank">think outside the scope of the task in front of them</a> to ensure they were not designing a solution that could cause problems down the road (he has a lot of great example design considerations in addition to this post).  This is a great post not just for IT/technology but any project as you have to constantly be thinking about future growth and sustainability in your projects - just because you meet the requirements for a specific task or project in a vacuum doesn't mean you aren't hampering future projects.  I feel quite blessed to have cut my teeth in technology with a manager and team who had this vision 15 years ago, and is one of the reasons I'm constantly shocked that technology groups today are just figuring out that we are all service providers.

A design consideration for my projects I often incorporate is that of company culture, a very non-technical consideration but one that is important just the same.  Some might lump this into business requirements but I feel that it is important to call this out as a separate consideration.  You have to understand not only the business and technical requirements of the organization you are designing a solution for, but also their work style, team and culture.

A recently project I was involved in scoping was for a small software services company.  They very much had a start-up type culture where many people wore many hats.  As their development processes were advancing, they wanted to achieve a more agile process both in their development and release cycles.  Knowing the people on the team, their work styles and preferences gave me insight into how to plan and design their infrastructure stack.  They were not the type of company who, for the foreseeable future, would need or want to dedicate people to maintaining hardware and infrastructure.  Knowing this, as well as their technical needs and business requirements lead me to suggesting  a platform built around a hyper-converged solution such as VSAN, ScaleIO, Nutanix or Simplivity.

While other solutions would have certainly worked, and knowing the goals of the company would have supported future technical growth, they were not the right solution for them to support on a day to day basis, or even when they needed to add more capacity; be it compute, network or storage.  Get to know the people you are designing solutions for, think out side of technical and business requirements and think about the people requirements for maintaining the solution being put in place to add another layer of depth to your design.