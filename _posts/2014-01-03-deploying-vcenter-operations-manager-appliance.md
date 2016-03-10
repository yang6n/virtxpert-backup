---
ID: 1753
post_title: >
  Deploying the vCenter Operations Manager
  appliance
author: Jonathan Frappier
post_date: 2014-01-03 12:04:34
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/deploying-vcenter-operations-manager-appliance/
published: true
dsq_thread_id:
  - "2089819187"
---
vCenter Operations Manager (vCOPS) is being pushed heavily right now by VMware, at least by my rep, and with good reason.  vCOPS is an advanced monitoring tool that provides insight, monitoring and alarms for your vSphere environment.  If you are licensed for any version of vSphere, then you are licensed for at least the vCOPS Foundation Edition, there are other editions which provide more features.  You can find details on all of the various features here:  <a href="http://www.vmware.com/products/vcenter-operations-management/compare.html">http://www.vmware.com/products/vcenter-operations-management/compare.html</a>

Before you get started, there are a couple of requirements you will need some planning on before you start.  If you do not have DRS enabled (and do not have Enterprise Plus so you can't enable it) you will need an ESXi host that is not in a cluster to deploy the OVF.  This is a known issue per <a href="http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&amp;cmd=displayKC&amp;externalId=2013695  " target="_blank">KB 2013695</a>.  You will have to evacuate all VMs from a host, place the host into maintenance mode and move it out of the cluster.  You should also have a service account ready to connect vCOPS to vCenter, at first glance I don't see anything in the documentation that specifies which role is required, I'm going forward for this test with a user that has full admin privileges.

Once you have an available host, either in a DRS enabled cluster or isolated, the OVF deployment is otherwise straight forward.  Follow the wizard, select your deployment size - small, medium, or large.  You will need to ensure you have an appropriate amount of resources based on your selection
<ul>
	<li>Small (less than 1500 VMs): 4 vCPU and 16GB RAM</li>
	<li>Medium (1500-3000 VMs): 8 vCPU 25GB RAM</li>
	<li>Large (greater than 3000 VMs): 16 vCPU and 24GB RAM</li>
</ul>
Chose how you wish to assign IPs (DHCP or Manual), I opted for fixed so I could assign the IP information myself.  When I deployed the OVF via the vSphere Web Client, it had me set the network mask, DNS servers and Gateway.  Because of some problems with the web client, I had to fall back to the C# client and I was only prompted to enter the IP address for each of the two VMs.

Once the OVF is deployed, you will have a vApp containing 2 different VMs.  You may want to review each of the VMs to ensure they were assigned the amount of resources you expected.  Power on the vApp, the Analytics VM will power on, followed by the UI VM - very similar to a multi-tier web app.  As I mentioned in my article about deploying the VCSA, setting the IP information manually does not work with the C# client during an OVF deployment, so check the IP address of the UI VM.  You may even want to log in and configure the appropriate IP information for each.  The first boot of the Analytics VM is fairly quick, however the UI VM takes quite a bit of time as it is performing an initial setup/import of various components.
<p style="text-align: center;"><a href="http://www.virtxpert.com/wp-content/uploads/2014/01/vcops-setup.png"><img class="aligncenter  wp-image-1764" alt="vcops-setup" src="http://www.virtxpert.com/wp-content/uploads/2014/01/vcops-setup.png" width="446" height="151" /></a></p>
Once the VM booted up, and provided the IP address I was able to navigate to to the vCenter Operations Manager Administration page at the IP of the UI VM.
<p style="text-align: center;"><a href="http://www.virtxpert.com/wp-content/uploads/2014/01/vcops-admin.png"><img class="aligncenter  wp-image-1766" alt="vcops-admin" src="http://www.virtxpert.com/wp-content/uploads/2014/01/vcops-admin.png" width="497" height="225" /></a></p>
Log in with the default username and password of admin / admin.  You will be logged in and start the Initial Setup Wizard.
<ul>
	<li>Enter the IP  of your vCenter server and a user with access to the server (I'm unclear right now if this needs to have admin access, assuming so for the time being) and click Next.</li>
	<li>Click yes to accept the SSL cert of vCenter</li>
	<li>Update the admin and root account passwords.  The default admin password is admin (same as you used to log in to the web admin) and the default root password is vmware.</li>
	<li>Re-enter the vCenter server details you wish to monitor, this is a bit confusing as you were asked previously for the vCenter hosting the vAPP, but none the less it is required.</li>
	<li>On my vCenter, there were no plugins, so nothing to do here for me other than click next.</li>
	<li>Finially, I do not have vCenter in linked mode, so here I just clicked finished.</li>
</ul>
Now that the initial configuration is complete, you should be able to log into the vCOPS Manager UI at the IP/Host name of your UI VM with a username with access to your vCenter server.
<p style="text-align: center;"><a href="http://www.virtxpert.com/wp-content/uploads/2014/01/vcops-ui-login.png"><img class="aligncenter  wp-image-1770" alt="vcops-ui-login" src="http://www.virtxpert.com/wp-content/uploads/2014/01/vcops-ui-login.png" width="397" height="341" /></a></p>
 From here you can start to drill into various parts of your environment and see information that vCOPS is collecting.  Over time, of course, more details will be available to give you a better understanding of your environment.

VMware also has a deployment guide available with more detail than the quick walk through I provided available here:  <a href="https://www.vmware.com/pdf/vcops-vapp-57-deploy-guide.pdf" target="_blank">https://www.vmware.com/pdf/vcops-vapp-57-deploy-guide.pdf</a>

&nbsp;