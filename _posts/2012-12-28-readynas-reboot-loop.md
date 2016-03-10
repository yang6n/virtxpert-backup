---
ID: 317
post_title: ReadyNAS Reboot Loop
author: Jonathan Frappier
post_date: 2012-12-28 11:56:19
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/readynas-reboot-loop/
published: true
jabber_published:
  - "1356713779"
publicize_reach:
  - 'a:2:{s:7:"twitter";a:1:{i:1983177;i:508;}s:2:"wp";a:1:{i:0;i:14;}}'
publicize_twitter_user:
  - jfrappier
email_notification:
  - "1356713780"
tagazine-media:
  - 'a:7:{s:7:"primary";s:0:"";s:6:"images";a:0:{}s:6:"videos";a:0:{}s:11:"image_count";i:0;s:6:"author";s:7:"7110326";s:7:"blog_id";s:8:"38472741";s:9:"mod_stamp";s:19:"2012-12-28 16:56:19";}'
reddit:
  - 'a:2:{s:5:"count";i:0;s:4:"time";i:1357231397;}'
dsq_thread_id:
  - "1095159492"
---
I hate SOHO technology, generally lacking in support/features.  Recently I ran into a ReadyNAS stuck in a seemingly famous reboot loop.  As a Netgear partner I may have better support than most but this is a story of the process to try and get it back online.

First they had me try an OS reinstall, according to support this is no destructive but does put back all the settings to the factory default.  To do this, have the IT gods favorite tool handy, a paper clip.
<ol>
	<li>Power the unit off</li>
	<li>Push the paperclip into the small reset button on the back of the unit under the USB ports (at least on a ReadyNAS200) and turn the unit on.</li>
	<li>After a few seconds a Boot Menu will appear.  Use the backup button to go to OS Reinstall and push the paperclip in the reset button again to select.</li>
</ol>
This step did not fix my problem, but now we didn't have internet access.  The next step probably should come first in Netgears support steps and that is to boot into TechSupport mode.  Since we had already reset the unit, it booted with the default IP address which probably doesn't work on anyone's actual network so if you find yourself in this situation, maybe suggest tech support mode first.

Since I didn't have a spare switch handy and, since it was a Friday, wasn't much in the mood to start making changes to the customers core switch, I need to figure out how to connect.  Plugging directly in didn't work as expected, however there are 2 ports on the back of the ReadyNAS so I plugged my laptop in directly and I could ping!  Great now I will hop on the web gui and reconfigure for the network.... no so much - no HTTP.  Okay no problem I will SSH .... nope but wait - TELENT!  No to figure out the tech support username and password.  Google to the rescue, the root password for tech support mode is 'infr8ntdebug' - once logged in, it appears quite linuxy (great...**sarcasm**).  At this point, it appears you need to go through Netgear tech support in order to find/access anything to fix the problem.  All the forums suggest calling tech support and it is magically fixed.  I will update this post if/when I hear back from them.

<em>Update:  2 hour wait so far for L3 support, just posted a message on their support forums after my original phone call.</em>

<em>Update 2:  Now almost 3 hours, called back and being told it could be as much as 2-3 days or longer before I get a response.  </em>

<em>Update 3:  22 hours later, on a Saturday morning, on hold waiting for our "partner" 24x7 technical support because no one has called me back or emailed me.</em>

<em>Update 4:  My partner support wouldn't help me because of how I needed them to access the device (Kind of can't blame them) but thankfully someone from the community support forum had the directions on how to fix.  Very easy and I recorded the session so I will post notes shortly.  Essentially its mount the boot volume, delete the file, sync the writes, and unmount all the volumes.</em>