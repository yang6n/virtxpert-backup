---
ID: 3670
post_title: Installing ViPR SRM
author: Jonathan Frappier
post_date: 2015-04-13 14:42:23
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/installing-vipr-srm/
published: true
dsq_thread_id:
  - "3678737212"
---
<em>*Disclaimer: I am an EMC employee, this post was not sponsored or in any way required by my employer, it is my experience getting to know this particular product.**</em>

In <a title="Getting to know ViPR SRM" href="http://www.virtxpert.com/getting-to-know-vipr-srm/">my last ViPR SRM post</a>, I introduced you to some of the features if you were not already aware of them. In this post, I will look at installing ViPR SRM 6.5.2. I downloaded ViPR SRM from support.emc.com; while I am an EMC employee, I logged into the support site with my personal email account to download the files. Once logged in, search for ViPR SRM and click on the downloads menu, as I mentioned I will be going with the vApp option versus a binary installation.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-search-support.png"><img class="aligncenter  wp-image-3671" src="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-search-support.png" alt="vipr-srm-search-support" width="848" height="549" /></a>

Once downloaded, extract the content of the zip file - you'll have 2 OVF's. One is the 4 VM vApp I mentioned in my last post, the other, a 1VM vApp useful for lab and evaluation purposes. Given I have limited resources in my home lab, I will be deploying the 1 VM vApp.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/04/info.png"><img class="alignleft  wp-image-3680" src="http://www.virtxpert.com/wp-content/uploads/2015/04/info.png" alt="info" width="50" height="50" /></a>

Important note here, you will need to deploy the OVF to vCenter, not a stand-alone ESXi host as some of the OVF properties will not be exposed properly, causing the deployment to fail.

Follow the OVF deployment wizard, when prompted select the All-In-One configuration:

<a href="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-all-in-one-ovf.jpg"><img class="aligncenter size-full wp-image-3678" src="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-all-in-one-ovf.jpg" alt="vipr-srm-all-in-one-ovf" width="954" height="557" /></a>

By default, the VM deploys with 4 vCPU - adjust according to your lab, I have set mine to 2, 16GB RAM and removed the reservation (performance here would not be ideal obviously, but this is for lab purposes only). Once the OVF has been deployed, you should be able to log into <strong>http://&lt;viprsrm DNS or IP&gt;:58080/APG. </strong>Login as admin/change me to access ViPR SRM.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-UI.jpg"><img class="alignleft size-full wp-image-3682" src="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-UI.jpg" alt="vipr-srm-UI" width="1632" height="650" /></a>

sadfsadf

By default, you are in the "User" interface, if you click on "Administration" in the upper right corner, you will go to the administration screen. Go ahead and click on Administration &gt;&gt; Centralized Management (on the left nav menu) &gt;&gt; License Management (also on the left nav menu). As you can see you have a 30 day trial license to test out ViPR SRM.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-trial-license.jpg"><img class="alignleft size-full wp-image-3683" src="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-trial-license.jpg" alt="vipr-srm-trial-license" width="1376" height="497" /></a>

Close the license window/tab. Notice where the "Administration" menu was, you now see a "User Interface" menu, this will (like the administration link did) take you to the User interface (where you initially landed when you logged in.

In the next post, I will look at connecting ViPR SRM to vCenter and, in my case, XtremIO.