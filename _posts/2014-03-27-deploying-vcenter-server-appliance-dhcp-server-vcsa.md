---
ID: 2098
post_title: 'Deploying the vCenter Server Appliance with no DHCP server #VCSA'
author: Jonathan Frappier
post_date: 2014-03-27 13:10:46
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/deploying-vcenter-server-appliance-dhcp-server-vcsa/
published: true
dsq_thread_id:
  - "2525605325"
---
Deploying the vCenter Server Appliance is easy when you've got DHCP, import, boot, go to https://ip:5480, but what happens if you have a deployment with no DHCP server on the network?  Since the VCSA is a linux appliance, linux admins/engineers will be familiar with how to set an IP address.

Before getting started you'll need a valid static IP address on the network/VLAN/port group you've connected the VM, and its subnet mask.  If you are not already, you'll need to have the C# client connected to the host you've deployed the VCSA to.  Next, switch to the console tab and log in with the default username of root and password of vmware.  Once logged in you will be at a Linux CLI, following these steps to provide an IP address.

Type the following command to edit the interface configuration file:
<pre>vi /etc/sysconfig/networking/devices/ifcfg-eth0</pre>
From here you will be brought into the scary world of vi, fear not, its really not that bad.  Within vi you use the arrow keys to move the cursor, tip - don't use the number pad.  Move the cursor to the line that says BOOTPROTO and press use the e key or arrow keys to move to the end of the line.  Now press the i key on your keyboard to be able to edit the document.  Use the Backspace key to remove dhcp and replace it with static.

Use the arrow keys again to move the bottom of the document and add these lines:
<pre>TYPE=Ethernet
USERCONTROL=no
IPADDR=actual IP
NETMASK=actual subnet
BROADCAST=actual IP broadcast address</pre>
Yours should look something like this:

<a href="http://www.virtxpert.com/wp-content/uploads/2014/03/ifcfg-eth0.jpg"><img class="aligncenter size-full wp-image-2099" src="http://www.virtxpert.com/wp-content/uploads/2014/03/ifcfg-eth0.jpg" alt="ifcfg-eth0" width="281" height="194" /></a>

Now, hit the Esc key on your keyboard, enter a : (shift+;), type wq and hit the Enter key.  You should get a message back that ifcfg-eth0 has been written.  Finally type service network restart.  If you type ifconfig you should see that eth0 has the IP address you set and ping other addresses on your network (having problems?  Check the IP, mask and VM port group).

<strong>Summary</strong>

If you work with linux, this isn't anything new but for folks not familiar with linux it may be a little unnerving but as you can see its quite simple.  With the IP address set, now you can navigate to (based on this example) https://192.168.100.100:5480