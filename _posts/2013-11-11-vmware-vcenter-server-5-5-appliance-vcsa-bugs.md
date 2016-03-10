---
ID: 1501
post_title: >
  VMware vCenter Server 5.5 Appliance
  (VCSA) Bugs
author: Jonathan Frappier
post_date: 2013-11-11 10:24:22
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vmware-vcenter-server-5-5-appliance-vcsa-bugs/
published: true
dsq_thread_id:
  - "1956392928"
---
<strong>[Updated / Solved] - I don't feel bad for posting this, as others may run into the same scenario.  I deployed the OVA and used the default settings it configured the VM with - 2 vCPUs and 8GB of RAM.  Apparently that is not enough memory to function properly.  After increasing the memory to 16GB all Web Client functions appear to be working.  I will test re-deploying the appliance and running the setup wizard with 16GB of RAM to see if I get the AD integration failure again soon.</strong>

Working on a POC of vSphere 5.5 with the vCenter Server Appliance (VCSA) and running into a few bugs with it that I am not finding in the VMware KB which is normally very good.  The VCSA was deployed on a host with dual quad-core Intel Xeon processors and 128GB of RAM, so I don't think this is a resource issue.

The first issue I ran into, after deploying the OVA I downloaded from my.vmware.com, the Setup Wizard said it failed during the Active Directory configuration.  I happened to also be logged into the C# client and could see the CPU was pegged.  For a few minutes I could not navigate to any of the appliance's management pages.  Once the CPU settled down, the management page was responsive again and it had successfully configured AD integration.

Second, I am still unable to deploy OVA's through the web client.  It fails when trying to select a datastore, it also did this with 5.1 for me.  The OVA deploys fine via the C# client.

Finally, there are several settings I am unable to configure via the web client.  I just get the 'Loading...' bar.  I checked resource utilization from the C# client and its quiet.

<a href="http://www.virtxpert.com/wp-content/uploads/2013/11/loading.png"><img class="aligncenter size-full wp-image-1502" alt="loading" src="http://www.virtxpert.com/wp-content/uploads/2013/11/loading.png" width="964" height="535" /></a>

&nbsp;

I haven't been able to find any mention of this in the VMware KB.  I'll try to dig into the logs shortly and see if anything stands out.  Anyone else seeing issues in the web client?