---
ID: 330
post_title: >
  Mounting iSCSI volumes in Windows Server
  2012
author: Jonathan Frappier
post_date: 2012-12-31 11:44:36
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/mounting-iscsi-volumes-in-windows-server-2012/
published: true
jabber_published:
  - "1356972278"
email_notification:
  - "1356972280"
publicize_twitter_user:
  - jfrappier
reddit:
  - 'a:2:{s:5:"count";i:0;s:4:"time";i:1357593894;}'
publicize_reach:
  - 'a:2:{s:7:"twitter";a:1:{i:1983177;i:507;}s:2:"wp";a:1:{i:0;i:14;}}'
dsq_thread_id:
  - "1182363729"
---
Maybe I am mis-remembering, or maybe not, but I was mounting iSCSI volumes created on a storage appliance today and was baffled a bit.  This should be easy right?  Configured storage, password/authentication go to the iSCSI initiator in Windows and add the IP address of the storage device.

So far, all was working as I thought it should, the two iSCSI volumes showed up, entered the CHAP password that was configured and connected....but no drives showed up - hmmmm.  As it turns out in Server 2012 I have to bring the drives online.  Maybe I am so used to doing this in ESXi that I just forgot but pretty sure I did not have to do this in 2008 or 2003.  Once you see your drives connected in the Microsoft iSCSI initiator go to Server Manager &gt;&gt; File and Storage &gt;&gt; Disks.  You should see your volumes here with a status of "offline."

<a href="http://jonathanfrappier.wordpress.com/2012/12/31/mounting-iscsi-volumes-in-windows-server-2012/servermanager/#main" rel="attachment wp-att-331"><img class="aligncenter size-full wp-image-331" alt="servermanager" src="http://jonathanfrappier.files.wordpress.com/2012/12/servermanager.jpg" width="572" height="422" /></a>

Simply right click, select Bring Online and accept the warning about other servers (of course if other servers are connected it may be worth while to heed that warning!).

<a href="http://jonathanfrappier.wordpress.com/2012/12/31/mounting-iscsi-volumes-in-windows-server-2012/online/#main" rel="attachment wp-att-332"><img class="aligncenter size-full wp-image-332" alt="online" src="http://jonathanfrappier.files.wordpress.com/2012/12/online.jpg" width="323" height="192" /></a>