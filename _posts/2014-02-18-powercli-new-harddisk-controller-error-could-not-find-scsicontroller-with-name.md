---
ID: 1978
post_title: 'PowerCLI New-HardDisk Controller error could not find ScsiController with name &#8220;name&#8221;'
author: Jonathan Frappier
post_date: 2014-02-18 11:57:28
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/powercli-new-harddisk-controller-error-could-not-find-scsicontroller-with-name/
published: true
dsq_thread_id:
  - "2284420091"
---
Excuse the post if its noobish, but I'm getting to know PowerCLI better and had a scenario where someone needed to add a hard drive to a VM with multiple controllers.  The New-HardDisk help file on this wasn't clear as to what it wanted passed for the -Controller option so I figured I could just run
<pre>Get-ScsiController -vm nameofvm</pre>
And it would return the name.  However the command, by default doesn't see to return the controller name so, instead I had to run
<pre>Get-ScsiController -vm nameofvm | format-table - property name, UnitNumber</pre>
So that I could identify the name of the controller, then I could pass the expected value in the New-HardDisk command like so;
<pre>New-HardDisk -VM nameofvm -CapacityGB 5 -StorageFormat thin -Controller "name from Get-ScsiController cmdlet"</pre>