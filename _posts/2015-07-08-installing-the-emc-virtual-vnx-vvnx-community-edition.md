---
ID: 3850
post_title: >
  Installing the EMC Virtual VNX (vVNX)
  Community Edition
author: Jonathan Frappier
post_date: 2015-07-08 08:00:46
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/installing-the-emc-virtual-vnx-vvnx-community-edition/
published: true
dsq_thread_id:
  - "3915192840"
---
*<em>*Disclaimer: I am an EMC employee, this post was not sponsored or in any way required by my employer, it is my experience getting to know this particular product.**</em>

The virtual VNX was announced at EMC World in May of 2015, and is a free to use, software only version of the VNXe. <a href="http://www.emc.com/products-solutions/trial-software-download/vvnx.htm" target="_blank">More details on the vVNX can be found at the ECN</a>.

A few requirements for the vVNX: you'll need to provide the virtual machine with 2 vCPU and 12GB of RAM (I'll test that as well) and you can present up to 4TB of storage. This is a great lab solution as well as a way to test upgrades or changes to your production VNX arrays (I know I never had budget to buy additional arrays for testing). Before you get started, <a href="http://www.emc.com/products-solutions/trial-software-download/vvnx.htm" target="_blank">download the vVNX bits</a> (http://www.emc.com/products-solutions/trial-software-download/vvnx.htm) which is provided as an OVA.

1.  Once the OVA has been downloaded, log into vCenter and start the Deploy OVF Template wizard. In the image below, you can see I am deploying to an existing vApp but you could do this to an individual ESXi host or cluster as well.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/07/1.deploy-ova.png"><img class="aligncenter size-full wp-image-3854" src="http://www.virtxpert.com/wp-content/uploads/2015/07/1.deploy-ova.png" alt="1.deploy-ova" width="365" height="428" /></a>

2.  Once you select the OVA package, you'll be prompted to accept the extra configuration options; click the check box, click Next, and accept the EULA

<a href="http://www.virtxpert.com/wp-content/uploads/2015/07/2.accept-config.png"><img class="aligncenter size-full wp-image-3857" src="http://www.virtxpert.com/wp-content/uploads/2015/07/2.accept-config.png" alt="2.accept-config" width="970" height="570" /></a>

3.  In section 2 of the wizard, you will name your virtual VNX and select the appropriate resources such as storage, and configure networks.

4.  The network setup (2c) includes 3 interfaces; 1 for management and 2 for data. Select the appropriate port groups and click next. As you can see below I select two different port groups for this.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/07/3.network-setup.png"><img class="aligncenter size-full wp-image-3858" src="http://www.virtxpert.com/wp-content/uploads/2015/07/3.network-setup.png" alt="3.network-setup" width="967" height="569" /></a>

5.  In step 2d you will set the system name, as well as expand the IPv4 section to provide the management IP information as pictured below, of course that is valid in your environment. If using DHCP, leave these values blank

<a href="http://www.virtxpert.com/wp-content/uploads/2015/07/4-mgmt-network.png"><img class="aligncenter size-full wp-image-3859" src="http://www.virtxpert.com/wp-content/uploads/2015/07/4-mgmt-network.png" alt="4-mgmt-network" width="971" height="569" /></a>

6. Click next, check the box to Power on after deployment and click Finish. After the vVNX deploys, it will boot and start its initial configuration which can take some time. You can watch the setup process via the console to know when it has completed, for me I started the OVA deployment at 1:25p and it was completed within about 20 minutes (I also wasn't paying very close attention)

7.  With the Virtual VNX powered on, add more virtual disks to the VM; this would mimic having physical drives in your array. The number of drives you add will depend on your use case. I've added 4x 250GB drives. Do not remove the 22, 30, or 32GB drives that were already created from the VM deployment.

8.  Navigate to the IP address you set during installation and log in as as admin with a default password of Password123# to start the Unisphere Configuration Wizard (note in may take several minutes after the initial setup for the login page to be available)

<a href="http://www.virtxpert.com/wp-content/uploads/2015/07/5.unisphere-config-wiz.png"><img class="aligncenter size-full wp-image-3864" src="http://www.virtxpert.com/wp-content/uploads/2015/07/5.unisphere-config-wiz.png" alt="5.unisphere-config-wiz" width="647" height="562" /></a>

9.  The first 2 steps are pretty straight forward; accept the EULA, and enter a new password (keep the service password box checked)

10.  When you get to the license screen, you will need to switch gears for a minute and navigate to https://www.emc.com/auth/elmeval.htm and enter the System UUID in the configuration wizard

<a href="http://www.virtxpert.com/wp-content/uploads/2015/07/6.uuid_.jpg"><img class="aligncenter size-full wp-image-3865" src="http://www.virtxpert.com/wp-content/uploads/2015/07/6.uuid_.jpg" alt="6.uuid" width="647" height="557" /></a>

11. Download the license key file that is generated, and upload it in Unisphere using the Install License File button

<a href="http://www.virtxpert.com/wp-content/uploads/2015/07/7.download.jpg"><img class="aligncenter size-full wp-image-3866" src="http://www.virtxpert.com/wp-content/uploads/2015/07/7.download.jpg" alt="7.download" width="996" height="443" /></a>

12.  You should see a message that the License file installed successfully

<a href="http://www.virtxpert.com/wp-content/uploads/2015/07/8.lic-file-installed.png"><img class="aligncenter size-full wp-image-3867" src="http://www.virtxpert.com/wp-content/uploads/2015/07/8.lic-file-installed.png" alt="8.lic-file-installed" width="647" height="562" /></a>

13.  Next, select the appropriate DNS and NTP configuration for your network

14.  Create your initial storage pool, you can create others later as well. I have opted to create one called CloudStorage and added the 4x 250GB drives I added previously and assigned a tier.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/07/9.storage-pool.png"><img class="aligncenter size-full wp-image-3870" src="http://www.virtxpert.com/wp-content/uploads/2015/07/9.storage-pool.png" alt="9.storage-pool" width="654" height="643" /></a>

15.  Next, configure your iSCSI interfaces, for example ETH0

<a href="http://www.virtxpert.com/wp-content/uploads/2015/07/10.iscsi_.png"><img class="aligncenter size-full wp-image-3873" src="http://www.virtxpert.com/wp-content/uploads/2015/07/10.iscsi_.png" alt="10.iscsi" width="646" height="558" /></a>

16.  The remaining steps are optional. If you would like to use NFS, you can do so in step 9 and replication in step 10. Click Finish to complete the wizard.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/07/11.finish.png"><img class="aligncenter size-full wp-image-3874" src="http://www.virtxpert.com/wp-content/uploads/2015/07/11.finish.png" alt="11.finish" width="647" height="555" /></a>

At this point, if you have not done so already you will need to configure a vmkernel port on your ESXi hosts on the same network as the storage interface(s). Once that is done, you should be able to go to Storage &gt;&gt; LUN and create a new LUN. For example here you can see the ESXi host I added to the vVNX while creating a LUN.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/07/12.add-lun.png"><img class="aligncenter size-full wp-image-3875" src="http://www.virtxpert.com/wp-content/uploads/2015/07/12.add-lun.png" alt="12.add-lun" width="753" height="642" /></a>

In my next post, I will be seeing if I can add the vVNX to a ViPR Virtual Array...stay tuned.

<strong>*Update: It appears the vVNX ships with a version of SMI-S that is not currently supported by ViPR. While it will initially discover the vVNX it fails on subsequent discovers for both file and block**</strong>

&nbsp;