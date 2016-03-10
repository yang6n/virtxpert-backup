---
ID: 2632
post_title: 'vCAC / vRA Tenant Identity Store &#8211; User and Group search DN base'
author: Jonathan Frappier
post_date: 2014-09-24 15:25:26
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vcac-vra-tenant-identity-store-user-group-search-dn-base/
published: true
dsq_thread_id:
  - "3050460698"
---
I am in a course this week and a question came up about how to configure the Group and User search base DN and its effect on access within vCAC / vRA.  Ultimately permission will be granted as a combination of both fields.  First and foremost when configuring vCloud Automation Center for vRealize Automation tenants this will control which users or groups you can assign tenant administrator or infrastructure administrator roles.  Let's look at some examples; if my domain is test.lab and I set my User and Group search base DN to dc=test,dc=lab I will be able to assign either of those roles to any user or group in the entire Active Directory, regardless of what organization unit or container they may be in.  Easy enough, but that starts to open things up pretty wide.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/09/vcac-is-tld.png"><img class="size-full wp-image-2633 aligncenter" src="http://www.virtxpert.com/wp-content/uploads/2014/09/vcac-is-tld.png" alt="vcac-is-tld" width="1186" height="729" /></a>

&nbsp;

In the real world I am likely to have an OU for groups or in a large enough AD groups spread across multiple OUs so you'll need to consider your AD structure to set the base DN appropriately.  For example if you have ou=groups,dc=test,dc=lab as your Group search base DN but you have some groups created in ou=sales,dc=test,dc=lab you will not be able to assign permissions to the groups in the Sales OU.

You may have noticed from the screenshot that only the Group search base DN is required, personally I prefer to assign permissions to groups so that is great - what happens if I leave the User search base DN empty and set a more restrictive Group search base DN such as ou=groups,dc=test,dc=lab like so?

<!--more-->

<a href="http://www.virtxpert.com/wp-content/uploads/2014/09/vcac-is-groupou-only.png"><img class="size-full wp-image-2636 aligncenter" src="http://www.virtxpert.com/wp-content/uploads/2014/09/vcac-is-groupou-only.png" alt="vcac-is-groupou-only" width="552" height="226" /></a>

&nbsp;

In this scenario, <strong>BOTH</strong> the user account, and group would need to be in the same OU; not something I'd typically do.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/09/vcac-incorrect-username.png"><img class="size-full wp-image-2638 aligncenter" src="http://www.virtxpert.com/wp-content/uploads/2014/09/vcac-incorrect-username.png" alt="vcac-incorrect-username" width="758" height="180" /></a>

What I am likely to do given this scenario is to set my user search base more broadly and be more restrictive on my Group search base so that only specific groups can be assigned permission in vCAC - let's look at that scenario.  I have created an OU called org-users with a sub-OU called sales and an OU called org-groups.  I set the Group search base DN to ou=org-groups,dc=test,dc=lab and the User search base DN to ou=org-users,dc=test,dc=lab.

In the org-groups OU I have a group called vcac-admins.  In the Sales OU (which is under org-users) I have a user called test and a group called sales.  Since Group search base DN is set to org-groups I cannot assign the sales group either tenant administrator or infrastructure administrator roles.  I can however assign my vcac-admins group permission since that falls within the Group search base.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/09/vcac-permissions.jpg"><img class="size-full wp-image-2641 aligncenter" src="http://www.virtxpert.com/wp-content/uploads/2014/09/vcac-permissions.jpg" alt="vcac-permissions" width="562" height="199" /></a>

&nbsp;

Now, so long as my test user falls within the scope of the User search base - in this case the sub-OU called Sales under org-users and is a member of the vcac-admins group (even though the group and user are not in the same OU like I would need if I did not define the User base search DN field.)

<a href="http://www.virtxpert.com/wp-content/uploads/2014/09/test-lab-ad-org.png"><img class="size-medium wp-image-2643 aligncenter" src="http://www.virtxpert.com/wp-content/uploads/2014/09/test-lab-ad-org-300x285.png" alt="test-lab-ad-org" width="300" height="285" /></a>

Now I can log in with the expected permissions.  In short, if you leave the User search base DN blank, your user accounts need to fall within the same scope as the Group search base DN.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/09/test-user-logged-in.png"><img class="size-full wp-image-2642 aligncenter" src="http://www.virtxpert.com/wp-content/uploads/2014/09/test-user-logged-in.png" alt="test-user-logged-in" width="746" height="389" /></a>