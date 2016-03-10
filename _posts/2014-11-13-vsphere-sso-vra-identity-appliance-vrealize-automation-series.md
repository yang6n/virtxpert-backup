---
ID: 2918
post_title: 'vSphere SSO or vRA Identity Appliance &#8211; vRealize Automation Series Part 1'
author: Jonathan Frappier
post_date: 2014-11-13 08:00:06
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vsphere-sso-vra-identity-appliance-vrealize-automation-series/
published: true
dsq_thread_id:
  - "3220540827"
---
[display-posts category="vRA Home Lab" display-posts posts_per_page="15"]

One of the first steps generally in setting up vCloud Automation Center or vRealize Automation would be to deploy the identity appliance, however you can also use an existing vSphere SSO implementation.  In fact, VMware has gone so far as to publish a technical white paper on how to configure <a href="http://www.vmware.com/files/pdf/products/vCloud/VMW-vRealize-Automation-61-Deployment-Guide-HA-Configurations.pdf" target="_blank">vSphere SSO for high availability for use with vCloud Automation</a>, now I won't be doing that just yet but know its possible.

Here is the support matrix for currently supported authentication providers for vCloud Automation Center 6.1, as you can see vSphere SSO 5.5 U2b, U1c and U1b are all certified and supported.  A quick check on the vCenter server version (vSphere Web Client &gt;&gt; vCenter &gt;&gt; vCenter Servers &gt;&gt; vxprt-vc01; Version Information portlet) shows that the vCenter Server Appliance that was deployed is 5.5.0 build 2183111; <a href="http://kb.vmware.com/kb/1014508" target="_blank">cross reference on the VMware KB (1014508)</a> shows that the build number correlates to vSphere 5.5 Update 2b - certified to work with vCloud Automation Center / vRealize Automation 6.1

[caption id="attachment_2932" align="aligncenter" width="680"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/vcac-vsphere-sso-support-matrix.png"><img class="size-full wp-image-2932" src="http://www.virtxpert.com/wp-content/uploads/2014/11/vcac-vsphere-sso-support-matrix.png" alt="vCloud Automation Center with vSphere SSO support matrix" width="680" height="350" /></a> vCloud Automation Center with vSphere SSO support matrix[/caption]

Given we are running in a lab environment with limited resources, I am going to go ahead and use the vSphere SSO implementation bundled with the vCenter Server Appliance.  If you would like more information on deploying the vCloud Automation Center / vRealize Automation Identity Appliance, <a href="http://emadyounis.com/vrealize-automation/vrealize-automation-6-1-formally-vcloud-automation-center-identity-appliance-deployment-configuration/" target="_blank">check out Emad Younis' post on his blog</a>.

Whether or not to use your vSphere SSO implementation for production deployments would have several factors (if resource constraint is one of them please talk to your boss about why you're deploying vRA in the first place).  For enterprise deployments it may make sense to leverage an existing vSphere SSO deployment since your employees are likely to share a common Active Directory already.  Yes it becomes a single point of failure for both vCenter and vCloud Automation Center / vRealize Automation (unless you deploy the HA solution referenced above), but if SSO for vSphere is down, or the identity appliance is down, you're still not getting much done until that is restored.  It may make sense to simplify support in that regard.

For organizations supporting external users, you may want to separate the authentication domains so they are not co-mingled, creating a separate security domain.  Another reason may be politics - maybe one group manages vCenter and another vCloud - if that is the case, again please talk to your boss.

I'd love to hear some of your pros and cons for separate identity appliance or using vSphere SSO.  Up next we'll deploy the vCloud Automation Center / vRealize Automation appliance.