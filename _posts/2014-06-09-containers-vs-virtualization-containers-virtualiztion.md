---
ID: 2266
post_title: >
  Containers vs Virtualization or
  Containers + Virtualiztion
author: Jonathan Frappier
post_date: 2014-06-09 08:38:51
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/containers-vs-virtualization-containers-virtualiztion/
published: true
dsq_thread_id:
  - "2749404198"
---
Containers have been a hot topic of late, many are suggesting it is the next step in the virtualization evolution and spells doom for vSphere, Hyper-V or other "traditional" virtualization platforms.  For those who are not aware of containers, its is a packaged application that can run isolated from other applications.  It is not too dissimilar from ThinApps in a virtual desktop environment but focused on server applications such as Apache, Tomcat or other custom applications on top of a single Operating System.

Traditional OS level virtualization generally looks something like this:

<a href="http://www.virtxpert.com/wp-content/uploads/2014/06/esxi-os-app.jpg"><img class="aligncenter size-full wp-image-2267" src="http://www.virtxpert.com/wp-content/uploads/2014/06/esxi-os-app.jpg" alt="esxi-os-app" width="222" height="227" /></a>

Some, such as Linux Journal suggest it is the future and that traditional OS level virtualization and the hypervisor is not needed.  With containers, you could remove the hypervisor layer and run your OS directly on baremetal and run the "virtualized" applications helping to save resources (including budget) which would look something like this:

<a href="http://www.virtxpert.com/wp-content/uploads/2014/06/container.jpg"><img class="aligncenter  wp-image-2268" src="http://www.virtxpert.com/wp-content/uploads/2014/06/container.jpg" alt="container" width="413" height="411" /></a>

You can read more about Linux Journal's take on Containers here:  <a title="http://www.linuxjournal.com/content/containers%E2%80%94not-virtual-machines%E2%80%94are-future-cloud" href="http://www.linuxjournal.com/content/containers%E2%80%94not-virtual-machines%E2%80%94are-future-cloud">Containers—Not Virtual Machines—Are the Future Cloud | Linux Journal</a>

There seems to be a small group who think - as it generally is with most technology, that traditional OS/hypervisor virtualization and containers are complimentary.  Scott Lowe has a blog post here walking through the initial setting up along with some thoughts on LXC:  <a title="http://blog.scottlowe.org/2013/11/25/a-brief-introduction-to-linux-containers-with-lxc/" href="http://blog.scottlowe.org/2013/11/25/a-brief-introduction-to-linux-containers-with-lxc/">A Brief Introduction to Linux Containers with LXC - blog.scottlowe.org - The weblog of an IT pro specializing in virtual…</a>

My question is, why does it have to be Containers versus Virtualization?  Why can't it be a marriage of the two technologies to offer the best of each, or something like this:

<a href="http://www.virtxpert.com/wp-content/uploads/2014/06/container.png"><img class="aligncenter size-full wp-image-2269" src="http://www.virtxpert.com/wp-content/uploads/2014/06/container.png" alt="container" width="229" height="271" /></a>

With this model, you can still isolate and manage resources at the OS level which has been proven over and over again as well as drop containers on top of the virtualized OS?  Not only can I still leverage hypervisor features such as high availability, but I can reduce the number of VM's needed by adding more containers to a single VM.  Scale up resources when needed for adding containers OR scale out resources when needed for redundancy or additional throughput?  What are your thoughts?

You can find out more about popular container at the following sites:

Parallels: <a title="http://www.parallels.com/products/pvc/" href="http://www.parallels.com/products/pvc/">OS Virtualization Solution for Windows and Linux — Parallels Virtuozzo Containers - Parallels</a>

Docker:  <a title="http://www.docker.com/" href="http://www.docker.com/">Docker - Build, Ship, and Run Any App, Anywhere</a>

LXC: <a title="https://linuxcontainers.org/" href="https://linuxcontainers.org/">https://linuxcontainers.org/</a>

lmctfy (Google):  <a title="https://github.com/google/lmctfy" href="https://github.com/google/lmctfy">https://github.com/google/lmctfy</a>