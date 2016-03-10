---
ID: 2944
post_title: >
  Synology DS1513+ beeping after
  installing SSDs (New deployment)
author: Jonathan Frappier
post_date: 2014-11-14 10:00:14
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/synology-ds1513-beeping-installing-ssds-new-deployment/
published: true
dsq_thread_id:
  - "3224222514"
---
I just got a Synology DS1513+ and wanted to try out the SSD cache.  Having never powered it on I pulled two of the 2TB Seagate drives and installed 2x Corsair SSDs.  Once I powered on the device, it started beeping and wouldn't stop.  Turns out that when shipped with drives there is an existing volume already created.  The beeping was an error because I basically broke the volume removing the two 2TB drives.  To turn off the beeping, do the following:
<ul>
	<li>Log into DSM, since I am assuming this is a new deployment you can find the IP at https://find.synology.com</li>
	<li>Log in as admin with no password</li>
	<li>The control panel window will open</li>
	<li>Click on Beep off, take aspirin to fix the headache</li>
	<li>Close the control panel window</li>
	<li>In storage manager you will see Volume 1 in a crashed state, highlight it and click remove</li>
	<li>Click OK then yes to confirm deleting the volume</li>
	<li>You should now see no volumes in storage manager and the disk station health change to good</li>
	<li>You can now go about creating volumes as you see fit</li>
</ul>
Having purchased other Synology's with no drives in them I didn't expect the volume to already exist.  If your Synology is beeping, log in and check it out!