---
ID: 75
post_title: VCP5 Study Prep
author: Jonathan Frappier
post_date: 2012-07-31 16:31:30
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vcp5-study-prep/
published: true
jabber_published:
  - "1343752295"
email_notification:
  - "1343752296"
reddit:
  - 'a:2:{s:5:"count";i:0;s:4:"time";i:1359696750;}'
dsq_thread_id:
  - "1094617778"
---
In an effort to help others persuing their VCP5, I thought it would be useful to share the steps I am taking to prepare.  A special thanks to all of the people who assembed the various resources I have used so far.

Step 1:  Make up your mind - do you really want your VCP?  I have gone back and forth on this since my first VMware implementation, and for a while it seemed like I could get by without it but more and more I want to focus on VMware so check...I want my VCP5.

2.  Sanity check - how much do I really know, or not know about VMware.  I looked at practice tests from <a href="https://twitter.com/SimonLong_">Simon Long</a> and VMware.  You can find Simon's at <a href="http://www.simonlong.co.uk/blog/vcp5-practice-exams/">http://www.simonlong.co.uk/blog/vcp5-practice-exams/</a> and the VMware practice exam in VMware's learning portal myLearn.

3.  Knowledge gap reality check - Look at these 2 exam crams, in combination with the practice test results, start to recognize areas you need to focus / practice on.  The first can be found here <a href="http://cosonok.blogspot.com/2011/10/vcp510-vcp-on-vsphere-5-exam-cram-notes.html">http://cosonok.blogspot.com/2011/10/vcp510-vcp-on-vsphere-5-exam-cram-notes.html</a> and <a href="https://twitter.com/mwpreston">Mike Preston'</a>s <a href="http://blog.mwpreston.net/wp-content/uploads/downloads/2012/03/OMG-Study-Guide.pdf">http://blog.mwpreston.net/wp-content/uploads/downloads/2012/03/OMG-Study-Guide.pdf</a>

4. Get your lab ready - I didn't want to just blindly read books, and didn't want to start making unnecessary changes to my production environment.  Though I am normally disappointed with www.geeks.com, I am giving them yet another chance.  I just ordered 2 Dell Precision's with dual Xeon dual-core processors and 4GB of RAM.  I will need to add a multi-port NIC and maybe another hard drive or two but this should be sufficient to run VM's for AD, vSphere and a few test servers.  My plan to mimic a SAN is to setup <a href="http://www.freenas.org/">FreeNAS</a> and share the local disks like they are actually a SAN/NAS (not sure whether I will do iSCSI or NFS yet).  The Virtual Storage Appliance from VMware is meant to do this (best I can tell since I haven't used it) but don't want it to integrate to well into vSphere so going FreeNAS (or OpenFiler or some other baremetal NAS/SAN OS).

<strong>Update:  </strong>As an alternative to building a physical lab, check out the autolab over at <a href="http://www.labguides.com/autolab/">http://www.labguides.com/autolab/</a>

5. Start reading - I picked up Mastering VMware vSphere 5 by <a href="https://twitter.com/scott_lowe">Scott Lowe</a>, I read Mastering VMware vSphere 4 a few years ago and it was fantastic so I fully expect this one to be the same.  I also picked up the vSphere 5 Study Guide by <a href="https://twitter.com/vmroyale">Brian Atkinson</a>.

6.  Official training - one of the things I love, and hate about VMware certifications is you have to take one of their courses, and they are not cheap.  On one hand (based on the practice tests) I could probably pass while brushing up on a few areas I don't have to live in everyday, on the other hand - hopefully this cert will not become meaningless in the future like the A+ or MCSE certifications have become.  Why is this only number 6 on my list?  Well if you flamed out in steps 1-5 you just saved yourself a good chunk of change.

Well, back to step 5.