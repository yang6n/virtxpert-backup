---
ID: 2415
post_title: 'Help &#8211; I installed CentOS with a VMXNET3 NIC and can&#8217;t install Perl or VMware Tools!'
author: Jonathan Frappier
post_date: 2014-08-01 08:00:39
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/help-installed-centos-vmxnet3-nic-cant-install-perl-vmware-tools/
published: true
dsq_thread_id:
  - "2891459396"
---
<a href="http://www.virtxpert.com/wp-content/uploads/2014/07/tux-egg.jpeg"><img class="alignleft wp-image-2420 size-full" src="http://www.virtxpert.com/wp-content/uploads/2014/07/tux-egg.jpeg" alt="tux-egg" width="204" height="204" /></a>I often (always?) prefer installing linux from the minimal CD's, nothing I need from the CD that I cannot get from yum or apt-get.  However what happens if you want to use the VMXNET3 driver with the minimal install?  In order to get the VMXNET3 drivers installed, you need VMware Tools.  In order to install VMware Tools you need Perl.  In order to get Perl you need internet access!  What's an admin to do? (Update, as Timothy Patterson pointed out this may be fixed in CentOS 7 - this was written on CentOS 6.2 and believe Perl is not included through at least 6.5)

Quite simple actually, add a 2nd NIC using the E1000 driver.  The E1000 driver will be recognized nativley by the OS without VMware tools.  Now you can configure this adapter (either DHCP or Staic by editing /etc/sysconfig/network-scripts/ifcfg-eth0 (since your VMXNET3 NIC won't be recongnized).  After a fresh install, you will need to at the very least activate the card.  Run:

<!--more-->

vi /etc/sysconfig/network-scripts/ifcfg-eth0

Set

ONBOOT="yes"

Type :wq and press the enter key (this saves the file).  Now type

service network restart

Now if you run ifconfig you will see eth0 in addition to lo.  If you have DHCP you should also have an IP address with all the information you need.  If you need to provide a static address, you'll need a bit more info in the ifcfg-eth0 file.  Here is what mine looks like

<a href="http://www.virtxpert.com/wp-content/uploads/2014/07/ifconfig.png"><img class="aligncenter size-full wp-image-2416" src="http://www.virtxpert.com/wp-content/uploads/2014/07/ifconfig.png" alt="ifconfig" width="537" height="229" /></a>

Now you should be able to ping network resources.  Now run

yum install perl

You will be prompted to confirm the installation of several packages, twice (press y).  After a few minutes you should receive a Complete! message.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/07/perl-complete.png"><img class="aligncenter size-full wp-image-2417" src="http://www.virtxpert.com/wp-content/uploads/2014/07/perl-complete.png" alt="perl-complete" width="770" height="436" /></a>

You can now start the VMware tools install by running

./vmware-install.pl

from the directory you extracted VMware tools - <a href="http://kb.vmware.com/kb/1018414" target="_blank">http://kb.vmware.com/kb/1018414</a>

<a href="http://www.virtxpert.com/wp-content/uploads/2014/07/vmwaretools.png"><img class="aligncenter size-full wp-image-2418" src="http://www.virtxpert.com/wp-content/uploads/2014/07/vmwaretools.png" alt="vmwaretools" width="705" height="144" /></a>

Reboot and you should see the VMXNET3 driver NIC listed in /etc/udev/rules.d/70-persistent-net.rules

<a href="http://www.virtxpert.com/wp-content/uploads/2014/07/persistent70.png"><img class="aligncenter size-full wp-image-2419" src="http://www.virtxpert.com/wp-content/uploads/2014/07/persistent70.png" alt="persistent70" width="774" height="410" /></a>

You can now make note of the MAC, in my case 00:50:56:bd:25:93, comment out the first SUBSYSTEM line, change the NAME="eth1" to "eth0"

Edit/etc/sysconfig/network-scripts/ifcfg-eth0 and change the HWADDR , disconnect the E1000 NIC in the vSphere client (web or otherwise) and reboot the VM.  CentOS seems to get a bit cranky about shutting down the interface when the MACs get changed (in theory you could stop networking all together before editing I guess - not tested).

When the VM reboots, you will have only your VMXNET3 adapater connected and have internet access.  Clone away!