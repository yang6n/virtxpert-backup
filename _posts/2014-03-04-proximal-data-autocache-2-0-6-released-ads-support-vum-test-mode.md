---
ID: 2017
post_title: >
  Proximal Data AutoCache 2.0.6 releases
  ads support for VUM, test mode
author: Jonathan Frappier
post_date: 2014-03-04 11:36:15
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/proximal-data-autocache-2-0-6-released-ads-support-vum-test-mode/
published: true
dsq_thread_id:
  - "2358760579"
---
<em>Disclaimer:  Proximal Data is a sponsor of virtxpert.com.  This post is a review of the new features they announced.  This post has not been reviewed or altered in any way by Proximal Data and is strictly my opinion.</em>

Proximal Data has just announced a new version of AutoCache, among the new features are a "test mode" to allow you to test the effectiveness of your caching devices such as an SSD or PCI-E flash drive and automated intelligence which allows the VM to bypass cache if there is a problem which would actually degrade performance by using the flash device.  I am most interested to see how the later works, and am hoping there is some sort of alerting built into this feature; after all if caching is not being effective I want to be notified.  In addition to these two features, there is improved integration with VMware Update Manager allowing you to upgrade your host without having to remove AutoCache.

Proximal Data uses local server flash devices to cache and serve hot data allowing VMs faster access to the data and reducing traffic to your SAN or NAS.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/03/AutoCache_after_292.png"><img class="aligncenter size-full wp-image-2018" alt="AutoCache_after_292" src="http://www.virtxpert.com/wp-content/uploads/2014/03/AutoCache_after_292.png" width="292" height="406" /></a>

<strong>Summary</strong>

If you are a current Proximal Data customer, you should look at getting upgrade to take advantage of these new features.  If there are any Proximal Data folks reading, can you confirm if there are alerts if you are automatically by-passing cache?