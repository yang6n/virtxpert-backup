---
ID: 2573
post_title: Hands on (lab) with EVO:RAIL
author: Jonathan Frappier
post_date: 2014-09-11 10:18:28
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/hands-on-with-evorail/
published: true
dsq_thread_id:
  - "3008537430"
---
It looks as though the VMware Hands-On Labs from VMworld are starting to roll out.  Short of having a physical EVO:RAIL to work on, I decided to do the next best thing and get some experience with it via the VMware Hands-On labs..  If you want to get some hands on yourself, head over to <a href="http://labs.hol.vmware.com/HOL/catalogs/lab/1503" target="_blank">http://labs.hol.vmware.com/HOL/catalogs/lab/1503</a>.

The HOL starts with the assumption that you have a working network and IP scheme, your top-of-rack switch is configured and your EVO:RAIL is connected and powered on (likely also assumes you have NTP and DNS working since those are critical to any environment and should never be skipped).
<ul>
	<li> Open a browser and navigate to the EVO:RAIL home page.  Click the Yes, Let's Go! button and accept the EULA by clicking the Yes, I do button</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/09/evo-rail-start.jpg"><img class="aligncenter  wp-image-2575" src="http://www.virtxpert.com/wp-content/uploads/2014/09/evo-rail-start.jpg" alt="evo-rail-start" width="642" height="372" /></a>

&nbsp;

<!--more-->

&nbsp;
<ul>
	<li>Click the Customize Me! button to enter your specific IP addresses, hostnames etc.  There is a "Just Go!" button which uses standard configuration options.</li>
	<li>On the next page, you configure host names to use for your ESXi hosts buy entering a prefix so that all hosts start with the same name, an optional separator if you like those in your host name and your iterator.  You also name your vCenter server hostname.  I prefer short names so I'm likely to go with something like vc01.  So with the settings below  you would have a host name of esxi-node01, esxi-node02 etc.  Once finished setting these options, click on the Networking tab.</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/09/evo-rail-config1.jpg"><img class="aligncenter  wp-image-2576" src="http://www.virtxpert.com/wp-content/uploads/2014/09/evo-rail-config1.jpg" alt="evo-rail-config1" width="638" height="394" /></a>
<ul>
	<li>Once you click on the Networking menu, you will have a sub-menu to configure IP pools and VLANs for your management network, vMotion and VSAN networks.  The VLAN option was not available, not sure if that is an HOL thing or they assume connectivity on a default VLAN.  You will also provide your vCenter server networking information and create port groups for VM traffic.  There is an Add a VM Network so you can create as many as you wish.</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/09/evo-rail-config2.jpg"><img class="aligncenter  wp-image-2577" src="http://www.virtxpert.com/wp-content/uploads/2014/09/evo-rail-config2.jpg" alt="evo-rail-config2" width="649" height="402" /></a>
<ul>
	<li>Next, click on the Passwords menu.  Here you set the ESXi host root password and vCenter Server admin password (assuming that is administrator@vsphere.local?).  You can also configure AD authentication as well.  Id like to see an option for different passwords here but without that you can use my <a title="PowerCLI – Update ESXi Root Password with Password Generator" href="http://www.virtxpert.com/powercli-update-esxi-root-password-password-generator/">ESXi password change PowerCLI</a> script to handle that for you.</li>
	<li>The Globals menu allows you to set time/NTP, DNS and logging settings.  You can chose either a general syslog server or vCenter Log Insight.</li>
	<li>Finally, click on the Validation menu, or the Validate button to ensure you have a valid EVO:RAIL configuration.  Once validated, click the Build Appliance button.</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/09/evo-rail-validate.jpg"><img class="aligncenter size-full wp-image-2579" src="http://www.virtxpert.com/wp-content/uploads/2014/09/evo-rail-validate.jpg" alt="evo-rail-validate" width="442" height="328" /></a>

&nbsp;
<ul>
	<li>With the EVO:RAIL configuration complete, make note of the IP address and click the Take me to it button to monitor the setup of your EVO:RAIL appliance</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/09/evo-rail-building.jpg"><img class="aligncenter  wp-image-2580" src="http://www.virtxpert.com/wp-content/uploads/2014/09/evo-rail-building.jpg" alt="evo-rail-building" width="656" height="398" /></a>

&nbsp;
<ul>
	<li>Once its finished, HOORAY!  Click the link to go to the EVO:RAIL log in</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/09/evo-rail-hooray.jpg"><img class="aligncenter  wp-image-2585" src="http://www.virtxpert.com/wp-content/uploads/2014/09/evo-rail-hooray.jpg" alt="evo-rail-hooray" width="637" height="393" /></a>

&nbsp;
<ul>
	<li>Log into your EVO:RAIL and start managing!</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/09/evo-ui.jpg"><img class="aligncenter  wp-image-2586" src="http://www.virtxpert.com/wp-content/uploads/2014/09/evo-ui.jpg" alt="evo-ui" width="645" height="364" /></a>

&nbsp;

From the EVO:RAIL UI you can do basic tasks such as create VMs and monitor the health of your environment as well as current/recent tasks.  You can also launch vCenter from this US to perform more advanced vSphere tasks that you cannot (currently?) do in the EVO:RAIL UI.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/09/evo-nav.jpg"><img class="aligncenter size-full wp-image-2588" src="http://www.virtxpert.com/wp-content/uploads/2014/09/evo-nav.jpg" alt="evo-nav" width="1015" height="573" /></a>

It will be interesting to see the differentiation between various EVO:RAIL partners such as EMC and Dell.  As Chad Sakac mentioned at VMworld the EMC EVO:RAIL will have the ability to connect to EMC support and should come with RecoverPoint for VMs (<a href="http://www.emc.com/storage/recoverpoint/recoverpoint-for-virtual-machines.htm" target="_blank">EMC page</a> | <a title="Introducing EMC RecoverPoint for VMs #VMworld #EMCElect" href="http://www.virtxpert.com/introducing-emc-recoverpoint-vms-vmworld-emcelect/" target="_blank">my coverage</a>).  Sincere thanks to the VMware HOL team, having these resources available for the community to use on demand, whenever they are free is a great for the community.