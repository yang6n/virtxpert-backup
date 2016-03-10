---
ID: 4040
post_title: AWS Virtual Private Cloud (VPC) Options
author: Jonathan Frappier
post_date: 2015-11-04 21:21:03
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/aws-virtual-private-cloud-vpc-options/
published: true
dsq_thread_id:
  - "4290752759"
---
I am starting to look at Amazon AWS and the various solutions available with it. For starters, I am looking at the various Virtual Private Cloud, or VPC, configuration options.

The first option available is setting up the VPC with a single, public subnet. That is all instances will have access to the internet. You can control access via ACLs as you might expect (please don't allow 0.0.0.0/0 all/all - think through your ACLs as you would a regular firewall).

The second option is to setup both a public, and private subnet. In this scenario, the instances in your private subnet do not have direct internet access. However you can setup NAT through your public subnet. This seems like the most logical option to me, as I would not want all of the servers in an application stack to have internet access - for example your database servers. If you are going to give the items in your private subnet internet access through a NAT device, remember those NAT devices will incur charges - in that scenario you might as well go with the single public subnet.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/vpc-priv-pub.png"><img class="aligncenter size-full wp-image-4041" src="http://www.virtxpert.com/wp-content/uploads/2015/11/vpc-priv-pub.png" alt="vpc-priv-pub" width="286" height="265" /></a>

The final two options provide you with the option for a hardware based VPN solution; depending on your security requirements this may be an option for you.

The next step is to define your subnet, by default a 10.0.0.0/16 block for your private space and 10.0.0.0/24 for your public space though you can change these to any private range you prefer. The ranges entered here will be used to configure a gateway device to allow communication. Your public subnet must fall within the range of your IP block.

You can also select your availability zone, or select a specific one if you have certain location requirements. Once your VPC is created, take a look through the options available. If you started deploying instances from here,  you would eventually find a huge security hole - the default rules allow ALL inbound traffic - eeek!

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/default-rules.png"><img class="aligncenter size-full wp-image-4042" src="http://www.virtxpert.com/wp-content/uploads/2015/11/default-rules.png" alt="default-rules" width="710" height="244" /></a>

This is also true for outbound communication, I've always been a fan of restricted outbound rules for my servers - there is no need for these to have outbound access in most cases.

That is a quick look at Amazon VPC's; as you can see super easy to create (and enable shadow IT), but also super insecure and why you should be engaged with someone that understands all of the ins and outs (ACL pun intended) of AWS. If you would like a <a href="http://professionalvmware.com/2015/11/vbrownbag-follow-up-an-introduction-to-amazon-vpc-with-sarah-zelechoski-szelechoski/" target="_blank">deeper dive on VPCs check out this #vBrownBag</a>