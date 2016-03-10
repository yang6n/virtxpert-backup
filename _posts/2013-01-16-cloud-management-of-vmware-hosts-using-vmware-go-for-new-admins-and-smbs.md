---
ID: 361
post_title: >
  Cloud Management of VMware hosts using
  VMware Go for new admins and SMBs
author: Jonathan Frappier
post_date: 2013-01-16 10:28:58
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/cloud-management-of-vmware-hosts-using-vmware-go-for-new-admins-and-smbs/
published: true
jabber_published:
  - "1358350145"
email_notification:
  - "1358350149"
reddit:
  - 'a:2:{s:5:"count";i:0;s:4:"time";i:1358555264;}'
publicize_twitter_user:
  - jfrappier
dsq_thread_id:
  - "1074720589"
---
VMware Go is a is a cloud based management solution for (small) vSphere deployments and includes features such as  the IT Advisor, ESXi and vCenter installation automation and patch/inventory scanning (though my free version is prompting me to upgrade to Go Pro for those right now).

As I am setting up a new lab environment, I thought I would poke around at some of the features.  I did a basic ESXi install leaving all the defaults.  As I drill into the inventory for this host, VMware Go identified two potential configuration problems I should correct - setting an NTP server and changing the IP address.

<a href="http://jonathanfrappier.files.wordpress.com/2013/01/host.jpg"><img class="aligncenter size-large wp-image-362" alt="host" src="http://jonathanfrappier.files.wordpress.com/2013/01/host.jpg?w=1024" width="1024" height="610" /></a>

Typically the IP address could be set via the vSphere Client, DCUI or command line and NTP via the DCUI or command line, but VMware Go is targeted (IMO) towards the small business or IT shops with little to no VMware experience so having the ability to set these items via a web interface seems very useful.  Click the Apply NTP Settings button worked flawlessly for the suggested NTP server (you may want to use an internal NTP source in your environment).

<a href="http://jonathanfrappier.files.wordpress.com/2013/01/ntp.jpg"><img class="aligncenter size-full wp-image-363" alt="ntp" src="http://jonathanfrappier.files.wordpress.com/2013/01/ntp.jpg" width="359" height="70" /></a>

There is an import VM feature, but this only works from a VMware Server instance (VMware on Windows) and since that has long since been out to pasture, not sure how useful that would be.  Being able to communicate with VMware Converter running on the network seems like it would be a more useful feature.  I also have the ability to scan the host for patches, since I installed the latest 5.1 release there were none to install so I downloaded 4.1 Update 2.  Adding the host was again easy and straight forward, though the NTP setting originally threw an error but trying to apply again worked correctly.  Running a patch scan worked as expected this time, I found the missing patches and automated shutting down VMs, putting the host into maintenance mode and rebooting the server.  One thing to remember, these are "updates" not "upgrades" so you cannot bring a 4.1 host up to 5.1 or even bringing a 5.0 hosts up to 5.1.

<a href="http://jonathanfrappier.files.wordpress.com/2013/01/patches41.jpg"><img class="aligncenter size-full wp-image-365" alt="patches41" src="http://jonathanfrappier.files.wordpress.com/2013/01/patches41.jpg" width="430" height="356" /></a>

One feature I would like to see, especially for the small IT shop who isn't comfortable managing ESXi directly is the ability to rename the hosts, currently both my hosts are named "localhost" and have the ability to to manage other basic IP settings such as subnet mask, DNS servers and gateways.

If the free version from VMware Go is nothing else, its a great tool to keep your ESXi hosts up to date with latest patches.  As I get further in my lab setup (vCenter etc...) I will write up additional features that are available in VMware Go and activate my VMware Go Pro trial.