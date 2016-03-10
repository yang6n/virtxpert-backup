---
ID: 247
post_title: VMware home lab rebuilt
author: Jonathan Frappier
post_date: 2012-12-11 14:15:24
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vmware-home-lab-rebuilt/
published: true
jabber_published:
  - "1355253324"
publicize_reach:
  - 'a:2:{s:7:"twitter";a:1:{i:1983177;i:469;}s:2:"wp";a:1:{i:0;i:14;}}'
publicize_twitter_user:
  - jfrappier
email_notification:
  - "1355253325"
reddit:
  - 'a:2:{s:5:"count";i:0;s:4:"time";i:1356936674;}'
dsq_thread_id:
  - "1118154764"
---
You know what would be great, if VMware had their Hands On Labs (HOL) available online - yea I'm talking to you!!!  Since I don't have an account yet and I would like to start working on my VCAP-DCD I had to dust off the lab and start getting it ready.  It sat dormant since early October when I passed my VCP-DV so I decided to rebuild from scratch.  My gear:
<ul>
	<li>2 Dell Precision workstations with dual dual-core Xeon 1.6GHz processors and 4GB or RAM each, 160GB local disk and 3 1Gbps NICs.  I know not a ton but enough to run a couple of VMs for Active Directory, vCenter and a few test machines.</li>
	<li>Shared NFS storage with a used Buffalo NAS from eBay for &lt; $100 (had no drives) - just wanted something to toy around with versus using FreeNAS or similar sharing the local disk in the host.</li>
</ul>
Had a weird battle with adding one of the hosts to vCenter.  VMware KB suggested it was bad DNS or IP or an SSL timeout problem but could connect directly to the host and they sit on the same switch.  Just reset the ESXi config and re-addressed and worked like a champ.  Next steps are to setup syslog, thinking I will give Splunk a try this time.  I have used Alienvault in the past since it also included monitoring but want to see something different.  Once I have syslog setup will finally do a 5.0 to 5.1 upgrade and possibly install vCD.