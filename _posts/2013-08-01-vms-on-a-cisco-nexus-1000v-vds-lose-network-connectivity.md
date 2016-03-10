---
ID: 1239
post_title: >
  VMs on a Cisco Nexus 1000v VDS lose
  network connectivity
author: Jonathan Frappier
post_date: 2013-08-01 09:54:42
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vms-on-a-cisco-nexus-1000v-vds-lose-network-connectivity/
published: true
dsq_thread_id:
  - "1555841793"
---
Recently I ran into an issue with certain hosts in one of our data centers configured with a Cisco Nexus 1000v VDS; any VM on certain host would lose network connectivity.  If you did a vMotion to another host connectivity would be restored to the VM while on the working host.

I did a review of the networking configuration on all host, and I was disapointed to find they all matched perfectly; after all and easy fix would have been something mis-configured.  In working with VMware support they found that not all of the VLANs were visible to the VDS on the affected host.  Unfortunately this is where VMware drew the line on support suggesting it might be a Cisco problem (protip - buy a vBlock) so I checked my UCS config and found, again that all my up-links were configured the same, allowing all our configured VLANs at a physical level.  A search of the KB and Googles turned up nothing specific to this configuration or the symptoms we were seeing.  Thankfully the VMware community came through here for a fix.  <a href="http://twitter.com/GreggRobertson5" target="_blank">Gregg Robertson</a> had a <a href="http://thesaffageek.co.uk" target="_blank">blog </a>post for a similar scenario but this was for a vSphere 4 implementation, I pined him regardless.  Even though he hadn't seen this particular issue, <a href="http://twitter.com/Mandivs">@Mandivs</a> saw the conversation and replied with a fix.  Here are the steps to determine if you are facing this problem and how to correct (though I still haven't been able to find out why it happened).  These steps were performed in the vSphere client (I have multiple environments to manage so I lean towards the client for consistency right now) but those familiar with the web client won't have a problem.
<ul>
	<li>Log into vCenter</li>
	<li>Select a host believed to be working properly, and one that is not and perform the following on both</li>
	<li>Go to Inventory &gt;&gt; Host and Clusters, click Configuration tab, click Security profile.  Click properties on top right (services), select SSH, click Options, start SSH.</li>
	<li>Click properties for Firewall, ensure SSH Server is selected, click ok</li>
	<li>Open a SSH session to the host, login as a user with administrative privileges</li>
	<li>Type the following command: vemcmd show port vlans</li>
	<li>Verify if all the VLANs appear as expected.</li>
	<li>If the VLANs are all listed, the problem is not (shouldn't be) with the host network.  If not all of the VLANs are listed continue to the next step.</li>
	<li>vMotion all of the VM's off the affected host</li>
	<li>Type the following command:  vem restart</li>
	<li>Re-run vemcmd show port vlans and confirm all VLANs are present</li>
	<li>Migrate a VM back to the previously bad host and test.</li>
</ul>
As I said before, I still haven't tracked down why this happened but if I do I will update the post, or if you do feel free to leave a comment :)  You may also be able to acomplish some of those steps with the VMA or PowerCLI but I don't yet have that setup in this particular environment.

&nbsp;

&nbsp;