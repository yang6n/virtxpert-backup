---
ID: 2281
post_title: 'Providence VMUG PowerCLI Presentation @PVDVMUG #MyVMUG'
author: Jonathan Frappier
post_date: 2014-06-19 14:27:28
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/providence-vmug-powercli-presentation-pvdvmug-myvmug/
published: true
dsq_thread_id:
  - "2778874961"
---
Here is the slide deck from my talk on PowerCLI at the Providence VMUG.  Thanks to Artur and Sebastian for letting me use your script as a reference.

<strong>Key takeaways</strong>
<ul>
	<li>If your KPI for automation projects is saving time, qualify that with "It will save time eventually."  Tasks that take 4-5 hours to do manually/semi-automated could take 6-8 months to fully automate.</li>
	<li>That time trade off is absolutely a smart investment for any company.</li>
	<li>Automation enables IT to become a service provider and is required for standardization and security.  If you do not automate, you are not secure.</li>
	<li>Helps you get a girlfriend or boyfriend</li>
	<li>Free tool, over 370 cmdlets for ESXi/vSphere, View or vCloud Director.  Tons of community resources.</li>
	<li>Simple tasks done manually are error prone, creating a VM takes 33 mouse clicks versus 1 line in PowerCLI (its not a great line but its 1 line)</li>
	<li>Get-Help Get-* | Format-List</li>
	<li>-whatif after a cmdlet ensures you aren't about to blow something up</li>
	<li>Prompt users for input for singular items (cluster name, etc)</li>
	<li>Make use of ForEach loops and pass variables from a CSV (every time I demoed Read-Host I realized this wasn't the best option)</li>
	<li>Indent after { and "de-indent" after }</li>
</ul>
<strong>Slides</strong>

<iframe src="http://www.slideshare.net/slideshow/embed_code/36076572" width="476" height="400" frameborder="0" marginwidth="0" marginheight="0" scrolling="no"></iframe>

You can find the basic live demo script I used <a href="http://www.virtxpert.com/basic-powercli-examples-common-vmware-vsphere-tasks/">here</a>:  <a href="http://www.virtxpert.com/basic-powercli-examples-common-vmware-vsphere-tasks/">http://www.virtxpert.com/basic-powercli-examples-common-vmware-vsphere-tasks/</a>