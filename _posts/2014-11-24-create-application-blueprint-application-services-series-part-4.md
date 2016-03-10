---
ID: 3168
post_title: 'Create an Application Blueprint &#8211; Application Services Series Part 4'
author: Jonathan Frappier
post_date: 2014-11-24 11:00:49
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/create-application-blueprint-application-services-series-part-4/
published: true
dsq_thread_id:
  - "3258472680"
---
[display-posts category="Application Services Lab" display-posts posts_per_page="15"]

Application Services is configured, now its time to create and publish an Application Blueprint.  During the installation I chose to install the sample content so I would have some an existing application blueprint available; I am going to take advantage of that sample content for my lab and edit one of the existing applications.  If you are not already, log into Application Services as luke and use the pull down menu in the upper right to change to the Application view.
<ul>
	<li>Click on jPetStore</li>
	<li>In the Application Versions pane, click on the 1.0.0 version</li>
	<li>Click on the blueprint</li>
</ul>
[caption id="attachment_3170" align="aligncenter" width="908"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/apps-jpetstore-blueprint.png"><img class="size-full wp-image-3170" src="http://www.virtxpert.com/wp-content/uploads/2014/11/apps-jpetstore-blueprint.png" alt="VMware Application Services jPetStore blueprint" width="908" height="308" /></a> VMware Application Services jPetStore blueprint[/caption]
<ul>
	<li>Click on CentOS32 v6.3</li>
	<li>Drag the CentOS64 v6.4  logical template into the application builder</li>
	<li>Drag the components from jPetStore to the CentOS64 operating sytem</li>
	<li>Delete the CentOS32 item and click the Save button</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/apps-new-os-blueprint-b.png"><img class="aligncenter size-full wp-image-3173" src="http://www.virtxpert.com/wp-content/uploads/2014/11/apps-new-os-blueprint-b.png" alt="apps-new-os-blueprint-b" width="347" height="353" /></a>
<ul>
	<li>Click the Deploy button in the upper right corner</li>
	<li>Name the new deployment profile and select the business group; Click the Deploy button</li>
	<li>Select the Deployment Environment, click the map details button then click Next</li>
	<li>Click into the hostname field and enter a name then click Next</li>
	<li>Review the execution plan and click next</li>
	<li>Click the publish button, name the item and click OK</li>
</ul>
Now we need to provide entitlements in vRealize Automation; log into vRA as tenantadmin:
<ul>
	<li>Click on the Administration tab &gt;&gt; Catalog Management &gt;&gt; Catalog Items</li>
	<li>Click on jPetStore (or whatever you named it), add it to the Clone Linux Template service and click Update</li>
	<li>Log out and log back in as luke</li>
	<li>Click on the Catalog tab; you should now have your basic VM template catalog item and the jPetStore catalog item.</li>
</ul>
[caption id="attachment_3174" align="aligncenter" width="1657"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/apps-published-in-vra.png"><img class="size-full wp-image-3174" src="http://www.virtxpert.com/wp-content/uploads/2014/11/apps-published-in-vra.png" alt="Application Services Blueprint published in vRealize Automation Catalog" width="1657" height="398" /></a> Application Services Blueprint published in vRealize Automation Catalog[/caption]

You are now able to request Application Services blueprints through vRealize Automation!

This was a pretty basic example, and not likely to be replicated in real world use cases.  In fact, I have seen projects to automate the installation of software take upwards of 6 months to complete. Remember with Application Services we have moved beyond installing an application and simply cloning it, as that doesn't work or scale for many applications - they require connection strings, network information etc..  What you are doing now is leveraging a release engineering or application automation tool so building a solid Application Services blueprint will go through its own SDLC.