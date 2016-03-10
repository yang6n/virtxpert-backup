---
ID: 3416
post_title: 'Video: Prepare CentOS 6.x virtual machine for cloning'
author: Jonathan Frappier
post_date: 2014-12-29 08:00:16
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/video-prepare-centos-6-x-virtual-machine-cloning/
published: true
dsq_thread_id:
  - "3369915035"
---
In my last video, we walked through how to install VMware Tools for CentOS 6.x. Now we are going to prepare the virtual machine for cloning. This requires we remove a specific file; /etc/udev/rules.d/70-persistent-net.rules. This file contains the MAC address for the virtual machine. Once removed, the file will be created during the initial boot with the matching MAC address for the cloned virtual machine.
<h3>Prepare CentOS 6.x virtual machine for cloning</h3>
<iframe width="640" height="480" src="//www.youtube.com/embed/u2BQOr3Sl7o" frameborder="0" allowfullscreen></iframe>