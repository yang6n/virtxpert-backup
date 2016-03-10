---
ID: 638
post_title: >
  Building a VMware Horizon Workspace Lab
  – Part 2 vApp Config
author: Jonathan Frappier
post_date: 2013-03-29 15:06:14
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/building-a-vmware-horizon-workspace-lab-part-2/
published: true
dsq_thread_id:
  - "1173064763"
---
In the<a href="http://www.virtxpert.com/building-a-vmware-horizon-lab-part-1/"> first part </a>of this series on setting up VMware Horizon Workspace (thank you to everyone for the RT's on Twitter, certainly more popular than I anticipated) I got the lab basics setup according to the reviewers guide, ensures I had a working vCenter, AD and DNS with reverse look-ups working.  Now its time to get the IP pools setup and import our VMware Horizon vApp.

First, we will setup the IP pools, the <a href="http://www.vmware.com/files/pdf/techpaper/vmware-horizon-workspace-reviewers-guide.pdf" target="_blank">reviewers guide</a> covered this so well I am not going to re-type it all.  As you can see, I have my IP pool configured, but not yet enabled, in vCenter.
<p style="text-align: center;"><a href="http://www.virtxpert.com/wp-content/uploads/2013/03/IPPool.png"><img class="aligncenter  wp-image-639" alt="IPPool" src="http://www.virtxpert.com/wp-content/uploads/2013/03/IPPool.png" width="390" height="330" /></a></p>
<p style="text-align: left;">The next step in the reviewers guide is create the DNS entries, I did this during part one while documenting what my IP address would be.  Also, I downloaded the OVA when I registered for the trial.  Now its time to import the vApp, I am using the Windows client instead of the web client, the reviewers guide walks you through importing via the web client if this is more applicable to  your environment.</p>

<ul>
	<li><span style="line-height: 13px;">Log into vCenter</span></li>
	<li>Click File--&gt;Deploy OVF</li>
	<li>Click Browse and navigate to where the OVA was downloaded and click Next.</li>
	<li>Validate you selected the correct file and that you have adequate resources for it.  Click Next.</li>
	<li>Accept the license agreement and click next.</li>
	<li>Select the appropriate data center and click next.</li>
	<li>Select your cluster and click next, if DRS is not enabled then select your desired host and click next.</li>
	<li>Select your datastore, then disk format.</li>
	<li>In the lab I have limited network connectivity, so I did not have to chose which networks to connect to, but also received an error that multiple source networks are mapped to my VM Network, proceeding as this is my configuration.</li>
	<li>I have selected Fixed IP allocation policy as I will be using the IP addresses we identified and created in DNS.</li>
	<li>Select your time zone and enter the IP information for each of the VMs.</li>
	<li>Next, select Power on after deployment and and then Finish.</li>
</ul>
Now my vApp is being deployed, this could take awhile (10 minutes as I watch the wizard) as there are 14 disks to created.  Because I am using NFS shared storage, it will be thin provisioning all the disks.

<a href="http://www.virtxpert.com/wp-content/uploads/2013/03/deployingvapp.jpg"><img class="aligncenter size-full wp-image-642" alt="deployingvapp" src="http://www.virtxpert.com/wp-content/uploads/2013/03/deployingvapp.jpg" width="571" height="379" /></a>

&nbsp;

After just a few minutes, my vApp was completed successfully.  Be aware, even though we selected the option to turn on the vApp, it only powers on the configurator-va VM (this seems to be expected based on the reviewers guide).  Now onto the initial configuration.  One item that was left out of the beginning of the guide, you are "required" to have an SMTP server, so I have installed it on my domain controller since this is just a lab.  You will also need your vCenter credentials and FQDN as well as AD credentials.
<ul>
	<li>Connect to the console of the configurator-va and hit enter to continue with the setup.</li>
	<li>The configurator validates your DNS entries we created earlier, make sure they match and press Y to continue.</li>
	<li>Enter the password used for the root account on your VMs.  This will be the same across all the VMs.</li>
	<li>Enter the DNS name for SMTP, it cannot be an IP address.</li>
	<li>Change the port if necessary or hit enter.</li>
	<li>Hit enter for the FQDN, note the warning that it cannot be changed later.  I looked through the reviewers guide and I am not sure how this will affect external access which I would like to setup later, but hey having to rebuild all this is at least good practice.</li>
	<li>Enter the IP or hostname for vCenter.</li>
	<li>Enter a vCenter server admin account, this should be in the format of user@domain.tld (not noted in the reviewers guide).</li>
	<li>Verify the info is correct and hit enter.</li>
	<li>The configurator VM will go through and power on each of the vApp VMs. (interesting, creating "base snapshots" - wonder if I need to manage those, don't want them growing out of proportion)</li>
</ul>
Once completed, you should be able to log into your configurator VM web interface as pictured below.  In the next post, I will walk through the web configuration.

<a href="http://www.virtxpert.com/wp-content/uploads/2013/03/configurator.jpg"><img class="aligncenter size-large wp-image-650" alt="configurator" src="http://www.virtxpert.com/wp-content/uploads/2013/03/configurator-1024x537.jpg" width="640" height="335" /></a>