---
ID: 2056
post_title: 'Update the vCenter Server Appliance #VCSA'
author: Jonathan Frappier
post_date: 2014-03-17 08:32:02
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/update-the-vcenter-server-appliance-vcsa/
published: true
dsq_thread_id:
  - "2450674943"
---
Doing an update the vCenter Server Appliance (VCSA) is quite easy thanks to the built in updater.  To update your VCSA, following the directions below.  Please note that during the installation vCenter will be <span style="color: #ff0000;"><strong>unavailable</strong></span>.  As with any update, take appropriate precautions to restore your environment in the event of a problem such as having a valid backup.  In the case of the vCenter VM, this becomes challenging because you generally need vCenter to interface with your backup software!
<ul>
	<li>Navigate to the configuration page of your VCSA, typically https://f.q.d.n:5480</li>
	<li>Click on the <span style="color: #0000ff;"><b>Update </b></span>tab</li>
	<li>Click on the <span style="color: #0000ff;"><strong>Check Updates</strong></span> button</li>
	<li>If there are updates available, you will see a <span style="color: #339966;"><strong>Available Updates</strong></span> message in green as pictured here</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/03/vcsaupdates.jpg"><img class="aligncenter size-full wp-image-2057" alt="vcsaupdates" src="http://www.virtxpert.com/wp-content/uploads/2014/03/vcsaupdates.jpg" width="572" height="332" /></a>

&nbsp;
<ul>
	<li>Click on the <span style="color: #0000ff;"><strong>Install Updates</strong></span> button and click the <span style="color: #0000ff;"><strong>OK </strong></span>button when prompted</li>
	<li>You will see a notification window that updates are being applied</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/03/updating.jpg"><img class="aligncenter size-full wp-image-2058" alt="updating" src="http://www.virtxpert.com/wp-content/uploads/2014/03/updating.jpg" width="525" height="110" /></a>

&nbsp;
<ul>
	<li>During the installation process, you will eventually lose access to the vSphere Web Client</li>
	<li>After a few minutes the installation will complete.  At this point you cloud log back into the vSphere Web Client, however you'll notice a reboot is required for the changes to take effect.</li>
	<li>Click on the <span style="color: #0000ff;"><strong>System</strong> </span>tab and click the <span style="color: #0000ff;"><strong>Reboot</strong> </span>button - that's it, you're done!  Quick tip, make note of the host the VCSA is running on prior to restarting in case it does not come back up and you need to log in directly to the host to troubleshoot.</li>
</ul>
If you run into trouble, check out this <a href="http://virtuwise.com/getting-an-error-updating-your-vcsa-this-might-help" target="_blank">post from Angelo Luciani</a>

<strong>Summary</strong>

Updates for the vCenter Server Appliance are quite easy, and straight forward.  As always check your normal processes for testing and applying updates!