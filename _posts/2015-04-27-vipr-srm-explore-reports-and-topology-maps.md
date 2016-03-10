---
ID: 3722
post_title: >
  ViPR SRM Explore Reports and Topology
  Maps
author: Jonathan Frappier
post_date: 2015-04-27 08:00:25
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vipr-srm-explore-reports-and-topology-maps/
published: true
dsq_thread_id:
  - "3716472749"
---
*<em>*Disclaimer: I am an EMC employee, this post was not sponsored or in any way required by my employer, it is my experience getting to know this particular product.**</em>

Up until now I went through a basic ViPR SRM installation, getting a basic single VM environment setup. What I want to show in this post is my favorite ViPR SRM feature - topology maps. To understand why these are useful, lets step back and give some scenarios:

<span style="line-height: 1.5;">You are the personal responsible for supporting the storage within your environment, you may support other things but ultimately when there is a storage related problem your name is called. An application own comes to you and says their application is slow, and that the network team said everything on their end is fine so its probably the storage. Great - now what?</span>
<ol>
	<li>You come into a new organization - whether as an internal IT person or a var and you've inherited an environment cabled by 3 monkeys and a cat with no documentation - now what?</li>
</ol>
This is where topology maps can be very useful. The topology maps is that end-to-end visualization and monitoring component I mentioned in previous posts. I see from my virtual machine or even some applications such as SQL Server all the way through to the underlying storage, and drill down on each component. Let me shows you some examples.

To access the topology maps, click on Explore &gt;&gt; Hosts - small aside here - host could be any physical or virtual server in the environment discovered by ViPR SRM, not just ESXi hosts. So this could be an ESXi host, a virtual machine, or a physical host running its own OS.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-explore-reports-hosts.jpg"><img class="aligncenter size-full wp-image-3723" src="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-explore-reports-hosts.jpg" alt="vipr-srm-explore-reports-hosts" width="1346" height="531" /></a>

From this report, you can see a list of all the hosts in the environment, which for some could be a very extensive list. I should mention that the filter field is not a search field, so you cannot type the end of a machine name; for example maybe all your VM names end in OS type or some other identifier, you couldn't just type W2K8 to find a server name myserver-w2k8, you would have to start with myserver, but would then see a list of all servers starting with that string. You can filter on any column that has the funnel icon, so for example I could filter on just physical hosts, or virtual machines by clicking the funnel icon in the host type column;

<a href="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-filter.jpg"><img class="aligncenter size-full wp-image-3724" src="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-filter.jpg" alt="vipr-srm-filter" width="211" height="261" /></a>

Using the example above, let's say an application owner has complained about performance and you need to investigate to see if storage could be the problem. Filter on the host name, in this case I will pick on mhmbd078-W2K8, as you can see below I start typing that name and can select it from a the list or type it in full and hit enter to filter on that one host

<a href="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-filter-hostname.jpg"><img class="aligncenter size-full wp-image-3726" src="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-filter-hostname.jpg" alt="vipr-srm-filter-hostname" width="601" height="396" /></a>

&nbsp;

Now I just see that specific host, in this case a virtual machine as you can see here with 16GB of memory and 4 vCPU:

<a href="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-single-host-explore.jpg"><img class="aligncenter size-full wp-image-3727" src="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-single-host-explore.jpg" alt="vipr-srm-single-host-explore" width="1121" height="268" /></a>

This much information is available in just a few clicks, now there are many places you could get this information but as I continue to drill deeper, you will start to see just how much information we have at hand. With just what is available so far, you might be able to say to the application owner who issued the complain that there is not enough memory, for example maybe you know that this particular application needs 32GB of memory, so disk I/O could be a problem if the application and OS are constantly swapping to disk. But, maybe so far everything checks out, if I click on any of the text here, it will take me into the detail of that virtual machine.

Now, this is where it gets interesting; what you see below is the topology map for mbmbd078-w2k8, we can see the host, the datastore it is on, the host it is on, the VSANs it is connected to and the arrays connected to those VSANs. Also, notice to the right we have different reports related to the host, we can see attributes about the host which is show by default, you can also see:
<ul>
	<li>Capacity information about the hosts local disks, in this case VMDKs and since it is a virtual machine, the datastore</li>
	<li>Path details for the disks attached to the host</li>
	<li>Related storage performance</li>
	<li>Events related to the host</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-topology-map.jpg"><img class="aligncenter size-full wp-image-3729" src="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-topology-map.jpg" alt="vipr-srm-topology-map" width="1107" height="518" /></a>

You can click on any element in the map to see details specific to that item, for example if you click on the datastore - DS_Bootcamp_D you can see reports about the datastore, or on the host - you guessed it, reports about the host. You may have also noticed the + icon next to some of the elements, this is because there are additional components, using VSAN0040 as an example, we can click on the + sign to see switches in that VSAN

<a href="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-exapanded-element.jpg"><img class="aligncenter size-full wp-image-3730" src="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-exapanded-element.jpg" alt="vipr-srm-exapanded-element" width="569" height="305" /></a>

Now I see two switches, each with their own + icon, I can keep drilling down and see ports on that switch as well. I can expand different elements and hover over different components to see how they are connected. For example I have expanded my host to see my HBAs, I can see that the particular HBA I am interested in is connected to VSAN mptb023 so I have expanded that as well and drilled down to see the switch ports. While I have some limited lab resolution available, you can see here that when I hover over the HBA from the host it highlights the path to the port on the switch - in this case fc1/6 (as shown by the blue highlighted line)

<a href="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-show-details.jpg"><img class="aligncenter size-full wp-image-3731" src="http://www.virtxpert.com/wp-content/uploads/2015/04/vipr-srm-show-details.jpg" alt="vipr-srm-show-details" width="700" height="311" /></a>

This is just one specific report, and I have only skimmed the surface of the data available in this report. Imagine being able to show this to an application owner as you troubleshoot each component, and explain how/why any particular piece of the infrastructure supporting the application is, or isn't doing what it is supposed to. For those folks who worked in a silo'd type group, I'd urge you not use this information to punt back over your wall to someone else, but rather be the person to start poking some pinholes in the silo, call up a virtualization, OS, or network person depending on what you might think the problem is and work with them, sharing knowledge and help the application owner be a happy customer. After all, even if you are "internal" IT - you are still providing a service to the business - they are you customers, treat them like it. Silos will only fall if someone starts poking holes, no reason it can't be you.

If you haven't done so, chat with your EMC rep (they can likey get you in touch with an SE who can help if you have any setup questions) and head over to support.emc.com to sign up for an account and download ViPR SRM which comes with a 30 day license.