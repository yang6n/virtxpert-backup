---
ID: 3068
post_title: 'Adding Business Groups &#8211; vRealize Automation Series Part 10'
author: Jonathan Frappier
post_date: 2014-11-20 07:00:49
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/adding-business-groups-vrealize-automation-series-part-10/
published: true
dsq_thread_id:
  - "3244798061"
---
[display-posts category="vRA Home Lab" display-posts posts_per_page="15"]

We are cruising right along here in our vRealize Automation / vCloud Automation Center setup.  So far we have everything installed, permissions assigned, a vCenter endpoint added and fabric group created with the cluster from our vCenter server.  Now its time to setup business groups.  Business groups are just a logical group of users, this may be done per department, per project or per external customer.  We can publish catalog items to business groups, so when planning your business groups think of the things certain groups may or may not need.  For example you may want a business group for your QA department that only has access to builds that are currently being tested so they do not chose the wrong version to deploy, or not want finance see HRs catalog items.   Consider helpdesk users, you may want to publish certain catalog items for them to do certain tasks like create AD users and groups through vCenter Orchestrator workflows or PowerShell scripts - the possibilities are seemingly endless.

Remember when I said installing it was the easy part - wasn't kidding - all the work for vRealize Autoamtion / vCloud Automation Center comes in the application configuration.

A couple of things before we get started with business groups however; lets create some users in our AD to mimic end users and if you recall from my last post we also need to create a machine prefix as it is a required field to create the business group - no defined prefix, no savie business group.
<ul>
	<li>Log into your DC and create several users; as a Walking Dead fan I used Rick, Carl, Tyreese and Daryl as my users.  All of these users were added to a group called vraGeorgia which will be assigned to my business group.  Create a 2nd group and set of users; in my case I went Star Wars related.</li>
</ul>
The fabric administrator creates machine, in the last post I assigned this role to the iaasadmin user, if you are still logged in from the last post you will need to log out and back in again to have the new permissions assigned.  Once logged in click on the Infrastructure tab &gt;&gt; Blueprints.  Recall from a previous post that the user with the IaaS admin role only had an menu item under Blueprints called Instance Types, now there are several - take a moment to look at each, when you are ready click on Machine Prefixes.

[caption id="attachment_3073" align="aligncenter" width="1331"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/vra-fabric-admin-menu.png"><img class="size-full wp-image-3073" src="http://www.virtxpert.com/wp-content/uploads/2014/11/vra-fabric-admin-menu.png" alt="vRealize Automation / vCloud Automation Center Fabic Admin Blueprint menu" width="1331" height="389" /></a> vRealize Automation / vCloud Automation Center Fabic Admin Blueprint menu[/caption]
<ul>
	<li>Click on New Machine Prefix</li>
	<li>Fill in the prefix name, number of digits and next number.  For example Dead, 2, 1 would create the first prefix as dead01 because my prefix is dead, I've added 2 digits to that and set the next number to 1.  If, for example, I set it to zombie, 3 and 75 my next prefix created would be zombie075.</li>
	<li>When finished, click the green circle with the check mark.  I have created two prefixes, dead for my vraGeorgia group and boom for vraAlderaan</li>
</ul>
[caption id="attachment_3074" align="aligncenter" width="1044"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/vra-machine-prefix.png"><img class="size-full wp-image-3074" src="http://www.virtxpert.com/wp-content/uploads/2014/11/vra-machine-prefix.png" alt="vRealize Automation / vCloud Automation Center New Machine Prefix" width="1044" height="192" /></a> vRealize Automation / vCloud Automation Center New Machine Prefix[/caption]
<ul>
	<li>Now that both machine prefixes are saved, log out of vRealize Automation / vCloud Automation Center and log in as tenantadmin</li>
	<li>To create a business group, click on the Infrastructure tab &gt;&gt; Groups &gt;&gt; Business Groups (I feel like it would make more sense for this to be under administration, but its not so..)</li>
	<li>Click on New Business Group and fill in the information, if you are using the same names as me, this is what it should look like when finished.  Use the ellipse to select the machine prefixes we just created and the magnifying glass icon to search for the names and groups.</li>
	<li>I<a href="http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&amp;cmd=displayKC&amp;externalId=2090803" target="_blank">n vCloud Automation Center 6, there was a bug that would not allow you to search for AD groups</a>, I am sad to see this is still present in 6.1; <a href="http://pubs.vmware.com/vCAC-61/index.jsp?topic=%2Fcom.vmware.vcac.iaas.all.doc%2FGUID-CDB547F8-0529-4270-891F-B04F5C9E8816_copyV1.html" target="_blank">according to the documentation groups should be accepted here</a>.  Type the group name in below the search box, its not very obvious but will work</li>
</ul>
&nbsp;

[caption id="attachment_3079" align="aligncenter" width="838"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/vra-create-business-group-b.png"><img class="size-full wp-image-3079" src="http://www.virtxpert.com/wp-content/uploads/2014/11/vra-create-business-group-b.png" alt="vRealize Automation / vCloud Automation Center Create Business Group" width="838" height="641" /></a> vRealize Automation / vCloud Automation Center Create Business Group[/caption]
<ul>
	<li>When finished, click the OK button and repeat for your second group</li>
</ul>
Here we are - business groups and prefixes created, next up - creating reservations for our business groups.