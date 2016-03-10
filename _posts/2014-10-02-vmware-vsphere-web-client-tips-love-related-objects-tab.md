---
ID: 2666
post_title: 'VMware vSphere Web Client Tips &#8211; Love Related Objects Tab'
author: Jonathan Frappier
post_date: 2014-10-02 09:01:42
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vmware-vsphere-web-client-tips-love-related-objects-tab/
published: true
dsq_thread_id:
  - "3075711293"
---
So, here we are, almost 2015 and folks are STILL complaining about the web client.  Yes, in 5.1 it sucked.  Yes the fact that it is written in Flash is not ideal.  Yes VMware added the ability to manage hardware version 10 VMs back to the C# client.  And yes there were rumors about at VMworld that the C# client will in fact live into the next version of vSphere.  But, folks, its time.  I was where you are not to long ago; loving the warm coziness of the C# client for my day to day work but then three things happened.  The 5.5 web client actually rocks, I switched to a Mac and I wrote a book and didn't want to be that person using with screenshots of the C# client in a book where the focus was vSphere 5.5.

I hope to turn this into a regular series, with small tips on how to get he most out of the web client for those still clinging to the C# client.  So here we go; The <strong>Related Objects</strong> tab.  The Related Objects tab might just be one of the most useful areas of the web client; regardless of what yo are looking at you can see a list of... you guessed it, related objects.  For example If I am looking at a Data Center I can see all of the hosts, clusters, VMs, datastores, switches etc... right from the Related Objects tab

[caption id="attachment_2668" align="aligncenter" width="1350"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/10/web-client-related-objects.png"><img class="size-full wp-image-2668" src="http://www.virtxpert.com/wp-content/uploads/2014/10/web-client-related-objects.png" alt="vSphere Web Client Related Objects Tab" width="1350" height="249" /></a> vSphere Web Client Related Objects Tab[/caption]

The wonderful thing about the Related Objects tab - its everywhere and changes context based on what you are looking at.  For example if I click on my Cluster &gt;&gt; Related Objects I won't see information about other clusters, just items related to that specific cluster.  If I click on a VM/vApp I will see information about that VM.  I can continue to drill down in the Related Objects tab.  It's not only information but I can make setting changes right there, no need to bounce back and forth to different screens.  If I need to make a change to the vSwitch/Portgroup my VM is connected to, right click and edit - boom all done!