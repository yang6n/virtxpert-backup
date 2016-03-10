---
ID: 1200
post_title: >
  Introduction to Indeni Dynamic
  Knowledgebase
author: Jonathan Frappier
post_date: 2013-07-16 10:33:40
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/introduction-to-indeni-dynamic-knowledgebase/
published: true
dsq_thread_id:
  - "1504425560"
---
<a href="http://indeni.com/product-overview" target="_blank">Indeni </a>Dynamic Knowledgebase is a "game changing" network device monitoring tool that allows administrators to scan their network and monitor devices based on real world device profiles.  In addition to monitoring your devices, Indeni also provides remediation information for each alert.  There are two versions of the product today - the Dynamic Knowledge base (i.e. enterprise/full version) and the stand alone Indeni Health Check which is a free product that runs on a standard desktop OS with Java installed.  What is interesting to me about Indeni is that they have taken the next step in vendor agnostic monitoring and built in solutions to errors, dare I say a "big data" like approach versus configuring your basic ping or service monitors and then leaving the troubleshooting up to the engineer/administrator.  The <a href="http://indeni.com/resource-center/videos-webinars" target="_blank">features </a>from Indeni include monitoring, device backups, profiling (think host profiles in VMware for validating configuration settings), change management and troubleshooting.

For the purposes of this post, I have downloaded the trial of Indeni Dynamic Knowledgebase which is delivered as an ISO image that includes a hardened linux OS.  The user guide can be found <a href="http://indeni.com/sites/default/files/downloads/indeni_User_Guide.pdf" target="_blank">here</a>.  Once downloaded, place the ISO in a location available for you to install, in my case I have uploaded to one of my datastores.  I then created a VM and selected the ISO image for the CD device.  Once booted, you go though a pretty general linux setup to set the IP information and then let the installer configure the necessary components.  One item to keep an eye for is that you need to manually restart the system once the configuration is complete (seem's like that should be automagic).  Once the restart has finished, you can access the web gui at https://ipaddress:8181

<a href="http://www.virtxpert.com/wp-content/uploads/2013/07/indeni.png"><img class="aligncenter size-full wp-image-1204" alt="indeni" src="http://www.virtxpert.com/wp-content/uploads/2013/07/indeni.png" width="714" height="399" /></a>

From here, you can log in with the default Indeni admin/admin123! user.  Accept the license agreement and decide weather you want to enable device deletion, for historical reporting purposes you may wish to select 'Disallow Device Deletion' or you may require this setting for other reasons; I chose disallow since it cannot be changed.  Once logged in I added a switch to verify Indeni could communicate with my network devices and it was able to successfully log in and verify that my device was online, with no alerts.  Once given a few minutes, it will start to generate recomendations for the device(s) it is monitoring.  You can see here it suggests I create a dedicated user account for Indeni to use across all my monitored devices.
<p style="text-align: center;"><a href="http://www.virtxpert.com/wp-content/uploads/2013/07/indenirec.png"><img class="aligncenter  wp-image-1207" alt="indenirec" src="http://www.virtxpert.com/wp-content/uploads/2013/07/indenirec.png" width="869" height="214" /></a></p>
<p style="text-align: center;"></p>
<p style="text-align: left;">The one area I was most interested in testing was the device configuration, backup and change tracking component however I have been unable to get this to work.  While my device appears in the monitored list, and I configured a backup job, there are no actual backups in the backup location (by default /var/indeni/backups/<em>devicename) </em>so I am not able to try this feature out - maybe a bug, maybe I am having trouble RTFM'ing but in my opinion this should be the easiest part to configure.</p>
<p style="text-align: left;"><strong>Conclusion</strong></p>
<p style="text-align: left;">Indeni is certainly on its way to creating an interesting product offering for managing and maintaining your network equipment.  The built in knowledge base, ability to monitor and to search config backups alone make this an interesting option for device management.  Stay tuned for a review of the free desktop version of the product.</p>