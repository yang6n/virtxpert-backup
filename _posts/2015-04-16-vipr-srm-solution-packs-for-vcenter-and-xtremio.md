---
ID: 3685
post_title: >
  ViPR SRM Solution Packs for vCenter and
  XtremIO
author: Jonathan Frappier
post_date: 2015-04-16 08:00:20
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vipr-srm-solution-packs-for-vcenter-and-xtremio/
published: true
dsq_thread_id:
  - "3686368301"
---
*<em>*Disclaimer: I am an EMC employee, this post was not sponsored or in any way required by my employer, it is my experience getting to know this particular product.**</em>

In my last two posts I touched on what ViPR SRM can do, and the quick installation.

[display-posts category="ViPR SRM Series" display-posts posts_per_page="15"]

With the ViPR SRM installation out of the way, it's time to start adding Solution Packs. Solution Packs are use to connect to various systems, such as VMware vCenter, so ViPR SRM can collection information about virtual machines, ESXi hosts, datastores, and HBA's. Additionally, you connect ViPR SRM to your switches and storage for, quite literally, an end to end view of your environment.
<ul>
	<li>First, log into <strong>http://&lt;vipr srm IP or DNS&gt;:58080/APG</strong> and click on Administration (upper right corner)</li>
	<li>Once you are in the Administration interface, click on Centralized Management on the left navigation menu, a new window or tab will open</li>
	<li>In the new window, click on Solution Pack Center (back in the upper right corner)</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-solution-packs.jpg"><img class=" size-full wp-image-3689 aligncenter" src="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-solution-packs.jpg" alt="vipr-srm-solution-packs" width="811" height="599" /></a>
<ul>
	<li>In the search box in the upper right corner, type vCenter to filer the results, and click on VMware vCenter</li>
	<li>When the vCenter box opens, click on the install button.</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2015/04/virp-srm-vcenter-install-pack.jpg"><img class="aligncenter size-full wp-image-3690" src="http://www.virtxpert.com/wp-content/uploads/2015/04/virp-srm-vcenter-install-pack.jpg" alt="virp-srm-vcenter-install-pack" width="813" height="535" /></a>
<ul>
	<li>Follow the wizard and review the options; it's a basic wizard - next, next; if using PowerPath click Enable the Host PowerPath alerts for example and click next, next, next, next, and finally install. ViPR SRM will go through and install the selected components.</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-solutions-pack-vcenter-installed.jpg"><img class="aligncenter size-full wp-image-3693" src="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-solutions-pack-vcenter-installed.jpg" alt="vipr-srm-solutions-pack-vcenter-installed" width="813" height="392" /></a>
<ul>
	<li>Click OK. Repeat the above steps for your environment. At the very least, the Storage Compliance pack is useful. Here is the EMC XtremIO solution pack which I will be installing to show examples from.</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-solution-pack-xtremio.jpg"><img class="aligncenter size-full wp-image-3694" src="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-solution-pack-xtremio.jpg" alt="vipr-srm-solution-pack-xtremio" width="812" height="276" /></a>
<ul>
	<li>With the solution packs installed, we need to provide each some information. Expand Discovery Center in the left navigation menu, expand Devices Management and click on VMware vCenter</li>
	<li>Click on the Add new device... button and fill in the information to connect to vCenter. I suggest using dedicated accounts for external services, so for example here is my app_viprsrm user account which has admin privileges in vCenter. Click the test button to confirm the account has access, and then click OK. Repeat for multiple vCenters or the storage in your environment you added a pack for.</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2015/04/info.png"><img class="alignleft  wp-image-3680" src="http://www.virtxpert.com/wp-content/uploads/2015/04/info.png" alt="info" width="48" height="48" /></a>

Don't forget to click the Save button!

<a href="http://www.virtxpert.com/wp-content/uploads/2015/04/save.png"><img class="aligncenter size-full wp-image-3701" src="http://www.virtxpert.com/wp-content/uploads/2015/04/save.png" alt="save" width="519" height="179" /></a>

<a href="http://www.virtxpert.com/wp-content/uploads/2015/04/vcenter-vipr-srm-creds.jpg"><img class="aligncenter size-full wp-image-3697" src="http://www.virtxpert.com/wp-content/uploads/2015/04/vcenter-vipr-srm-creds.jpg" alt="vcenter-vipr-srm-creds" width="812" height="380" /></a>Depending on your environment, you may also want to add your FC switches as well. Switch monitoring is done by adding a Solution pack for your switch, and connecting to it via SNMP. While logged in as admin go to http://&lt;viprsrm IP or DNS&gt;:58080/device-discovery, click Collectors, click New Collector, and Save. This will add an SNMP collector to the local VM. Once the collector is added click on Devices, New Device, and fill in the appropriate information.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-snp-device-discovery.png"><img class="aligncenter size-full wp-image-3708" src="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-snp-device-discovery.png" alt="vipr-srm-snp-device-discovery" width="665" height="374" /></a>

With all switches added, click the check box next to it, and click the magnifying glass icon under actions; this will discover the switch.

ViPR SRM will now start collecting data, to expidite the process click on Scheduled Tasks (left navigation menu), check box for the "import-properties-default" task, and click the Run Now button. If you return to the User Interface (back in the Administration page, click User Interface) and go to Explore &gt;&gt; Hosts you should see your vCenter hosts as well as virtual machines.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-vcenter-hosts.png"><img class="aligncenter size-full wp-image-3703" src="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-vcenter-hosts.png" alt="vipr-srm-vcenter-hosts" width="1288" height="202" /></a>

If you navigate to Explore &gt;&gt; Storage you should also see the storage devices you added.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-storage.png"><img class="aligncenter size-full wp-image-3704" src="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-storage.png" alt="vipr-srm-storage" width="1308" height="114" /></a>

With the configuration out of the way, I can now start to explore my environment with the various reports available, which I will do in the next post!