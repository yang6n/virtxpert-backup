---
ID: 3085
post_title: >
  Whats missing from my vRealize
  Automation lab
author: Jonathan Frappier
post_date: 2014-11-30 11:00:34
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/whats-missing-vrealize-automation-lab/
published: true
dsq_thread_id:
  - "3276842717"
---
[display-posts category="vRA Home Lab" display-posts posts_per_page="15"]

With my vRealize Automation / vCloud Automation Center lab mostly working, I did want to recognize a few things we missed that you might like to investigate further on your own.

First, if you look back you'll notice we did not do anything specifically with vCenter Orchestrator.  Like vSphere templates, you can publish vCO workflows as catalog items to perform advanced or no routine tasks.  For example maybe you are an organization that makes heave use of vApps in vSphere and want to continue that.  vRA has no concept of vApps but using vCenter Orchestrator I could publish a workflow that will create the vApp and create virtual machines inside the vApp.  Additionally I could tie vCO into other infrastructure such as Active Directory or my storage layer using EMC ViPR for example.

We did not work with any of the advanced networking solutions such as VMware NSX or vCloud Networking and Security.  Consider the need for an isolated multi-virtual machine development environment, I could deploy an NSX edge device and places all of the virtual machines behind the edge device and provide access to the application to a specific set of users or other network segments.  Also missed in these posts were adding additional endpoints to connect to services such as vCloud Air or EC2 - things that could enable you to build a "hybrid" cloud

The last item I will cover here is charge back using vRealize Business (formerly IT Business Management Suite).  With vRB...no sorry not doing it - with ITBM you can get much more granular in cost tracking and turn that data into charge back to other groups or show back to justify your IT budget (remember IT people - you job is not to make money, its to support the business).

Thank you for following along with my vCAC / vRA posts, I hope you found them useful!