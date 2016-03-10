---
ID: 2263
post_title: >
  AWS vCenter Plugin ellicits response
  from VMware, but why?
author: Jonathan Frappier
post_date: 2014-06-06 08:56:32
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/aws-vcenter-plugin-ellicits-response-vmware/
published: true
dsq_thread_id:
  - "2741524125"
---
Amazon recently released an AWS vCenter plugin that allows direct provisioning of AWS instances from vCenter.  You can read more about the plugin here: <a class="jive-link-external-small" href="http://aws.amazon.com/ec2/vcenter-portal/" rel="nofollow">http://aws.amazon.com/ec2/vcenter-portal/</a>

Shortly after, VMware responds with a post pointing out the negatives with a solution that does not allow for true hybrid management which you can read here: <a class="jive-link-external-small" href="http://www.theregister.co.uk/2014/06/02/vmware_amazon_counter_marketing" rel="nofollow">http://www.theregister.co.uk/2014/06/02/vmware_amazon_counter_marketing</a>

My question is, so what?  Doesn't VMware's own vCloud Automation Center (vCAC) provide this exact same functionality - provision AWS instances without the ability to migrate workloads?  I don't think this plugin from Amazon takes away from the vCAC market, in fact it probably hurts smaller vendors such as CloudBolt more than it hurts VMware.  While you could argue that it might take away from vCloud Hybrid Serivce (vCHS) sales, doesn't that really depend on your use case?  In some cases the ability to provision AWS instances such as test/dev for example may not need to be migrated, so AWS would be fine where as VMs provisioned in response to increase demand may warrant moving back and forth between vCHS and a private vSphere/vCAC cloud.

I wonder what your thoughts are?