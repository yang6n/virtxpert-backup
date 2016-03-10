---
ID: 1181
post_title: >
  Restoring a file from a VM backup with
  Unitrends
author: Jonathan Frappier
post_date: 2013-07-11 09:54:31
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/restoring-a-file-from-a-vm-backup-with-unitrends/
published: true
dsq_thread_id:
  - "1488782689"
---
In my last two posts, we looked at <a href="http://www.virtxpert.com/trying-out-unitrends-enterprise-backup/" target="_blank">installing Unitrends</a> and configuring a <a href="http://www.virtxpert.com/creating-a-backup-job-with-unitrends-for-vms/" target="_blank">backup job</a>.  Now, lets restore some data.  In this example I have the domain controller for my lab setup on an Incremental Forever job that runs every hour.  First click on the vCenter server in your navigation window and then click the restore button.  As you can see here, I am presented with a graph that shows me the results and times of my recent backup jobs.
<p style="text-align: center;"><a href="http://www.virtxpert.com/wp-content/uploads/2013/07/unitrends-restore-graph.png"><img class="aligncenter  wp-image-1183" alt="unitrends-restore-graph" src="http://www.virtxpert.com/wp-content/uploads/2013/07/unitrends-restore-graph.png" width="584" height="467" /></a></p>

<ul>
	<li>To start the restore process, click on one of the green marks in the graph, or one of the items in the Recovery Point Times window.</li>
	<li>Next, select whether you have to chose what type of restore you want to do.  If you click the Next (Select Options) button you can chose to restore the entire VM to a host or use <a href="https://www.youtube.com/watch?v=xYk-OA1VL7I" target="_blank">Instant Recovery</a>, which as the feature states allows near instant recovery of the VM which I will also cover in a later post.  As you can see here Unitrends sees both of my host and allows me to select whichever datastore I would like to recover to.</li>
</ul>
<p style="text-align: center;"><a href="http://www.virtxpert.com/wp-content/uploads/2013/07/unitrends-restore-vm.png"><img class="aligncenter  wp-image-1184" alt="unitrends-restore-vm" src="http://www.virtxpert.com/wp-content/uploads/2013/07/unitrends-restore-vm.png" width="650" height="552" /></a></p>

<ul>
	<li><span style="line-height: 13px;">The other option to restore a single file by clicking on the Next (Select Files/Items) button.</span></li>
	<li>You will be prompted with a message that no disk image exists.  Click the Create button on the lower right.</li>
	<li>A disk image of your selected snapshot time will be created.  You have the option of mounting the image as an iSCSI target or navigating to a network path to view the files.</li>
	<li>If you open the network path, you will see folders for each of the volumes Unitrends is protecting.  For most modern Windows OS's, volume1 will be your C drive, volume0 will be the recovery/system drive.</li>
	<li>Double click on any of the folders and you can navigate to ANY file that is present on the system during that snapshot, its not just files that changed since the last incremental; this is why Incremental Forever and Unitrends is so powerful.  As you can see in the screenshot below, even though I selected a backup from 7/5 I can still see, access and restore my files from the original full backup on 6/10!</li>
</ul>
<strong><a href="http://www.virtxpert.com/wp-content/uploads/2013/07/unitrendsfilerestore.png"><img class="aligncenter size-full wp-image-1185" alt="unitrendsfilerestore" src="http://www.virtxpert.com/wp-content/uploads/2013/07/unitrendsfilerestore.png" width="768" height="465" /></a></strong>

<strong>Conclusion</strong>

<strong></strong>Again, with simplicity as the theme, I am able to quickly and easily access files that were backed up and restore them to any computer.