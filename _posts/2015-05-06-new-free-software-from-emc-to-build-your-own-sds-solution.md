---
ID: 3738
post_title: >
  New free software from EMC to build your
  own SDS solution
author: Jonathan Frappier
post_date: 2015-05-06 08:24:55
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/new-free-software-from-emc-to-build-your-own-sds-solution/
published: true
dsq_thread_id:
  - "3741110013"
---
*<em>*Disclaimer: I am an EMC employee, this post was not sponsored or in any way required by my employer, it is my experience getting to know this particular product.**</em>

There were two software related announcements at EMC World this week which I found very exciting. Building on the free for no production use of <a href="http://www.emc.com/storage/recoverpoint/recoverpoint-for-virtual-machines.htm#!software_download" target="_blank">RecoverPoint for Virtual Machines</a> from VMworld 2014, EMC announced the same for ScaleIO. <a href="http://www.emc.com/products-solutions/trial-software-download/scaleio.htm" target="_blank">ScaleIO allows you build your own Hyperconverged Infrastructure solution</a> (HCI). This is the same software used in the new <a href="http://www.vce.com/products/hyper-converged/vxrack" target="_blank">VxRack</a> from VCE which was also announced at EMC World.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/05/TtlMiFqu.jpg"><img class="alignleft  wp-image-3740" src="http://www.virtxpert.com/wp-content/uploads/2015/05/TtlMiFqu.jpg" alt="CoprHD" width="157" height="157" /></a>In addition to ScaleIO, EMC also announced <a href="https://coprhd.github.io/" target="_blank">CoprHD which is an open source version of EMC ViPR</a> (<a href="https://twitter.com/coprhd" target="_blank">@coprhd</a>). <a href="http://www.emc.com/vipr" target="_blank">ViPR</a> (which is also free for non production use) is a solution that allows you to manage multiple arrays and present those as virtual volumes to hosts. In addition to managing the arrays, it also provides a self-service and automation at the storage layer. EMC ViPR also supports ScaleIO, assuming this carries over to CoprHD you could deploy a fully managed, and automated storage solution on commodity hardware for test/dev or QA (I hope they publish more specific guidelines on just what they mean by "non-production").

Last, but not least, the <a href="http://www.emc.com/products-solutions/trial-software-download/vvnx.htm" target="_blank">community version of the VNXe</a> which you can use to provide full block and file servers on commodity hardware. The vVNX will later come in a supported ROBO and cloud edition.

My hope is that CoprHD, ScaleIO, and the community edition of the vVNX will lead to more solutions being open sourced and offered in a free to use model. CoprHD should be available on GitHub by June, ScaleIO by the end of May, whereas the vVNX is available now for download.

&nbsp;