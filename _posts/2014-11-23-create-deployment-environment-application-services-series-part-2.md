---
ID: 3158
post_title: 'Create a Deployment Environment &#8211; Application Services Series Part 2'
author: Jonathan Frappier
post_date: 2014-11-23 11:00:48
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/create-deployment-environment-application-services-series-part-2/
published: true
dsq_thread_id:
  - "3255235091"
---
[display-posts category="Application Services Lab" display-posts posts_per_page="15"]

In my last post we created the Cloud Provider, now we need to setup a Deployment Environment.  We are really setting up logical constructs here to map to to services and resources we already have.  So far we mapped a Cloud Provider to vRealize Automation Center and to our business group.  Now we are going to create a deployment environment for Application Services that maps to the cloud provider we created, that maps to vRealize resources... If you are not already, log in as Luke and perform the following.
<ul>
	<li>Click on the Cloud Provider pull down menu in the top right corner (short aside, that menu name will change to show the context you are currently working in so if you logged out this may be different) and select Deployment Environments</li>
	<li>Click the Create A Deployment Environment button</li>
	<li>Provide a name</li>
	<li>Select a Cloud Provider from the pull down menu</li>
	<li>Click the Select button to select a reservation policy; click OK then Save</li>
</ul>
You screen should look similar to what is pictured below.  Since Application Services is now part of vRealize Automation, most of the work we are doing here will map to what has already been configured in vRealize Automation.  Next we need to create a logical template.

[caption id="attachment_3160" align="aligncenter" width="1017"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/apps-cloud-provider.png"><img class="size-full wp-image-3160" src="http://www.virtxpert.com/wp-content/uploads/2014/11/apps-cloud-provider.png" alt="VMware Application Services Create Cloud Provider" width="1017" height="689" /></a> VMware Application Services Create Cloud Provider[/caption]