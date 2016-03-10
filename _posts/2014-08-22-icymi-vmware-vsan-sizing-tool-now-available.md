---
ID: 2487
post_title: 'ICYMI &#8211; VMware VSAN Sizing Tool now available'
author: Jonathan Frappier
post_date: 2014-08-22 11:09:48
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/icymi-vmware-vsan-sizing-tool-now-available/
published: true
dsq_thread_id:
  - "2949987438"
---
Those nice folks over at VMware have released a web based VSAN sizing tool.  When VSAN was first announced, there was quite a bit of math involved in <a title="VSAN all things!" href="http://www.virtxpert.com/vsan-all-things/">determine things like usable space, number of hosts</a> needed etc...  Now you can use the VSAN Sizing tool at <a href="http://virtualsansizing.vmware.com/" target="_blank">http://virtualsansizing.vmware.com/</a>; here is a quick walk through.
<ul>
	<li>When you first hit the site, click on the Start sizing button (all you anti-web client folks, don't be scare away by the very web client look and feel)</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/08/start-sizing.png"><img class="aligncenter wp-image-2488 " src="http://www.virtxpert.com/wp-content/uploads/2014/08/start-sizing.png" alt="start-sizing" width="358" height="117" /></a>
<ul>
	<li>First, enter the information about your virtual machines int he Virtual Machine Characteristics form on the left, for example I used 72 VMs with 1TB (1024GB) VMDKs, with 2 VMDKs per host each using 32GB of RAM.</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/08/vsan-sizing-tool.png"><img class="aligncenter  wp-image-2489" src="http://www.virtxpert.com/wp-content/uploads/2014/08/vsan-sizing-tool.png" alt="vsan-sizing-tool" width="882" height="599" /></a>
<ul>
	<li>Next click on Host Hardware Characteristics (honestly I dislike this part very much, I would have expected the calculator to help me identify the necessary host configuration, I shouldn't have to tell it what hardware I am using - is that what a calculator is supposed to do?)</li>
	<li>On the Host Hardware Characteristics page, enter the size of the disks in each hosts, the extra usable capacity (I am assuming GB but you may want to call that out), the number of magnetic (e.g. traditional hard drives) per host and the amount of memory, cores and VM density you would like each host to have.</li>
	<li>Once that information is entered, the sizing tool will tell you how many hosts you'll need, the size of flash based cache and other information like total memory in the cluster</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/08/vsan-cluster-output.png"><img class="aligncenter size-full wp-image-2490" src="http://www.virtxpert.com/wp-content/uploads/2014/08/vsan-cluster-output.png" alt="vsan-cluster-output" width="794" height="629" /></a>
<ul>
	<li>In the example output above, I entered 1TB disks, with 100GB of additional usable space with each hosts having 7 disks, 16 cores and 128GB of RAM and a 2-to-1 VM to core over commitment ratio (this is to support a nested production environment - yes I support a nested production environment) so I kept my VM to core low as my 72 VMs are all ESXi.</li>
	<li>I can see from the output I would need 22 hosts (nicely below the 32 host config maximum) which would provide me with 301TB of total capacity in the cluster.</li>
</ul>
All in all this is a handy tool, I would like to see a vCPU characteristic added to ensure the cluster size meets the demand of the VMs.  For example without asking how many vCPU my VM has, how can you identify a VM to core ratio which is asked on the Hardware Characteristics page? I would also like to see a host sizing tool, for example I have 72 VMs with 4x vCPU each, 1TB VMDKs and 32GB of memory, what size host do I need (VMware probably wants to avoid customers complaining about performance  if someone uses the tool incorrectly and builds a cluster based on the tools recommendations).

Originally announced at <a href="https://blogs.vmware.com/vsphere/2014/08/vmware-virtual-san-sizing-tool.html" target="_blank">https://blogs.vmware.com/vsphere/2014/08/vmware-virtual-san-sizing-tool.html</a>