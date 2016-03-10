---
ID: 1173
post_title: >
  Creating a backup job with Unitrends for
  VMs
author: Jonathan Frappier
post_date: 2013-07-10 09:21:56
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/creating-a-backup-job-with-unitrends-for-vms/
published: true
dsq_thread_id:
  - "1470023388"
---
In my last <a href="http://www.virtxpert.com/trying-out-unitrends-enterprise-backup/" target="_blank">post</a>, I wrote about installing Unitrends and how easy the process was.  Now that you have Unitrends installed, creating a backup job is also very easy.  First log into your recovery console, typically at https://ipofyourimportedappliance/recoveryconsole.  Now that you are logged in, you should see any devices you added during the initial setup wizard, so in my case I cam see my vCenter server that was added as well as the individual VM I added.  If you want to add another machine (or for some reason you did not add any during the wizard) click on Settings, then the Clients, Networking and Notifications icon and then the Clients icon.  Now click on Add Client and fill in the appropriate information into the form and click the Setup button.

<a href="http://www.virtxpert.com/wp-content/uploads/2013/07/unitrends-clients.png"><img class="aligncenter size-full wp-image-1175" alt="unitrends-clients" src="http://www.virtxpert.com/wp-content/uploads/2013/07/unitrends-clients.png" width="262" height="66" /></a>

&nbsp;

Since I have already added my vCenter server during the setup wizard, I will now configure a backup.
<ul>
	<li>Click on your vCenter server and click the backup button, you should now see a list of all the VM's your vCenter server is managing.</li>
</ul>
<p style="text-align: center;"><a href="http://www.virtxpert.com/wp-content/uploads/2013/07/vcenter-unitrends.png"><img class="aligncenter  wp-image-1176" alt="vcenter-unitrends" src="http://www.virtxpert.com/wp-content/uploads/2013/07/vcenter-unitrends.png" width="645" height="535" /></a></p>

<ul>
	<li>Name the scheduled</li>
	<li><span style="line-height: 13px;">Select the VM you wish to backup and select a schedule type.  Available options include Incremental Forever, Full with Incrementals, Full with Differentials, or Custom.  In this case I am select Incremental Forever which will do an initial full back with incrementals at which ever intervals you select.  The beauty of this is for systems that require a low RPO you can set the recurrence to a minute interval that A) allows the backup to finish and B) falls within your RPO (If your backup can't finish within your RPO window go back to the drawing board).</span></li>
	<li>I have selected my server, Incremental forever and now set the Incremental Forever scheduled to every 5 minutes.</li>
	<li>Click the Save button, click the confirm button.</li>
	<li>Unitrends will validate your settings and give you a green check if you are good to go, click the Okay button.</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2013/07/unitreds-backup-created-success.png"><img class="aligncenter size-full wp-image-1177" alt="unitreds-backup-created-success" src="http://www.virtxpert.com/wp-content/uploads/2013/07/unitreds-backup-created-success.png" width="640" height="496" /></a>

&nbsp;

Now click on the status button, and click on the accordion tiles on the right to view the initial backup.  Once finished your backups will run based on your selected schedule.

<a href="http://www.virtxpert.com/wp-content/uploads/2013/07/unitrendsbackuprunning.png"><img class="aligncenter size-large wp-image-1179" alt="unitrendsbackuprunning" src="http://www.virtxpert.com/wp-content/uploads/2013/07/unitrendsbackuprunning-1024x248.png" width="640" height="155" /></a>

<strong>Conclusion</strong>

As you can see, it was very easy to configure the backup.  Since Unitrends integrates with vCenter it is very easy to add new VM's to your backup environment.  In my next post, I will review how you can restore data using Unitrends.