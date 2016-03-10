---
ID: 1328
post_title: Editing a VMX file
author: Jonathan Frappier
post_date: 2013-09-03 09:49:46
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/editing-vmx-file/
published: true
dsq_thread_id:
  - "1701173483"
---
One of the things I love about Twitter is being able to just happen upon a conversation that gives you some knowledge you can tuck away for when you need it.  Once example was a conversation started by Jason Boche, Jason had run into an issue where he needed to edit the settings of a Virtual Machine (VM) but was unable to.  Apparently the older C# vSphere client is unable to edit the virtual machine configuration for the new vSphere 5.5 version 10 hardware, you can only do this via the web client (later confirmed that this was "by design" by Duncan Epping in the same Twitter thread).  VMware, for the last year or so, has been moving towards making the web client the standard and have further pushed this with vSphere 5.5.  One problem arises in this scenario though, you still need the C# client to get your environment up and running, at least if you are building from scratch (I need VMs for AD, vCenter, SSO, and the web client etc...), or how about a scenario where vCenter or the the web client is unavailable - what then?

All of a VM's settings are stored with a file with an extension of .VMX.  I<em><strong> don't typically suggest editing this file manually</strong></em>, but it appears (at least with 5.5 in beta) that this will be a skill VMware admins should hone, or at least bookmark a few handy blog sites for reference.  I'll assume for purposes of this post that you are using the C# client because the web client is unavailable (otherwise just edit with the web client).  There are other advanced troubleshooting reasons where you may need to edit a .VMX file manually but it was this particular Twitter conversation that got me thinking it would be handy to document.
<ul>
	<li>Start the vSphere (C#) client and power off the VM if it is not already powered off.  Also remove the VM from inventory by right clicking and select remove from inventory.</li>
	<li>Navigate to Datastores and Datastore Clusters.  If the VM is stored on local storage, you could also browse the datastore from the Hosts and Clusters &gt;&gt; ServerName &gt;&gt; Configuration &gt;&gt; Storage view</li>
	<li>Right click the datastore where the VM is stored and select Browse Datastore.  Find the folder of your virtual machine.</li>
	<li>Highlight the .vmx file and click the download button.  Make a copy so you can revert easily if need be.</li>
	<li>Open the .vmx file in your favorite text editor and make the desired changes.</li>
	<li>Upload the new file and re-add the VM to inventory.</li>
</ul>
What you will need to change within the file will depend on your specific scenario for why you are editing it in the first place.  Maybe you need to change the name of the network the VM is connecting to, in this scenario look for something similar to:
<pre>ethernet0.networkName = "VM Network"</pre>
And edit that for your environment.  **Updated** As William Lam pointed out on Twitter, there are other ways to change VM settings such as using PowerCLI or the vMA, however this post is assuming that these tools are not working or not available.  The example above, changing the VM network, is one or the more basic examples I could think of that most admins could relate to.  As I mentioned, what you would actually have to edit will be unique to your specific scenario.  VMware, as you might come to expect, has a few good KB articles on editing a .vmx files for different use cases:
<ul>
	<li><a href="http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&amp;cmd=displayKC&amp;externalId=1714" target="_blank">Tips for editing a VMX file</a></li>
	<li><a href="http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&amp;cmd=displayKC&amp;externalId=1023880" target="_blank">Rebuilding a VMX file from vmware.log</a></li>
	<li><a href="http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&amp;cmd=displayKC&amp;externalId=2011654" target="_blank">Changing the boot order of a VM</a></li>
</ul>
I am hoping that the ability to edit a VM with hardware version 10 is just a beta oversight or bug, but if it does prove to be true editing a .vmx file will become part of all our lives very soon.  I have trouble envisioning a scenario where VMware will bundle the web client into ESXi, but maybe they will release a stand alone appliance where the web client, like the C# client can connect directly to an ESXi hosts?  Lets hope!