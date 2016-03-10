---
ID: 3532
post_title: >
  Error during deployment of vCenter
  Server Appliance or Platform Services
  Controller following error
author: Jonathan Frappier
post_date: 2015-02-10 08:45:23
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/error-deployment-vcenter-server-appliance-platform-services-controller-following-error/
published: true
dsq_thread_id:
  - "3502806956"
---
Scenario: You try to install the VMware vCenter Server Appliance (VCSA) or Platform Services Controller but receive an error during the installation. After correcting the problem during installation you attempt to re-install the appliance but receive the following error message:

[caption id="attachment_3534" align="aligncenter" width="873"]<a href="http://www.virtxpert.com/wp-content/uploads/2015/02/virtual-machine-already-exists.png"><img class="size-full wp-image-3534" src="http://www.virtxpert.com/wp-content/uploads/2015/02/virtual-machine-already-exists.png" alt="Virtual Machine Already Exists" width="873" height="294" /></a> Virtual Machine Already Exists[/caption]

As of the release candidate of vSphere 6.0, the vCenter Server Appliance installation wizard does not clean up deployed virtual machines after failed deployments. Virtual Machines deployed are still present on the selected ESXi hosts inventory. Log into the ESXi host, power off, and delete the virtual machine from the failed deployment.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/02/vcsa-failed-deployment-vms-not-delete.png"><img class="aligncenter size-full wp-image-3537" src="http://www.virtxpert.com/wp-content/uploads/2015/02/vcsa-failed-deployment-vms-not-delete.png" alt="vcsa-failed-deployment-vms-not-delete" width="483" height="272" /></a>

If you attempt to redploy the virtual machine with a different name (appliance and host name) using the same IP address you receive the following error message:

<em><strong>Encountered an internal error. see /var/log/firstboot/vmafd-firstboot.py_6399_stderr.log</strong></em>

Because the virtual machine was deployed and powered on, there is a duplicate IP address on the network.