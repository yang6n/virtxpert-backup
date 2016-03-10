---
ID: 937
post_title: 'VMware Announces vCloud Hybrid Service™ &#8211; Reaction to the news'
author: Jonathan Frappier
post_date: 2013-05-22 13:54:14
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vmware-announces-vcloud-hybrid-service-reaction-to-the-news/
published: true
dsq_thread_id:
  - "1306808122"
---
Yesterday VMware announced (click <a href="http://www.vmware.com/now.html" target="_blank">here </a>to see the recording) their new vCloud Hybrid Service, for those living under a rock for the better part of the last year, its VMware's IaaS offering; their answer to AWS, Azure, and the glut of smaller but still very good vendors such as GoGrid, Softlayer and ProfitBricks.  While it is an IaaS offering, I think it will be positioned as an "enterprise" cloud versus a consumer cloud meaning you should expect better SLA's and equipment with a focus on allowing current VMware customers an easy path to expanding their infrastructure (while making VMware some recurring month to month revenue - not a bad thing at all by the way).  This announcement was really no surprise, we all knew at a high level what was coming (<a href="http://www.youtube.com/watch?v=ooTine8PafQ" target="_blank">I uploaded a video of the beta version last October to YouTube</a>) but lets review what was released.

Pricing on the service can be found <a href="http://vcloud.vmware.com/about_services/pricing" target="_blank">here</a>; during the announcement they said it would be a very simple and straight forward pricing model, however at first glance is utterly confusing - am I paying per hour on compute, storage bandwidth and IP's?  It says on the page that those items are inclusive so is the chart listing cost over a certain amount?  A pricing calculator like <a href="http://calculator.s3.amazonaws.com/calc5.html" target="_blank">Amazon offers</a> would have been a handy add-on to their pricing page.  If the pricing works out to be similar to the vCloud Service Evaluation Beta pricing would start at roughly $30/month for 1 CPU, 512MB RAM, 50GB of storage based on 730 hours of use.

My brain not working (or the pricing page actually being confusing) aside, I have a love/hate relationship with this announcement.  For an on-premise solution, there isn't a better hypervisor/virtualization platform than VMware.  They make great software for managing all these resources but can they really compete with Amazon, and even Azure who already has a strong customer base?  Why not allow vCloud Director/vCloud Connector to work with these other IaaS providers to allow me to expand my data center into these other "public clouds"?  Is it really necessary to re-invent the wheel?

The flip side to that is this is clearly what VMware needs to do to stay relevant.  <!--more-->Companies are going to stop buying/building their own data centers to support peak/burst usage scenarios that generally only occur for a few hours a month.  If I can build my local/private cloud to meet every day demands and then burst into VMware's cloud for that short period of time, I can save quite a bit of money on infrastructure costs.  I have also seen a few tweets knocking VMware for "vendor lock in".

<a href="http://www.virtxpert.com/wp-content/uploads/2013/05/lockin.jpg"><img class="aligncenter size-full wp-image-938" alt="lockin" src="http://www.virtxpert.com/wp-content/uploads/2013/05/lockin.jpg" width="369" height="149" /></a>

Personally don't mind this that much, for production purposes I am a fan of having a single vendor to call for support.  Do you really want a conference call with VMware and Amazon when your not able to all of a sudden spin up VM's in AWS from vCenter?  Does it suck, yea a bit and I hear the argument but I also can live with it (wait wasn't the part I didn't like have to do with inability to use other public clouds :) ).

<strong>Wrap Up</strong>

So what we are left with is a new service from VMware that should make it easy for companies to expand their on-premise infrastructure without the need for additional CAPEX spending to support short periods of increased use with a vendor you know and trust and allow them to increase revenue, or at the very least maintain it by offsetting losses from customers moving to 100% public clouds.  I am a fan and can't wait for the opportunity to use this in a production environment.

Links to resource for the vCloud Hybrid Service™ can be found below:
<ul>
	<li>Pricing:  <a href="http://vcloud.vmware.com/about_services/pricing">http://vcloud.vmware.com/about_services/pricing</a></li>
	<li>Datasheet:  <a href="http://www.vmware.com/files/pdf/vchs/vCloud-Hybrid-Service-Datasheet.pdf">http://www.vmware.com/files/pdf/vchs/vCloud-Hybrid-Service-Datasheet.pdf</a></li>
	<li>FAQ:  <a href="http://www.vmware.com/files/pdf/vchs/vCloud-Hybrid-Service-FAQ.pdf">http://www.vmware.com/files/pdf/vchs/vCloud-Hybrid-Service-FAQ.pdf</a></li>
	<li>Service Level Agreements:  <a href="http://www.vmware.com/support/product-support/vcloud-hybrid-service/sla.html">http://www.vmware.com/support/product-support/vcloud-hybrid-service/sla.html</a></li>
	<li>Terms of Service:  <a href="http://www.vmware.com/support/product-support/vcloud-hybrid-service/terms-of-service.html">http://www.vmware.com/support/product-support/vcloud-hybrid-service/terms-of-service.html</a></li>
	<li>Support:  <a href="http://www.vmware.com/support/services/iaas-production.html">http://www.vmware.com/support/services/iaas-production.html</a></li>
</ul>
Here is a video from the beta service that shows how easy it is to deploy a new server:

<iframe src="http://www.youtube.com/embed/ooTine8PafQ" height="315" width="420" allowfullscreen="" frameborder="0"></iframe>