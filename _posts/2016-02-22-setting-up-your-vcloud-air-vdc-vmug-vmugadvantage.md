---
ID: 4310
post_title: 'Setting up your vCloud Air VDC #VMUG #VMUGADVANTAGE'
author: Jonathan Frappier
post_date: 2016-02-22 08:15:58
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/setting-up-your-vcloud-air-vdc-vmug-vmugadvantage/
published: true
dsq_thread_id:
  - "4601115593"
---
<em>**Disclaimer: My VMUG Advantage subscription was provided courtesy of the Boston VMUG. This post was not paid for, nor reviewed prior to publishing. This is simply my opinion after using the service. Additionally, I am an EMC employee**</em>

Once you have completed the signup for your VMUG Advantage, you go through a checkout process on the VMUG website to access the advantage subscriptions, this is fairly well documented so I am not going to rehash that. Once you get your welcome email from vCloud Air, be sure to note the Service ID associated with the account.

When you sign into vCloud Air, the first step will be to create your VDC; if you have multiple accounts on my.vmware.com, this is where you will want to be certain you associate the VDC with the appropriate service ID, otherwise you will be charged. Now, you will select the location of your VDC, as vCloud Air offers several physical locations:

<a href="http://www.virtxpert.com/wp-content/uploads/2016/02/vca-location.png" rel="attachment wp-att-4311"><img class="aligncenter size-full wp-image-4311" src="http://www.virtxpert.com/wp-content/uploads/2016/02/vca-location.png" alt="vca-location" width="1365" height="577" /></a>

Your VDC will be created, along with an edge device used to provide network services such as NAT, DHCP, load balancing, and firewall services. Once complete, you are now ready to create your first virtual machine.

<a href="http://www.virtxpert.com/wp-content/uploads/2016/02/vca-vdc.png" rel="attachment wp-att-4313"><img class="aligncenter size-full wp-image-4313" src="http://www.virtxpert.com/wp-content/uploads/2016/02/vca-vdc.png" alt="vca-vdc" width="1366" height="429" /></a>

You will have the option to create a virtual machine from scratch, or select from several pre-defined templates. For example if you are interested in testing Ansible you could deploy either a CentOS or Ubuntu template. If you click create from scratch, you will be launched into the vCloud Director GUI (the same as you would get from deploying VCD, so another good use case to get some time administering VCD) to create the vApp. If you are not familiar with VCD, you always create vApps, not just virtual machines.

Select the Ubuntu 64-bit template and click continue, you can now assign resources to the template, as you would a regular virtual machine in vCenter. Note the cost here, for the Ubuntu 64-bit vApp with 1 vCPU, 2GB of RAM and a 10GB drive (either standard or SSD accelerated) the cost is 5cents per hour...5cents! To run that single VM for 24 hours would cost a total of $1.20

<a href="http://www.virtxpert.com/wp-content/uploads/2016/02/vm-vca.png" rel="attachment wp-att-4314"><img class="aligncenter size-full wp-image-4314" src="http://www.virtxpert.com/wp-content/uploads/2016/02/vm-vca.png" alt="vm-vca" width="826" height="562" /></a>

You could run 2 Ubuntu vApps/VMs - one for the Ansible control machine and one to run playbooks against, 24 hours per day for 20 before your Advantage credit is used up. If you take care and shut down when you are not actively using, you can start to see how this is a good alternative to buying a home lab for basic testing.

So, what about a nested lab? I can run ESXi virtually, and vCloud Air is based on vSphere so... in theory this should be possible. Well before I dive into setting up ESXi in vCloud Air my question is, is it cost feasible? If I play around with the sliders for a moment I found that  2vCPU, 12GB RAM, 300GB storage costs a whopping 25cents per hour. If I want to run a scaled back VCSA you should be able to get away with a small two host cluster, including a Windows 2008 DC for roughly 88cents per hour which gives you 56 hours a month of hands on time with vSphere.

In my next post, I'll walk through installing ESXi in vCloud Air.