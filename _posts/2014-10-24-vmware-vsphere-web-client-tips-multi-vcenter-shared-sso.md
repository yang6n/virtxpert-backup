---
ID: 2717
post_title: 'VMware vSphere Web Client Tips &#8211; Multi vCenter Shared SSO'
author: Jonathan Frappier
post_date: 2014-10-24 15:34:52
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vmware-vsphere-web-client-tips-multi-vcenter-shared-sso/
published: true
dsq_thread_id:
  - "3161312496"
---
A great feature of the vSphere Web Client comes when you have two separate vCenter servers that share a common Single Sign-on  (SSO) server.  In this scenario you can see all vCenter servers connected to the shared SSO server - logging into the vSphere Web Client for either vCenter (or having a single web server running the Web Client bits) you can see any/all vCenter servers using the shared SSO server.

As you can see in the screenshot below, I have VC1 and VC2, along with all of the resources you would expect to have access to (<a title="VMware vSphere Web Client Tips – Love Related Objects Tab" href="http://www.virtxpert.com/vmware-vsphere-web-client-tips-love-related-objects-tab/">including the awesome related objects tab</a>) but I only have to log into one client!

[caption id="attachment_2720" align="aligncenter" width="802"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/10/vsphere-web-client-shared-sso-multiple-vcenter.png"><img class="size-full wp-image-2720" src="http://www.virtxpert.com/wp-content/uploads/2014/10/vsphere-web-client-shared-sso-multiple-vcenter.png" alt="Multiple vCenter Servers in the vSphere Web Client with a shared SSO server" width="802" height="392" /></a> Multiple vCenter Servers in the vSphere Web Client with a shared SSO server[/caption]