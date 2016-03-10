---
ID: 2711
post_title: >
  Update EMC ViPR SRM licenses after they
  have expired
author: Jonathan Frappier
post_date: 2014-10-23 12:13:34
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/update-emc-vipr-srm-licenses-expired/
published: true
dsq_thread_id:
  - "3148249682"
---
If you are running EMC ViPR SRM, and your license key expires you will no longer be able to log into the UI where you could have installed a new license key.  Instead you will need to update the license(s) via the command line.  The directions I had found had <del>a mistake</del> were unclear, so thought I'd publish the steps that worked for me here.

First and foemost, obtain your new license key by submitting a SR (Service Request) via support.emc.com and follow the steps below.
<ol>
	<li>Launch WinSCP or your file copy tool of choice</li>
	<li>Connect to your ViPR SRM front end server and login in as a user who can elevate privileges (Default root/Changeme1!)</li>
	<li>Navigate to /opt/APG/</li>
	<li>Upload the license key zip file (which may have multiple license files
<ol>
	<li>If not already, name the file licenses.zip - It gave me an error when it was  not named that</li>
</ol>
</li>
	<li>SSH to your ViPR SRM FE server</li>
	<li>Login as  a user who can elevate privileges</li>
	<li>Run:</li>
</ol>
<p style="padding-left: 60px;">/opt/APG/bin/manage-licenses.sh install /opt/APG/licenses.zip</p>
<p style="padding-left: 60px;">/opt/APG/bin/manage-modules.sh service restart tomcat</p>
You should now be able to log in

[caption id="attachment_2712" align="aligncenter" width="1151"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/10/viprsrm.png"><img class="size-full wp-image-2712" src="http://www.virtxpert.com/wp-content/uploads/2014/10/viprsrm.png" alt="ViPR SRM Dashboard" width="1151" height="664" /></a> ViPR SRM Dashboard[/caption]

Now that I was able to log in, I still had to upload my licenses through the UI and synchronize my licenses. Click on Administration in the upper right corner, then click on Licenses Management. Click the Upload button and re-upload the license zip file (in some cases I have heard that expired licenses needed to be removed first). Now click the Synchronize button and OK.  You should now be able to use all licenses again.

[caption id="attachment_2725" align="aligncenter" width="1315"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/10/vipr-srm-license-syncronize.png"><img class="size-full wp-image-2725" src="http://www.virtxpert.com/wp-content/uploads/2014/10/vipr-srm-license-syncronize.png" alt="EMC ViPR SRM Administration &gt;&gt; Licenses Management" width="1315" height="391" /></a> EMC ViPR SRM Administration &gt;&gt; Licenses Management[/caption]