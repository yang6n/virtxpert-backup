---
ID: 1630
post_title: >
  Getting started with PHD Virtual
  ReliableDR
author: Jonathan Frappier
post_date: 2014-01-06 07:43:13
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/getting-started-phd-virtual-reliabledr/
published: true
dsq_thread_id:
  - "2095328527"
---
ReliableDR from PHD Virtual, now Unitrends is an application that "helps assure business continuity by automating the disaster recovery process to dramatically reduce the cost and complexity of fail over, fail back and testing.  Now you can certify your VMs will recover as planned, and within corresponding SLAs."  That's the marketing version, what does it mean for an engineer/administrator?  Its a tool that allows you to test your DR plan, pretty straight and simple, then when you actually need to perform your DR plan it provides the tools needed to automate that process as well as the process to fail back, which is generally the harder process of the two!

Installing ReliableDR was amazingly simple and complete, you will need a Windows 2008 OS or greater; you can't install on Win7 for example, and from there the installer handles all of the dependencies such as .NET 4.0 and IIS 7.  I haven't come across many applications recently where even the installation process was so well done and documented.
<ul>
	<li>Download and start the installer from PHD Virtual</li>
	<li>Next, Accept/Next, Next</li>
	<li>Here if you do not have IIS 7 installed, the ReliableDR installer configures that for you, Next</li>
	<li>You will then be prompted on whether to use a local SQL instance or an existing ReliableDR instance, selecting to use a new local instance will configure the ReliableDR database (when is it appropriate to use a separate SQL server - N number of Hosts? VMs? Data?)</li>
	<li>Option to change components, which appears to be no options to change, but just click Next</li>
	<li>Select your path for the web services, Next</li>
	<li>Select the IP(s) and ports you wish ReliableDRs web services to run on, Next (the installer will also stop the Default Web Site)</li>
	<li>Next to start all the bits moving around for the installer to configure the service.</li>
	<li>The installer went though and completed the installation, now click Finish.</li>
</ul>
Once the installation is complete there will be a ReliableDR shortcut on the desktop which will connect you to the web UI, the default username is Admin / password.
<p style="text-align: center;"><a href="http://www.virtxpert.com/wp-content/uploads/2013/12/reliableDR.jpg"><img class="aligncenter  wp-image-1638" alt="reliableDR" src="http://www.virtxpert.com/wp-content/uploads/2013/12/reliableDR.jpg" width="559" height="416" /></a></p>
Once you are logged in, you do need to hop around a bit as no wizard was presented, but its a very straight forward process to configure.
<ul>
	<li>Click on Servers and then click the Add button</li>
	<li>Add your vCenter servers, and credentials for each and click save.  If you only have one for testing or POC just enter that vCenter.</li>
	<li>For testing you may want to create an isolated network/vSwitch.</li>
	<li>Click on Mappings and click the Add button</li>
	<li>Select the primary and secondary server based on your use case and click Next</li>
	<li>Under each vCenter, click the link that says "Mapping not set, click to change"</li>
	<li>Here you can see I selected my VM Network and IsolatedDR next I created for testing.</li>
</ul>
<p style="text-align: center;"><a href="http://www.virtxpert.com/wp-content/uploads/2013/12/reliabledrmapping.jpg"><img class="aligncenter  wp-image-1641" alt="reliabledrmapping" src="http://www.virtxpert.com/wp-content/uploads/2013/12/reliabledrmapping.jpg" width="633" height="418" /></a></p>

<ul>
	<li>Click OK, click Next</li>
	<li>Select the failbox network, this is likely the opposite of what you selected above.  Click OK and Next.</li>
	<li>Name your mapping and click Save.</li>
	<li>Click on Jobs, here there was no Add button like there was for Mappings (maybe a bug?) but if you right click on Jobs you will get the Add job button; click that.</li>
	<li>You will have 3 options here, the first however will be to setup ReliableDR replication.</li>
	<li>Select your source and replication server, click Next.</li>
	<li>Select your mapping that we just created and click Next.</li>
	<li>Select the VM you wish to protect, and drag the VM to the datastore on the right you wish to replicate to, repeat for each VM and click Next.</li>
	<li>Name and review your job options such as RTO and RPO and click Save.</li>
</ul>
Now you are all set to run your first test!  Just click on the job, click the Actions button and select Run Test.  You will see the status of your replication and....

<a href="http://www.virtxpert.com/wp-content/uploads/2013/12/reliableDRreplication.png"><img class="aligncenter size-large wp-image-1644" alt="reliableDRreplication" src="http://www.virtxpert.com/wp-content/uploads/2013/12/reliableDRreplication-1024x357.png" width="640" height="223" /></a>

&nbsp;

<strong>Summary</strong>

In less than an hour I installed the product, configured for my environment and was able to successfully test a DR scenario.  I can't think of many tasks that only occupy and hour of your time at work that are more worthwhile than building a DR solution, ReliableDR makes it that easy!

<a href="http://www.virtxpert.com/wp-content/uploads/2013/12/reliabledrtestsucess.png"><img class="aligncenter size-large wp-image-1646" alt="reliabledrtestsucess" src="http://www.virtxpert.com/wp-content/uploads/2013/12/reliabledrtestsucess-1024x404.png" width="640" height="252" /></a>

You can find all the current documentation at <a href="https://phdreliabledr.zendesk.com/entries/24880616-ReliableDR-Installation-and-Configuration-Guide">https://phdreliabledr.zendesk.com/entries/24880616-ReliableDR-Installation-and-Configuration-Guide</a>