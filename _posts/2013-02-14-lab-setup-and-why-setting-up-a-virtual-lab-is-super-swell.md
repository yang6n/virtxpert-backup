---
ID: 409
post_title: >
  Lab setup and why setting up a virtual
  lab is super swell
author: Jonathan Frappier
post_date: 2013-02-14 12:46:35
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/lab-setup-and-why-setting-up-a-virtual-lab-is-super-swell/
published: true
dsq_thread_id:
  - "1083564805"
---
Over the summer when I was preparing for my VCP5 test I purchased some equipment to setup at home and work on during my prep.  It was a pretty nice setup for under $500 - I got 2 dual processor, dual core desktops each with 4GB of RAM and a Buffalo NAS for storage.  I ran into one problem though, I am never home.  So after hours on install and configuring I was stuck with no/limited access to my lab environment.  Also I generally like to push to the point of breaking so I can figure out how to fix problems as well as master the setup.  When I want to go back and and test some new features or other products I generally rebuild the lab so I know I am starting from a clean slate.  Now that I have my VCP5, and my NFR Workstation license for passing I have been working with a virtual lab setup entirely in VMware Workstation.  I have a single computer with 2 SATA hard drives and 24GB of RAM with an i7.  As you will see in my notes, this is more than adequate for a lot of setup and testing and is very easy to rebuild.

<a href="http://www2.virtxpert.com/wp-content/uploads/2013/03/setup1.jpg"><img class="aligncenter size-full wp-image-565" alt="setup" src="http://www2.virtxpert.com/wp-content/uploads/2013/03/setup1.jpg" width="556" height="450" /></a>

I booted my first blank VM with a ESXi 5.1 ISO at 11:15A, then started writing so lost a few minutes.  Less than 45 minutes later (its now 11:55) I have 3 hosts setup - pretty easy when I am not waiting for some physical computer to boot, powered on my vCenter appliance for the first time taking a basic configuration and created my cluster.  Not bad for 45 minutes of work.  And yes, I know I skipped some best practices - for what I am setting up lab up for right now I am not concerned with a detailed setup, but just think if you could have vCenter and 3 hosts setup in less than 45 minutes (with distractions as I am setting up an Exchange server for my day job in the background) what you could do - such a time saver to have a SDL (Software Defined Lab)!