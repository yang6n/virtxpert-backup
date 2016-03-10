---
ID: 4185
post_title: >
  Deploying ManageIQ (OpenSource RedHat
  CloudForms) and Discovering vCenter
author: Jonathan Frappier
post_date: 2015-11-25 20:49:42
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/deploying-manageiq-opensource-redhat-cloudforms-and-discovering-vcenter/
published: true
dsq_thread_id:
  - "4351334642"
---
Since I spend my days working with vRealize Automation, I like to understand what other platforms are out there such as CloudBolt C2 and RedHat CloudForms. While CloudForms does not have a trial or free(mium) download, there is <a href="http://manageiq.org/" target="_blank">an OpenSource version from the ManageIQ</a> acquisition. There are several ways which you can get started with ManageIQ, I have opted for the vSphere deployment which comes as an OVA you can deploy - I did so in VMware Workstation.

Once the OVA has been deployed, power on the virtual machine and access the console either through the vSphere Web Client or Workstation. Log in with the default credentials of admin / smartvm to change the hostname, or IP address. By default the VM will boot with DHCP enable so if you just want to quickly test drive  the ManageIQ GUI you can do so very easily.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/manageiq.png"><img class="aligncenter size-full wp-image-4186" src="http://www.virtxpert.com/wp-content/uploads/2015/11/manageiq.png" alt="manageiq" width="1674" height="870" /></a>

Log in with the same default credentials of admin/smartvm to access the ManageIQ GUI. You can change the basic settings under Configure &gt;&gt; Configuration

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/manageiq-configuration.png"><img class="aligncenter size-full wp-image-4187" src="http://www.virtxpert.com/wp-content/uploads/2015/11/manageiq-configuration.png" alt="manageiq-configuration" width="901" height="208" /></a>

One of the first items I would want to do is configure a cloud or infrastructure provider; I will start by going to Infrastructure &gt;&gt; Configuration &gt;&gt; Discover Infrastructure Providers. By default you can discover either vCenter, Microsoft SCVMM, or RedHat Virtualization Manager.

Click the VMware vCenter checkbox, provide an IP range to perform the discovery and click Start. Wait a few minutes and refresh the page; you should now see your Virtual Center listed.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/providers.png"><img class="aligncenter size-full wp-image-4188" src="http://www.virtxpert.com/wp-content/uploads/2015/11/providers.png" alt="providers" width="717" height="219" /></a>

&nbsp;

Once the provider appears, click on Configuration &gt;&gt; Edit this Provider and enter credentials for vCenter, likely a service account in the real world, or administrator@vsphere.local if you are testing in your lab. Validate, save the credentials, and then click Configuration &gt;&gt; Refresh Relationships.

After a few minutes you should be able to refresh the screen and see the number of hosts, as well as a green checkmark on the provider icon, now you can drill down to see details about the environment.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/manageiq-vc.png"><img class="aligncenter size-full wp-image-4191" src="http://www.virtxpert.com/wp-content/uploads/2015/11/manageiq-vc.png" alt="manageiq-vc" width="1675" height="610" /></a>

Navigate through the infrastrure items and you should be able to see all the details about your vCenter environment including cluster information such as total hosts, cores, memory and even HA and DRS configuration as well as hosts, virtual machines and datastores.

One item that was of interest you may have noticed is the Configuration Management tab, this integrates with another opensource project called <a href="http://theforeman.org/" target="_blank">Foreman</a> which I will also be looking in to. My last task for tonight, setup a user and allow them to log in; navigate to Configure &gt;&gt; Configuraiton &gt;&gt; Access Control &gt;&gt; Users &gt;&gt; Configuration &gt;&gt; Add a new User (lots of navigation here!). I added a user account and logged back in as that user and as you can see in the screenshot below, I can see my vCenter Resources but am unable to change policies related to that infrastructure provider.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/provider-user.png"><img class="aligncenter size-full wp-image-4192" src="http://www.virtxpert.com/wp-content/uploads/2015/11/provider-user.png" alt="provider-user" width="311" height="300" /></a>

I've just started to scratch the surface with ManageIQ/CloudForms, but am very interested in continuing to explore its features