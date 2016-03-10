---
ID: 2250
post_title: Untangle vs Vyatta for home lab use
author: Jonathan Frappier
post_date: 2014-05-29 16:06:29
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/untangle-vs-vyatta-home-lab-use/
published: true
dsq_thread_id:
  - "2722146769"
---
I wanted to specifically call out this comparison was done for my home lab, specifically to provide basic internet access for my isolated physical ESXi host which would run several nested ESXi VMs and other support VMs such as AD and vCenter.  Whether Untangle or Vyatta is right for you will come down to your specific project, and the requirements for that project.  My requirement was to have an easy to configure virtual router running in VMware Workstation to provide access to an isolated  network that would not otherwise be able to communicate with my home router.

Most of the work in either case for me was in VMware Workstation, setting up proper bridging on my "home" computer which uses the WLAN adapter for every day internet access - this would end up being the "external" interface for my virtual router and the LAN connection which is connected to a switch along with the VMkernel interface for my physical ESXi host (<a title="8-Core, 32GB RAM, 240GB Flash Home Lab Hardware Assembly" href="http://www.virtxpert.com/8-core-32gb-ram-240gb-flash-home-lab-hardware-assembly/" target="_blank">8-core 32GB home lab build notes here</a>).

Once the networking was setup, next stop was <a href="http://www.vyatta.org/downloads" target="_blank">Vyatta Community Edition</a>, I'm not sure what Brocade is doing with the site, but I had quite a hard time accessing it and was ready to give up until one night it worked and I was able to download the bits.  I created a VM with two network interfaces, one on each network segment and powered up the VM.  I had expected an installation process to start, but alas it did not, it had to be manually started.  After a bit of messing around and reading these two posts (<a href="http://wojcieh.net/vyatta-router-running-on-vmware-workstation-part-1/" target="_blank">install</a> and <a href="http://wojcieh.net/vyatta-router-running-on-vmware-workstation-part-2-dns-firewall-and-nat/" target="_blank">DNS/NAT</a>) I thought I'd be just about set.  From my Vyatta router I could ping 8.8.8.8 (internet working) but my physical host could not.  After reading through the <a href="http://www.brocade.com/downloads/documents/html_product_manuals/vyatta/vyatta_5400_manual/wwhelp/wwhimpl/js/html/wwhelp.htm" target="_blank">Vyatta documentation here</a> and making a few more changes I thought a reboot would be in order.   When my VM came back up I could no longer ping 8.8.8.8, I started looking around and none of my configuration was preserved!  I set it back up only to run into the same road block - it wasn't working and I'm not interested in becoming a Vyatta Certified network admin/engineer.  Time to punt and try something else.

My next try was using Untangle.  I was using the same VMware Workstation VM and network configuration.  I powered on the VM, was prompted to run through an installer (as I'd expect when booting from an ISO/installer image) and configured the networking the same way I had (tried) with Vyatta.  The results, however, were much different.  With essentially no effort (other than the network setup in Workstation) I not only had internet access from the Untangle / router VM but also from my ESXi hosts which were using it as the Default Gateway.

While this isn't a true bake off, feature for feature or comparing the power of each, I can say that Untangle was far simpler for a basic setup.  Vyatta may well be the more powerful option, but as I stated earlier right now I really have no desire to learn yet another CLI, I'm quite happy keeping my Cisco CLI vaulted and don't want to burn those brain cells for something I'm unlikely to use in production.  If I end up on a project with different requirements, maybe I'll find Vyatta gain but for now its Untangle!