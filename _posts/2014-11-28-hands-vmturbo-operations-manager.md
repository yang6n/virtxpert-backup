---
ID: 3186
post_title: Hands on with VMTurbo Operations Manager
author: Jonathan Frappier
post_date: 2014-11-28 08:00:09
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/hands-vmturbo-operations-manager/
published: true
dsq_thread_id:
  - "3270743799"
---
<em>*Disclaimer - VMTurbo is a sponsor of this blog.  I was not asked to write this post nor was it reviewed prior to being published.  The post simply represents my opinions as it relates to the first time use*</em>

First I would like to thank the folks at VMTurbo for setting up NFR access and inviting me to their community site.  I have never used VMTurbo before, however I have used vCenter Operations manager and Veeam One.  VMTurbo comes as an appliance, I deployed mine in VMware Workstation, powered it on and was able to connect right to the web UI.  Before I log in and get started though, I want to give it the appropriate DNS server IP instead of what DHCP is providing.  Log into the console as ipsetup/ipsetup
<ul>
	<li>Select Static Address Setup by using the tab key then pressing the space bar to select it</li>
	<li>Tab to the IP address field and enter the appropriate information; repeat for all fields</li>
	<li>Press the tab key until you get to OK then press the space bar again</li>
	<li>Now, create a DNS entry in your forward and reverse lookup zone</li>
</ul>
You should now be able to navigate to the VMTurbo UI with the new IP address or FQDN.  The initial login is administrator/administrator (though as the UI suggests you probably want to change that).  Once logged in for the first time, you will run through an initial setup wizard.
<ul>
	<li>First, provide your license key which arrives as an XML file.  In my case since I had the license key I selected the I have a license key and pasted the XML I received with the key into the text box</li>
	<li>Once the license key is accepted, click next</li>
	<li>On the Target Configuration screen click Add</li>
	<li>Here you chose the type of system you want to monitor, I have selected vCenter and entered my vCenter server information.  Once everything is entered, click the Save button</li>
	<li>Add any additional systems you wish to monitor and click Next</li>
	<li>Enter your email credentials if you have them and click Finish</li>
</ul>
Right away VMTurbo is able to look at resource utilization in the environment, as you can see from the charts below.

[caption id="attachment_3187" align="aligncenter" width="1274"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/vmturbo-ui.png"><img class="size-full wp-image-3187" src="http://www.virtxpert.com/wp-content/uploads/2014/11/vmturbo-ui.png" alt="VMTurbo Dashboard" width="1274" height="909" /></a> VMTurbo Dashboard[/caption]

You can click through the various tabs in the UI to see different information, for example on the Suppy Chain tab I can see a map of my infrastructure.  Using the navigator I can click on the components in my environment and instantly get information about that resource.  For example here I clicked on Storage and can see my vxprt-esxi01-gold-local datastore is about about 60% utilization.

[caption id="attachment_3188" align="aligncenter" width="688"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/vmturbo-navigator.png"><img class="size-full wp-image-3188" src="http://www.virtxpert.com/wp-content/uploads/2014/11/vmturbo-navigator.png" alt="VMTurbo Navigator" width="688" height="502" /></a> VMTurbo Navigator[/caption]

Beyond just monitoring, VMTurbo can also make recommendations about how to improve the environment.  For example if you had a host over utilized, it could generate recommendations on how to resolve the problem and take action on it.  I can also use VMTurbo to perform deployments; one thing I found interesting was that in addition to my existing vSphere templates, there were several already defined such as Microsoft_IIS-small which can help you determine the best location for a virtual machine and use the template to deploy the virtual machine.

I am really excited to watch VMTurbo in my lab over the next few days.  It was by far the simplest deployment of this type of system that I have ever done - within minutes it was monitoring my environment.  A lab may not be the best litmus test for VMTurbo, but given the ease of install and the fact it does not need any agents you may want to go ahead and see what it finds in a larger test or production environment.  I'll keep you posted on what other cool things I find as I explore the many options in VMTurbo Operations Manager.