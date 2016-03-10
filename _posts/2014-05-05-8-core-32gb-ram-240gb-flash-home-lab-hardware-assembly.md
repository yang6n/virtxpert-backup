---
ID: 2194
post_title: >
  8-Core, 32GB RAM, 240GB Flash Home Lab
  Hardware Assembly
author: Jonathan Frappier
post_date: 2014-05-05 08:19:34
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/8-core-32gb-ram-240gb-flash-home-lab-hardware-assembly/
published: true
dsq_thread_id:
  - "2658753174"
---
A while back I wrote about a couple of options for building a single, powerful desktop capable of running a nested ESXi lab (<a title="Quad-Core, 32GB RAM, 240GB Flash, 2TB, Dual-NIC Home Lab Part List" href="http://www.virtxpert.com/quad-core-32gb-ram-240gb-flash-2tb-dual-nic-home-lab-part-list/">4-core</a> &amp; <a title="8-Core, 32GB RAM, 360GB Flash, 3TB, Dual-NIC Home Lab Part List" href="http://www.virtxpert.com/8-core-32gb-ram-360gb-flash-2tb-dual-nic-home-lab-part-list/">8-core</a>), these are my notes about that home lab hardware assembly.  The 8-core post has remained fairly up to date, I made a few revisions between conception and actual assembly including changing out the NICS to HP dual-port NC7170.  Also, hindsight being what it is, I think I'd likely opt for 3x 1TB SATA drives versus 4x 500GB hybrid drives.

One item I was unsure of witht he AMD FX-8320 CPU was whether it supported RVI so I could boot 64-bit OS VMs from a nested ESXi VM.  Thanks to <a href="http://www.virtuallyghetto.com/2012/08/how-to-enable-nested-esxi-other.html" target="_blank">this post from William Lam</a> I was able to confirm that, in fact, the CPU does support this feature.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/05/nested-true.png"><img class="aligncenter size-medium wp-image-2206" src="http://www.virtxpert.com/wp-content/uploads/2014/05/nested-true-300x116.png" alt="nested-true" width="300" height="116" /></a>

<strong>Other home lab options</strong>

I had also looked at a few other options for setting up a usable home lab such as Dell C6100’s from eBay which are single 2U units with multiple “sled” style servers, smaller HP MicroServer boxes and even tried refurbished high end Dell Precision workstations. What I was never comfortable with for any of those options was the amount of electricity draw to use them, and overheating issues when leaving them running all day; thus I landed on the single server environment.

<strong>Physical assembly</strong>

Assembling the hardware is pretty straight forward.  A few notes with this specific hardware, however, are in order.

This motherboard (as well as a Biostar TA970 that I also tried) aren’t quite as wide as a normal ATX motherboard... that or I missed some type of spat between motherboard and case manufactures (I also tried a second case with the same results).  Since the motherboard doesn’t reach the standoffs in the middle of the case you’ll need to provide it with some support.  When connecting the power supply and installing the RAM and SATA cables, you’ll want to place your index fingers under the motherboard for support and push down with your thumbs to make sure you do not damage the case.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/05/img2.jpg"><img class="aligncenter size-large wp-image-2196" src="http://www.virtxpert.com/wp-content/uploads/2014/05/img2-1024x577.jpg" alt="img2" width="640" height="360" /></a>

&nbsp;

As you can see in the image above, the case provides ample space to run the cables behind the mounting plate for the motherboard.  Not only does this help keep the inside of the case neat, but its actually required. When installing the hard drives into the 3.5” bays, the SATA and power connectors will need to face the inside of the case as seen here.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/05/img3.png"><img class="aligncenter size-full wp-image-2197" src="http://www.virtxpert.com/wp-content/uploads/2014/05/img3.png" alt="img3" width="362" height="317" /></a>

The HP NC7170 NICs are installed in the bottom two PCI slots, with the PNY video card installed in the PCI-E slot just above them. The small card near the battery is a SYBA dual port NIC that uses a Realtek chipset (same that is on the motherboard).  The Realtek chipset is not supported out of the box, but later we will look at how to install the VIB for these.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/05/img4.jpg"><img class="aligncenter size-full wp-image-2198" src="http://www.virtxpert.com/wp-content/uploads/2014/05/img4.jpg" alt="img4" width="446" height="791" /></a>

The PCI-E slot (slot #4 in the motherboard manual) that the video card is installed in runs at 4x, and since this is a low end video card I wanted to keep the 16x slot (slot #1 in the manual) free for future use; maybe a high end video card to do some View graphics test with or an additional SATA controller.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/05/img5.jpg"><img class="aligncenter size-full wp-image-2199" src="http://www.virtxpert.com/wp-content/uploads/2014/05/img5.jpg" alt="img5" width="446" height="791" /></a>

One last piece of hardware you’ll need, if only temporarily, is a USB CD/DVD drive to do the first ESXi installation. After that we can use ISO’s mounted from the datastores.  I’ve also opted to install ESXi to a USB drive, though you obviously have enough hard drives in this build to install to to a drive. I may remove some of these drives to test out some external drive enclosures later on so i did not want my ESXi install tied to any particular drive.

Once your hardware is installed, connect one of the LAN ports to your home network so we can manage the baremetal ESXi install and start creating new VMs. Download and burn the ISO image for ESXi 5.5 to a CD and you will be ready to power on the computer, configure the BIOS configured and install ESXi.

<strong>BIOS Configuration</strong>
<ol>
	<li>On boot, press F2 to enter setup.  Once in the BIOS I prefer advanced mode, so press F7 to enter advanced mode.</li>
	<li>Ensure the total memory is 32GB, otherwise you may have not seated your DIMMS securely or they could be defective.</li>
	<li>Check the System date and time and, if necessary adjust.</li>
	<li>Go to the Ai Tweakter tab and ensure AMD Turbo Core Technology is disabled</li>
	<li>Go to the Advanced tab and change the C state (C1E) from Enabled to Disabled, make sure SVM is enabled, Disable Core C6 state and disable Apm Master Mode.</li>
	<li>Go to the boot tab and ensure you can see all your devices. I am able to see my USB drive which I’ll install ESXi to, my 4x Seagate hybrid drives and 2 Neutron GTX drives.</li>
	<li>Finally, go to Secure Boot and change OS Type to Other OS. Now you are ready to install ESXi.</li>
</ol>
<strong>Wrap up and other notes</strong>

At this point you should be ready to install ESXi on the computer, while I won't cover that here I will write up a post on installing the nested ESXi hosts on this hardware build.  As for connectivity, I have vmnic0 connected to a switch as well as the Ethernet port on my home desktop and set the physical ESXi hosts IP address to 10.11.12.100/24 and a my desktop 10.11.12.254; you should now be able to connect to the host with the C# client.

If you are installing the vSphere 5.5 C# client on Windows 8.1 (maybe 8 as well), you will have to also go into Programs and Features, click on Turn Windows features on or off and add the .NET Framework 3.5 package as it is required for the client install.  Once that was installed and I rebooted (damn reboots) I was able to install the client and successfully connect to my physical host to start setting up the virtual ESXi hosts.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/05/host-client.png"><img class="aligncenter size-medium wp-image-2204" src="http://www.virtxpert.com/wp-content/uploads/2014/05/host-client-300x206.png" alt="host-client" width="300" height="206" /></a>

For now this lab will be isolated, but in the future I hope to connect it to the interwebs so I can test/play remotely.

In my next post, I'll cover the nested ESXi setup, including vSwitch configs and virtual ESXi host VMX settings.  As you can see here, 64-bit VMs are booting.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/05/inception-achieved.png"><img class="aligncenter  wp-image-2208" src="http://www.virtxpert.com/wp-content/uploads/2014/05/inception-achieved.png" alt="inception-achieved" width="665" height="592" /></a>

&nbsp;