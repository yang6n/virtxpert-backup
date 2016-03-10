---
ID: 2925
post_title: 'Workstation Home Lab Wrap-Up &#8211; On to vRealize Automation'
author: Jonathan Frappier
post_date: 2014-11-13 07:00:25
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/workstation-home-lab-wrap-up-on-to-vrealize-automation/
published: true
dsq_thread_id:
  - "3220379434"
---
[display-posts category="Lab Series" display-posts posts_per_page="15"]

That is a wrap on getting the basics of a home lab up and running in VMware Workstation.  Within Workstation we have a working Windows 2012 Domain Controller, two virtual ESXi hosts both capable of running nested 64-bit virtual machines thanks to the RVI support in the processor of the <a title="8-Core, 32GB RAM, 360GB Flash, 3TB, Dual-NIC Home Lab Part List" href="http://www.virtxpert.com/8-core-32gb-ram-360gb-flash-2tb-dual-nic-home-lab-part-list/">8-core home lab system build</a> and vCenter running.  In vCenter we have our datacenter and cluster created with both virtual ESXi hosts added.  The cluster has DRS enabled, a virtual distributed switch setup with both hosts attached and port group and VMkernel interface setup and running and demoed using vMotion to move a virtual machine from one host to another.  Not bad for 4 virtual machines barely consuming any memory on the host computer!

All that though, was leading up to this; setting up vRealize Automation and Application Services.  In my next series I will go over some of the basics of getting vRealize Automation setup in your home lab so you can start to get a feel for the various roles, requirements and setup.  Here is some handy reading in the interim (ignore anything that says vSphere SSO can't be used)
<ul>
	<li><a href="https://www.vmware.com/files/pdf/products/vmware_vrealize_cloud_management_platform_getting_started_guide.pdf" target="_blank">vRealize Suite Getting Started</a></li>
	<li><a href="http://www.vmware.com/files/pdf/products/vCloud/VMware-vCloud-Automation-Center-61-Reference-Architecture.pdf" target="_blank">vCloud Automation Center 6.1 Reference Architecture</a></li>
	<li><a href="http://www.vmware.com/pdf/vcloud-automation-center-61-support-matrix.pdf" target="_blank">vCloud Automation Center Support Matrix</a></li>
	<li><a href="http://www.vmware.com/files/pdf/products/vCloud/VMW-vRealize-Automation-61-Deployment-Guide-HA-Configurations.pdf" target="_blank">Using vSphere SSO with vCloud Automation Center 6.1</a></li>
</ul>
Thank you for following along with the home lab series setup, I know there may be a few holes but again the goal was to get this setup to have an environment as the foundation to test other tools.