---
ID: 3151
post_title: 'Creating Entitlements &#8211; vRealize Automation Series Part 15'
author: Jonathan Frappier
post_date: 2014-11-22 13:00:21
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/creating-entitlements-vrealize-automation-series-part-15/
published: true
dsq_thread_id:
  - "3252581042"
---
[display-posts category="vRA Home Lab" display-posts posts_per_page="15"]

Home stretch, 15 posts and we are about to see our first catalog item published!  Lets get going and create the entitlement which is how we define what can be done in vRealize Automation / vCloud Automation Center
<ul>
	<li>Log in as tenantadmin</li>
	<li>Click Administration &gt;&gt; Catalog Management &gt;&gt; Entitlements</li>
	<li>Click the Add button and fill in the information as follows</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/vra-entitlement.png"><img class="aligncenter size-full wp-image-3148" src="http://www.virtxpert.com/wp-content/uploads/2014/11/vra-entitlement.png" alt="vra-entitlement" width="1047" height="382" /></a>
<ul>
	<li>Click the Next button</li>
	<li>Click the plus sign next to Entitled Services, select Clone Linux Template and click OK</li>
	<li>Click the plus sign next to Entitled Catalog items, select CentOS template and click OK</li>
	<li>Click the plus sign next to Entitled Actions, Select Machine from the pull down and chose all of the items, Select Virtual Machine from the pull down and select Destroy; click OK</li>
	<li>Click the Add button</li>
</ul>
Log out as tenantadmin and log back in as luke, you should now see your vSphere template, which is now a vRealize Automation / vCloud Automation Center blueprint published!

<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/hooray.png"><img class="aligncenter size-full wp-image-3149" src="http://www.virtxpert.com/wp-content/uploads/2014/11/hooray.png" alt="hooray" width="722" height="381" /></a>