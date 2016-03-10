---
ID: 2825
post_title: Getting to know EMC VPLEX
author: Jonathan Frappier
post_date: 2014-11-04 08:57:05
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/getting-know-emc-vplex/
published: true
dsq_thread_id:
  - "3190713059"
---
<em>*Disclaimer - I work for EMC.  I was not asked to write this post nor was it reviewed/approved by my employer prior to publishing.  It is simply based on my learning experience as I get to know this solution*</em>

I've had the opportunity for the last few days to spend some time getting to know <a href="http://www.emc.com/storage/vplex/vplex.htm" target="_blank">EMC VPLEX</a>, and wow - I wish I knew about this a few years ago.  VPLEX enables continuous available of storage arrays either locally (Local) or over distance (Metro and Geo).  In addition of continuous availability in the event of array maintenance or failure it also provides the means to migrate data from different arrays.  Now before you keep reading know that I am still learning about this solution as well - if you know this solution well and I've got something wrong here please let me know.

VPLEX works by sitting between the hosts and storage arrays.  Rather than zoning a host to a physical array, you zone the host to the VPLEX.  Then the VPLEX is zoned to the storage array to present available storage to the host.  Since my host is access storage through the VPLEX, and not on the array directly I can take out entire physical arrays behind the VPLEX and depending on my configuration have no affect on the host or the availability of storage.

Of particular interest to me is the Metro configuration, I could stretch a distributed volume and VMware cluster across data centers (assuming &lt; 5ms round trip between data centers) and in the event of a site outage have access to my original virtual infrastructure.  Now a site outage could be many things - an array failure, network failure or natural disaster scenario that takes out accessibility to that physical location.  I had the opportunity in a course I was teaching last week to have some folks who helped me whiteboard what this looks like:
<h3>Whiteboarding a VPLEX Metro</h3>
[caption id="attachment_2826" align="aligncenter" width="800"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/vplex.jpg"><img class="wp-image-2826 size-full" src="http://www.virtxpert.com/wp-content/uploads/2014/11/vplex.jpg" alt="VPLEX Metro whiteboard session" width="800" height="540" /></a> VPLEX Metro whiteboard session[/caption]

What we have here are two arrays behind a VPLEX Metro setup - one array each in site A and B and one VPLEX in site A and B.  A distributed volume is created on the VPLEX and hosts are zoned to the VPLEX like you would typically directly to the array.  Since it is zoned to the VPLEX, and the VPLEX is setup in a Metro configuration each host can access the VPLEX in each site.  If a site fails, multipathing rules for the host would move to the VPLEX in site B and continue operation.  The witness in the middle is in a 3rd failure domain and used to monitor the VPLEXs to ensure the failure is not just communication between the VPLEXs and manage VPLEX rules appropriately.

Now as I said in the beginning I am still getting to know VPLEX, if you want to learn more check out the <a href="https://community.emc.com/docs/DOC-34286" target="_blank">free EMC Education Services VPLEX eLearning on ECN</a>.  There is also a <a href="https://community.emc.com/docs/DOC-17867" target="_blank">VPLEX practice test available</a> if you want to test your VPLEX knowledge after the eLearning and figure out what, if any other training  you want to purse.