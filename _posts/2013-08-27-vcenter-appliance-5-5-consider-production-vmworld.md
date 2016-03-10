---
ID: 1315
post_title: 'vCenter Appliance 5.5 &#8211; Would you consider it for production #vmworld'
author: Jonathan Frappier
post_date: 2013-08-27 10:24:07
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vcenter-appliance-5-5-consider-production-vmworld/
published: true
dsq_thread_id:
  - "1654873455"
---
With the announcement of vSphere 5.5 at VMworld 2013 yesterday came a long list of improvements, one of which was updates to the vCenter appliance, upgrading the number of hosts from only 5 to 500 (and now up to 5000 VMs, up from only 50)!  The vCenter appliance was nice for lab work, but I had a hard time considering it, even for very small deployments of only 2 or 3 hosts since VMware makes it so easy, I could see a lot of deployments going beyond the 5 host limit.  Add to this removing the Windows Server and SQL tax and this is huge.

I had pushed off a 4.1 upgrade, knowing 5.5 was coming and at first I overlooked these improvements to the vCenter appliance, but now I am thinking long and hard about deploying this for production.

Considerations I haven't thought through include backups of the database (or I guess just the entire VM) and sizing considerations for the appliance to manage a large number of VMs.  What are others saying?

Duncan Epping:  <a href="http://www.yellow-bricks.com/2013/08/26/vsphere-5-5-nuggets-vcenter-server-appliance-limitations-lifted/" target="_blank">http://www.yellow-bricks.com/2013/08/26/vsphere-5-5-nuggets-vcenter-server-appliance-limitations-lifted/</a>
<pre>If you ask me, this means that the vCenter Server Appliance with the embedded database can be used in almost every scenario! That makes life easier indeed.</pre>
There hasn't been much other chatter I am finding, what are you thoughts?  Legit for production deployments now?