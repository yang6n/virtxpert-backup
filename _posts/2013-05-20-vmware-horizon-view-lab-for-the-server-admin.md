---
ID: 922
post_title: >
  VMware Horizon View Lab for the server
  admin
author: Jonathan Frappier
post_date: 2013-05-20 11:43:23
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vmware-horizon-view-lab-for-the-server-admin/
published: true
switch_like_status:
  - "1"
dsq_thread_id:
  - "1301221355"
---
Recently I had the opportunity to setup a VMware Horizon View lab as a proof-of-concept (POC) for a customer who was looking for the ability to run their desktop apps on mobile devices.  After having setup <a href="http://www.virtxpert.com/building-a-vmware-horizon-lab-part-1/" target="_blank">VMware Horizon Workspace</a>, I was a bit concerned on the setup of the infrastructure to support View, however the View infrastructure setup is very similar to setting up your vSphere environment (assuming you built vCenter on Windows).
<p style="text-align: left;">The <a href="http://www.vmware.com/files/pdf/view/VMware-View-Evaluators-Guide.pdf" target="_blank">Evaluator's Guide</a> is an excellent resource, I felt like just about everything you need is mentioned in this guide.  Now obviously it does not go into setting up a lab or production environment so you will want to make sure you have your Active Directory setup properly, setting your domain controllers to sync with and <a href="http://support.microsoft.com/kb/816042" target="_blank">be an authoritative time source</a>, configure your hosts for appropriate logging etc.</p>
One item not mentioned in the reviewers guide, <a href="http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&amp;cmd=displayKC&amp;externalId=2035268" target="_blank">VMware Knowledge  Base Article 2035268</a>, there is a patch you will need to download if you already have a lab built, or a specific ISO image to support all of the view features.  Also view has a limited set of supported GPU's if you want to test some of the 3D or advanced graphics features, the cheapest I could find a Quadro 4000 was on Amazon for about $650.  Now you don't need one of these cards, View will still run you just may not have optimal video performance.

Finally, as you would on a virtualized server, it is important to tweak your image to ensure you are running the minimal number of necessary services and configure performance settings appropriately for your needs.  Quest (Dell) has a free <a href="http://communities.quest.com/community/vworkspace/blog/2011/09/08/introducing-the-free-quest-vworkspace-desktop-optimizer" target="_blank">Desktop Optimizer tool</a> that you can download to assist with these tweaks to get the most out of your environment.