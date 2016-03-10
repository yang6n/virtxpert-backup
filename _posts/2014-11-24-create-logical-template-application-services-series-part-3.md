---
ID: 3164
post_title: 'Create a Logical Template &#8211; Application Services Series Part 3'
author: Jonathan Frappier
post_date: 2014-11-24 08:30:32
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/create-logical-template-application-services-series-part-3/
published: true
dsq_thread_id:
  - "3258006068"
---
[display-posts category="Application Services Lab" display-posts posts_per_page="15"]

We are making good progress with Application Services, up next is creating a logical template, which will be part of our deployment environment, which is part of our cloud provider, which is ultimately vRealize Automation Center, which runs on vCenter!  If you are not logged into Application Services, log in as luke now (assuming your usernames are the same as mine).
<ul>
	<li>Click on the Deployment Environment pull down (recall that menu changes context) and click on Chose Logical Templates</li>
	<li>Click the Logical Template that matches your virtual machine template.  My CentOS template is 6.6 but I have selected CentOS6.4 64-bit</li>
	<li>Click on the box for the logical template version 1.0.0</li>
	<li>In the upper right corner click the Edit button</li>
	<li>Click on the green plus icon next to Cloud Template Mapping</li>
	<li>In the Cloud Provider pull down, select the cloud provider we previously created</li>
	<li>In the Cloud Template pull down, select the cloud template we previously crated</li>
</ul>
Your screen should look similar to what is below.  Click the Save button.  Much like we have done before, the logical template simply combines other items and groups them together - in this case the vSphere template we created, which is a vRealize Automation blueprint, which is added as a template to the Application Services Cloud Provider which is part of a deployment environment.

[caption id="attachment_3166" align="aligncenter" width="1678"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/apps-logical-template.png"><img class="size-full wp-image-3166" src="http://www.virtxpert.com/wp-content/uploads/2014/11/apps-logical-template.png" alt="VMware Application Services create Logical Temlate" width="1678" height="455" /></a> VMware Application Services create Logical Temlate[/caption]

&nbsp;