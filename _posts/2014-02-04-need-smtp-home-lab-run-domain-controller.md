---
ID: 1916
post_title: >
  Need SMTP for your home lab? Why not run
  it on your Domain Controller?
author: Jonathan Frappier
post_date: 2014-02-04 07:57:10
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/need-smtp-home-lab-run-domain-controller/
published: true
dsq_thread_id:
  - "2219613959"
---
Some tweets crossed the stream today about the need for an SMTP server in the home lab, so figured if others are asking its a worthy blog post.  A oft forgotten feature of Windows 2008/2012 is that there is an SMTP server available in Windows, no need for Exchange, Postfix or any SMTP application.  You could run this on any Windows server in your lab, so on a Domain Controller or your vCenter server if you aren't using the <a href="http://www.virtxpert.com/tag/vcsa/">VCSA</a>.  The SMTP server is easy to enable as you'll see here.
<ul>
	<li>Click on <span style="color: #3366ff;"><strong>Start</strong></span>, right click <span style="color: #3366ff;"><strong>Computer</strong> </span>and select <span style="color: #3366ff;"><strong>manage</strong></span></li>
	<li>Click on <span style="color: #3366ff;"><strong>Features</strong></span>, and then <strong><span style="color: #3366ff;">Add Feature</span></strong></li>
	<li>Click on <strong><span style="color: #3366ff;">SMTP Server</span>, </strong>then click on <span style="color: #3366ff;"><strong>Add Required Role Services</strong></span> to install the necessary components to manage it (it uses the IIS 6.0 Manager)</li>
	<li>Once finished, click on <span style="color: #3366ff;"><strong>Start &gt;&gt; Administrative Tools  &gt;&gt; Internet Information Services (IIS) 6.0 Manager</strong></span></li>
	<li>Expand the computer and you will see your SMTP server</li>
</ul>
You'll now want to make sure settings are in place to allow it to be used by your various VMs to send mail through
<ul>
	<li>Right click on <span style="color: #3366ff;"><strong>SMTP Virtual Server</strong></span> and select <span style="color: #3366ff;"><strong>Pr</strong><strong>operties</strong></span></li>
	<li>Click on the Access Tab, click the Authentication button and make sure <span style="color: #3366ff;"><strong>Anonymous</strong> </span>is selected, or another option such as <span style="color: #3366ff;"><strong>Basic</strong> </span>if you wish to configure your SMTP agents to authenticate with the SMTP service</li>
	<li>Click on Relay and select only the list below and enter the network/subnet of the machines that will be connecting.  You could even do this on a per server basis.  For example maybe you only want vCenter to send emails so you could just enter the vCenter IP.</li>
</ul>
<strong>Summary</strong>

That's about it, pretty easy.  Add a feature, its required supporting role features and lock it down to something acceptable for you.  Obviously for production purposes, you want to be more careful with your security settings.