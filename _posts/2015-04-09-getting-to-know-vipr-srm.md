---
ID: 3659
post_title: Getting to know ViPR SRM
author: Jonathan Frappier
post_date: 2015-04-09 08:29:46
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/getting-to-know-vipr-srm/
published: true
dsq_thread_id:
  - "3667616773"
---
<em>**Disclaimer: I am an EMC employee, this post was not sponsored or in any way required by my employer, it is my experience getting to know this particular product.**</em>

One of the upcoming tools I will be working with is ViPR SRM. ViPR SRM is a storage management tool that allows for monitoring the end-to-end health of your environment. I know what you're thinking, "C'mon now Frapp that sounds awfully marketingy" and you're right - it does, BUT let me give you an example of why some of the tools in ViPR SRM interest me.

<img class="alignleft wp-image-3662 size-medium" src="http://www.virtxpert.com/wp-content/uploads/2015/04/network-is-fine-300x300.jpg" alt="network-is-fine" width="300" height="300" />Have you ever went over to a friends cube to chat and they say the app it ain't no good? The reports are slow, the app keeps crashing, and the chicken taste like wood. Okay, but seriously how many times has someone walked over and said "my application is slow/down/broken" with no further detail, leaving it up to you to isolate what is going on? It has happened to me often. Worse is when you are the personal responsible for storage and someone else responsible for networking does the Jedi hand wave and says the network is fine, it must be storage.

&nbsp;

That is where ViPR SRM comes it, it can show you the relation from virtual machine, through the hypervisor, datastore, data path to the storage array hosting the virtual machine. Further, for heterogeneous it supports multiple types of applications, operating systems, hypervisors and storage arrays. Of course it supports more EMC products, since it is an EMC product but you don't necessarily have to run an EMC array to leverage ViPR SRM.

Below are some of the systems supported by ViPR SRM, an updated list can always be found at <a href="https://store.emc.com/us/Product-Family/EMC-ViPR-Products/EMC-ViPR-SRM/p/EMC-ViPR-SRM?showPrice=true&amp;isProdActive=true&amp;productClassCode=System#Specifications" target="_blank">emc.com</a>.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr.jpg"><img class="aligncenter size-full wp-image-3660" src="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr.jpg" alt="vipr" width="995" height="500" /></a>

While getting ready for the installation, know that you can deploy as either a pre-packed vApp or install the application on 64-bit versions of RedHat, CentOS, SUSE, or Windows; during my post I will be deploying the vApp version which includes 4 virtual machines. The 4 virtual machines each have unique roles as a typical multi-tier application would - there is a web front end for UI and reporting, database backend for storing data, and collector for, well, collecting data. In large environments with multiple arrays you may deploy multiple collectors.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-components.png"><img class="aligncenter size-full wp-image-3661" src="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-components.png" alt="vipr-srm-components" width="608" height="369" /></a>

In my next few blog posts I'll be reviewing the installation of ViPR SRM, and review some of the dashboards and how they might help you in the day to day monitoring, and troubleshooting of your environment. If you'd like to learn along with me check out the ViPR SRM <a href="https://community.emc.com/docs/DOC-34286" target="_blank">free e-Learning on ECN</a>.