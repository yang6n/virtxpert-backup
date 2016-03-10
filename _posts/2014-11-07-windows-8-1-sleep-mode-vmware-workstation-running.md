---
ID: 2864
post_title: >
  Windows 8.1 sleep mode with VMware
  Workstation running
author: Jonathan Frappier
post_date: 2014-11-07 06:54:47
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/windows-8-1-sleep-mode-vmware-workstation-running/
published: true
dsq_thread_id:
  - "3201260869"
---
One of the things I've been curious about as I build my home lab in VMware workstation is the stability of my lab if my Windows 8.1 host goes into sleep mode without any intervention with the lab virtual machines, says after hours troubleshooting and you're just two tired to shut down.  In the past, when I have suspended my virtual machines things didn't always come back up cleanly; for example the VCSA inventory service normally could not start without a VCSA reboot.

Well, so far, I am happy to report that putting the host OS to sleep - again in my case Windows 8.1, all 4 virtual machines setup so far in my lab have come back fully operational.  I have been able to log right into the vSphere Web Client without any trouble.  It would appear, if you are running virtual machines on your workstation (laptop or desktop) your best bet is to just put it to sleep and not interact with the virtual machines, I will try to test this on my laptop down the road but for now those following along, building a VMware Workstation home lab should be able to put their computer to sleep when not in use, of course your mileage may vary.