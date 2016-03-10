---
ID: 1751
post_title: >
  Is VMware getting sloppy with their
  products?
author: Jonathan Frappier
post_date: 2014-01-02 13:56:01
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vmware-getting-sloppy-products/
published: true
dsq_thread_id:
  - "2087860059"
---
I love VMware, there I said it.  Now that that's out of the way I am a bit concerned of late over some the hoops I have had to jump through to use their products.  Maybe I am just digging deeper into the rabbit whole than I have had to do before but there are some things that just seem downright lazy.

For example, there is this little gem when trying to deploy vCOPS - you need DRS enabled if you are deploying into a cluster, but you can use Foundations with any version so you may not have Enterprise Plus.  The work around?  Remove a host from the cluster (<a href="http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&amp;cmd=displayKC&amp;externalId=2013695">http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&amp;cmd=displayKC&amp;externalId=2013695</a>) - with all due respect VMware that is lazy.

Also, there is a problem deploying OVFs through the web client, something that has been present since 5.1 and still affects 5.5.  If you knew it existed in 5.1, how was it not corrected in 5.5?  (<a href="http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&amp;cmd=displayKC&amp;externalId=2045635">http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&amp;cmd=displayKC&amp;externalId=2045635</a>)

Then, there is the inability to edit VM's with hardware version 10 through the C# client, which would be fine if it weren't for the previous problem and seemingly every web client KB's suggested work around of using the C# client.

Lastly, NSX.  Every other piece of software VMware provides can be downloaded and deployed with a few mouse clicks, for NSX you need to engaged in a POC (that feels an awful lot like EMC).  I understand NSX is essentially a v1 product, but you allow us to download VSAN which is still in beta?  Why the change on NSX?

I'll say it again, I love VMware and their products, and their KB is one of the best I've ever used from a vendor but hacky work arounds like removing hosts from the cluster or falling back to a software program you claim is going away is not the right solution.  Please don't let this be your new reality.