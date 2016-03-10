---
ID: 3042
post_title: 'Configure vRealize Permissions &#8211; vRealize Automation Series Part 7'
author: Jonathan Frappier
post_date: 2014-11-18 08:00:27
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/configure-vrealize-permissions-vrealize-automation-series-part-7/
published: true
dsq_thread_id:
  - "3237501620"
---
[display-posts category="vRA Home Lab" display-posts posts_per_page="15"]

With the installation out of the way, we can now start to configure permissions beyond the administrator@vsphere.local account so we can log in and actually do cloudy things.  First though, lets create a couple of accounts in active directory so we can drive home the different roles.  Log into your DC and create two user accounts - tenantadmin and iaasadmin.

With the two AD accounts crated, head back to the vCloud Automation Center / vRealize Automation appliance log in page and log in as administrator@vsphere.local
<ul>
	<li>Click on Tenants &gt;&gt; vsphere.local &gt;&gt; administrators</li>
	<li>In the Tenant administrators search box type tenantadmin, click the magnifying glass icon to search and click on tenantadmin@vxprt.local</li>
	<li>In the Infrastructure administrators search box type iaasadmin, click the magnifying glass icon to search and click on iaasadmin@vxprt.local</li>
	<li>Both user accounts should be pictured, similar to below; click the Update button</li>
</ul>
[caption id="attachment_3052" align="aligncenter" width="1275"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/vcac-add-accounts-default-tenant.png"><img class="size-full wp-image-3052" src="http://www.virtxpert.com/wp-content/uploads/2014/11/vcac-add-accounts-default-tenant.png" alt="vCloud Automation Center / vRealize Automation add users default tenant" width="1275" height="417" /></a> vCloud Automation Center / vRealize Automation add users default tenant[/caption]
<h3>vRealize Infrastructure administrator role</h3>
<ul>
	<li>Log out of the appliance and log back in as iaasadmin</li>
</ul>
<blockquote>Remember why we don't need the @vxprt.local here? - thats right we set the default identity source to be our domain in vSphere SSO, and we are using that same SSO for vCloud Automation Center / vRealize Automation</blockquote>
<ul>
	<li>Notice as the Infrastructure administrator we have only 3 tabs along the top, and we can no longer manage the identity source because this user does not have permission for that.</li>
	<li>Click on Infrastructure, notice the various items as well as that little error message that popped up.  That is because we have only licensed the appliance thus far, we still need to license the IaaS components</li>
	<li>Click on Administration &gt;&gt; Licensing, click the Add a License link at the top, enter your license key and click the OK button</li>
	<li>Click on back to Infrastructure and explore the different menus such as Groups, Blueprints and Monitoring and see what type of information and options are available in each</li>
</ul>
<h3>vRealize Tenant administrator role</h3>
<ul>
	<li>Log out of the appliance and log back in as tenantadmin</li>
	<li>Notice that while there is an Infrastructure tab, there is much less available to the tenant admin user</li>
	<li>There is, however, much more available in the administration menu</li>
	<li>Explore the various options available to the tenant admin</li>
</ul>
We will cover the roles a bit more in-depth in future posts as we configure vRealize Automation.  To quench your thirst for all permission things here is a little cheat sheet for what menus and options are available to the tenant and IaaS administrative users, I know I forget easily.  With the basic permissions out of the way, it's time to start setting up the other required pieces such as business groups and endpoints, in the next post of course!
<h3>vRealize Automation tenant and infrastructure administrator menu cheat sheet</h3>
<!--more-->

[caption id="attachment_3053" align="aligncenter" width="800"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/vra-tenant-v-iaas-admin.png"><img class="size-full wp-image-3053" src="http://www.virtxpert.com/wp-content/uploads/2014/11/vra-tenant-v-iaas-admin.png" alt="vRealize tenant and infrastructure admin menu cheatsheet" width="800" height="1675" /></a> vRealize tenant and infrastructure admin menu cheat sheet[/caption]