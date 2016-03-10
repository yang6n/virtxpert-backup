---
ID: 2388
post_title: >
  Failed to start the virtual machine
  (error-18)
author: Jonathan Frappier
post_date: 2014-07-15 08:30:44
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/failed-start-virtual-machine-error-18/
published: true
dsq_thread_id:
  - "2845380394"
---
<a href="http://www.virtxpert.com/wp-content/uploads/2014/07/vmicon.png"><img class="alignleft size-medium wp-image-2301" src="http://www.virtxpert.com/wp-content/uploads/2014/07/vmicon-300x300.png" alt="vmicon" width="300" height="300" /></a>Recently an administrative error caused several host to lose access to datastores hosting virtual machines.  While in this particular scenario it was human error, switch, HBA, cabling or storage failures could also cause a host to lose access to storage.

Once the problem was corrected, and host once again had access to the storage and datastores VM's were brought back online, however one VM would not start giving the error:
<pre>Failed to start the virtual machine (error-18)</pre>
The following errors also appeared in the logs
<pre>Vpxa: [3E879B70 info 'DiskLib' opID=29f52016-bc] DISKLIB-LINK  : "/vmfs/volumes/531a13ef-0196038d-bcb7-44d3cabcb764/ehc-pod2-sql01/ehc-pod2-sql01-flat.vmdk" : failed to open (Failed to lock the file).</pre>
There are a couple KB's that describe a potential problem, such as a <a href="kb.vmware.com/kb/1002511" target="_blank">missing descriptor file</a> (http://kb.vmware.com/kb/1002511) which lead me to browse the datastore via SSH and see there was a .lck file.  <a href="http://kb.vmware.com/kb/1008728" target="_blank">KB 1008728</a> got me a bit closer in helping me find which server thought it had a lock on the files by running, although it didn't provide a direct solution:
<pre>vmkfstools -D pathtofile</pre>
<!--more-->

For example vmkfstools -D /vmfs/volumes/531a13ef-01960
38d-bcb7-44d3cabcb764/ehc-pod2-sql01/ehc-pod2-sql01-flat.vmdk and seeing the following output:
<pre>/vmfs/volumes/531a13ef-0196038d-bcb7-44d3cabcb764/ehc-pod2-sql01 # vmkfstools -D /vmfs/volumes/531a13ef-01960
38d-bcb7-44d3cabcb764/ehc-pod2-sql01/ehc-pod2-sql01-flat.vmdk
Lock [type 10c00001 offset 164800512 v 122, hb offset 3756032
gen 23, mode 1, <span style="color: #ff0000;">owner </span><span style="color: #000000;">53a21390-e78f7f00-f805-</span><span style="color: #ff0000;">44d3cabcb7b4</span> mtime 378512
num 0 gblnum 0 gblgen 0 gblbrk 0]
Addr &lt;4, 360, 53&gt;, gen 109, links 1, type reg, flags 0, uid 0, gid 0, mode 600
len 42949672960, nb 28851 tbz 0, cow 0, newSinceEpoch 28851, zla 3, bs 1048576</pre>
The "owner" of the file had a MAC address of 44-d3-ca-bc-by-b4.  With this information I was able to SSH to that host, navigate back to the datastore folder for that VM and remove the .lck file by running:
<pre># rm ehc-pod2-sql01.vmx.lck</pre>
However, attempts to restart the VM still failed, I additional had to remove the vmname.vmx~ and any .vswp files by using the rm command as I did to remove the .lck file.  For example:
<pre># rm ehc-pod2-sql01.vmx~</pre>
or
<pre># rm ehc-pod2-sql01-a71fc080.vswp</pre>
With these files removed, I was now able to power on the VM.