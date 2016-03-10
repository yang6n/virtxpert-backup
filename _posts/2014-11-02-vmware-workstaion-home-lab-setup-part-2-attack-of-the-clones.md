---
ID: 2732
post_title: 'VMware Workstation Home Lab Setup Part 2 &#8211; Attack of the Clones'
author: Jonathan Frappier
post_date: 2014-11-02 08:00:32
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vmware-workstaion-home-lab-setup-part-2-attack-of-the-clones/
published: true
dsq_thread_id:
  - "3183231482"
---
[display-posts category="Lab Series" display-posts posts_per_page="15"]

Now that you have your first Windows VM built and patched, you're probably itching to get things built like turning the virtual machine it into your domain controller for the home lab which will be used for authentication throughout this setup.  However, we want to be efficient with our time so we are going to take our Windows VM and use it to clone new VMs since at the very least I will need 3 Windows virtual machines for this lab; a Domain Controller, SQL server and web server for the vCloud Automation Center/vRealize Automation Infrastructure-as-a-Service server.

So once your Windows VM is fully patched there is one house keeping item to take care of before we use it to clone, and that is to sysprep it.
<ul>
	<li>Log into the Windows VM, in my case a Windows 2012 VM and open the Start menu</li>
	<li>Type C:\Windows\System32\Sysprep\sysprep.exe and press the enter button or click on sysprep.exe in the search bar</li>
	<li>Make sure Enter System Out-ofBox Experience (OOBE) is selected int he System Cleanup Action pull down menu. Next Click on the Generalize checkbox and change the Shutdown Options pull down menu to Shutdown; click OK</li>
	<li>After a few minutes Windows will shut down - don't worry we want the template shutdown as we cannot clone a running VM in VMware Workstation.</li>
</ul>
[caption id="attachment_2741" align="aligncenter" width="640"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/10/windows-sysprep.png"><img class="size-large wp-image-2741" src="http://www.virtxpert.com/wp-content/uploads/2014/10/windows-sysprep-1024x767.png" alt="Windows Sysprep" width="640" height="479" /></a> Windows Sysprep[/caption]

You should now have a powered off virtual machine, I chose to put mine into a folder called Templates though you can organize as you wish.  Before we clone, you want to take a snapshot of the virtual machine.  I know snapshots are bad right?  Not in this case, and actually when doing linked clones such as in vCloud Automation Center / vRealize Automation you would create a snapshot to do blueprints / linked clones from as well.  Right click the Windows virtual machine template and select Snapshot &gt;&gt; Take Snapshot and follow the wizard.  Once complete you will be able to clone from the snapshot but still make edits to the original virtual machine we are using as a template.
<ul>
	<li>Right click on the virtual machine in VMware Workstation and go to Manage &gt;&gt; Clone</li>
	<li>With no snapshots you could will only have the option to "Clone from" The current state in the virtual machine but since we took a snapshot select the "An existing snapshot" radio button, click Next</li>
	<li>One of the cloning process options in VMware Workstation is Create a linked clone, which means you will only have a delta file for changes associated to that virtual machine - that is what I will be using.  Select the Create a linked clone radio button and click Next</li>
	<li>Name the virtual machine and place it in the desired location, in my case I have named it vxprt-dc01 and placed it in V:\VMs\vxprt-dc01\ - click Finish and then close when the Clone virtual machine wizard completes.</li>
</ul>
Since the virtual machine was setup using a linked clone, the cloning process will have finished quickly and be space efficient for the lab environment, you will be ready to boot your VM.  I moved my VM into a folder I created called Lab, you can see my VMware Workstation layout below.

[caption id="attachment_2743" align="aligncenter" width="201"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/10/vmware-workstation-clone.png"><img class="size-full wp-image-2743" src="http://www.virtxpert.com/wp-content/uploads/2014/10/vmware-workstation-clone.png" alt="VMware Workstation folder layout" width="201" height="268" /></a> VMware Workstation folder layout[/caption]

With the VM cloned and powered on, you will be ready to setup your first virtual machine - our domain controller.