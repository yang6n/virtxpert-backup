---
ID: 2821
post_title: 'Importing VCSA via PowerCLI &#8211; VMware Workstation Home Lab Setup Part 10'
author: Jonathan Frappier
post_date: 2014-11-10 10:00:09
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/importing-vcsa-via-powercli-vmware-workstation-home-lab-setup-part-10/
published: true
dsq_thread_id:
  - "3210768322"
---
[display-posts category="Lab Series" display-posts posts_per_page="15"]

In the last post we looked quickly at importing the vCenter Server Appliance through the vSphere Client, however its high time we introduce PowerCLI.  PowerCLI is a set of PowerShell cmdlets to manage your VMware environments (vSphere, vCloud Director and View) and is quite powerful.  So powerful in fact that this is going to be a pretty short post, the 7 bullet points needed just to import the OVF through the vSphere Client is now a single command!

Launch PowerCLI as administrator and run the following to log in:
<pre>connect-viserver 192.168.6.11</pre>
Log in as root when prompted.

Now either change to the directory the OVF is located in or make note of the location for the cmdlet:
<pre>Import-VApp -source .\VMware-vCenter-Server-Appliance-5.5.x.xxxxx-xxxxxxx_OVF.ova -VMhost 192.168.6.11 -DiskStorageFormat thin -name vxprt-vc01</pre>
Below you can see it in console as well as it happening if you were to log into the vSphere Client

[caption id="attachment_2839" align="aligncenter" width="675"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/powercli-import-vapp.png"><img class="wp-image-2839 size-full" src="http://www.virtxpert.com/wp-content/uploads/2014/11/powercli-import-vapp.png" alt="PowerCLI Import-VApp progress" width="675" height="343" /></a> PowerCLI Import-VApp progress[/caption]

[caption id="attachment_2840" align="aligncenter" width="889"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/vsphere-deploying-via-powercli.png"><img class="size-full wp-image-2840" src="http://www.virtxpert.com/wp-content/uploads/2014/11/vsphere-deploying-via-powercli.png" alt="View PowerCLI Import-VApp progress in the vSphere Client" width="889" height="692" /></a> View PowerCLI Import-VApp progress in the vSphere Client[/caption]

1 command - how do you not love PowerCLI?  You can see all of the options available in the <a href="https://www.vmware.com/support/developer/PowerCLI/PowerCLI51/html/Import-VApp.html" target="_blank">Import-VApp cmdlet in the PowerCLI documentation</a>.  Now having shown you those options, I am actually going to run the VCSA in VMware Workstation, simply click File &gt;&gt; Open, select the OVF then provide a name and location.  Power on the VCSA and see my post <a title="Installing the vCenter Server Appliance 5.5.0b #VCSA" href="http://www.virtxpert.com/installing-vcenter-server-appliance-5-5-0b/">here about configuring i</a>t.