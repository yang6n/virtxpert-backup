---
ID: 1083
post_title: 'Infinio &#8211; Why cache to disk when you can cache to RAM'
author: Jonathan Frappier
post_date: 2013-06-19 08:09:54
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/infinio-why-cache-to-disk-when-you-can-cache-to-ram/
published: true
dsq_thread_id:
  - "1412131513"
---
Way back in April I had the opportunity to meet with a start-up called <a href="http://infinio.com/" target="_blank">Infinio </a>to participate in a review of their UI.  I had no idea going in what the product was about but was quickly floored by their vision and potential.  Infinio will have their first public demo Thursday at <a href="https://twitter.com/search?q=%23tfd9&amp;src=typd" target="_blank">Tech Field Day 9</a> and will also be a <a href="http://professionalvmware.com/2013/06/vbrownbag-techtalks-at-vmworld/" target="_blank">sponsor for the ProfessionalVMware.com #vBrownBag</a> at <a href="http://www.vmworld.com/community/conference/us/" target="_blank">VMworld 2013 in San Diego</a> on August 25th - 29th.
<div>

Infinio will allow you to create a read cache directly in RAM via a software appliance that will run on your ESXi host like any other VM.  Unlike caching to SSD or flash there is no additional hardware or infrastructure to buy (unless your host are light on RAM) like you would with a flash based array.  Since the VMware community is so awesome, I was curious about RAM availability in most host - enter <a href="http://vopendata.org" target="_blank">vOpenData.org</a>.  The metrics they collect support the idea that most hosts will have more than enough RAM to support the VM.  On average, host are running just under 12 VMs with an average of 115GB of RAM.  I pinged William Lam on Twitter to see if they can add the average amount of RAM per VM, but with 115GB per host, I suspect you have some idle capacity.

<a href="http://www.virtxpert.com/wp-content/uploads/2013/06/vopendatahostram.jpg"><img class="aligncenter size-large wp-image-1089" alt="vopendatahostram" src="http://www.virtxpert.com/wp-content/uploads/2013/06/vopendatahostram-1024x489.jpg" width="640" height="305" /></a>

Since this is RAM based, you will only be caching read requests since there is no hardware/battery backup like you would have with a Write cache.  For me, every millisecond I can save, every piece of IO I can offload from datastores hosted on my NAS helps provide a more responsive VM environment.

A couple of launch items to note; Infinio will only support NFS at launch.  If you are grappling between iSCSI and NFS for your datastores, add Infinio to the list of 'pros' for selecting NFS.  While one of the huge benefits I see is the speed of your RAM, SSD support will also be added in the future so you can add even a single SSD drive to your host to cache even more requests (lets face it even SSD is better than spinning disk for caching, eliminating disk swapping).

While the folks at #TFD9 will be getting a live demo, I am scheduled to get this hands on in my lab next week.  I had hoped to get an early preview of the software and installation process, but my recent job change negatively affected my schedule and access to a lab environment.  Once I am able to catch up with the team at Infinio I will have a follow up post to let you know how they are doing.  From the early work I did see, the product should be a win for shops running their datastores via NFS by the ease of installation, use and increased performance many workloads will see.

What do you think about a product that can cache to RAM?  Are you as excited as I am about its potential?  What questions do you have about Infinio?  Below is the Storage-Switzerland intro video.

<iframe src="http://www.youtube.com/embed/LXWJQVglLVk" height="315" width="560" allowfullscreen="" frameborder="0"></iframe>

</div>