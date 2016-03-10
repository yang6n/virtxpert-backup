---
ID: 2645
post_title: 'Linux Bash bug exists in at least some VMware appliances #bash #shellshock'
author: Jonathan Frappier
post_date: 2014-09-25 08:47:38
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/linux-bash-bug-exists-least-vmware-appliances-bash/
published: true
dsq_thread_id:
  - "3052649955"
---
<em><strong>**Update 9/29:  VMware has released KB 2090740 (<a href="http://kb.vmware.com/kb/2090740" target="_blank">http://kb.vmware.com/kb/2090740</a>) with more information about ShellShock and affected appliances however as of this update I do not yet see updated virtual appliances available for download.**</strong></em>

<em><strong>**Update 10/1:  VMware has started to release patches for selected appliances.  As of 1:30P EST LogInsight and the vCenter Server Appliance has been updated.  You can find patches at <a href="https://www.vmware.com/patchmgr/findPatch.portal" target="_blank">https://www.vmware.com/patchmgr/findPatch.portal</a>**</strong></em>

<em><strong>**Update 2 10/1:  The VCSA patch is not yet available via VAMI (Thanks Christian for checking, and Mike for looking into it) but you can download a new appliance, so new deployments will be patched**</strong></em>

As I actually expected, the <a href="http://www.theregister.co.uk/2014/09/24/bash_shell_vuln/" target="_blank">bash bug</a> seems to affect VMware virtual appliances such as the vCO appliance and vCAC appliance.  I'd imagine things like the vCenter server appliance and others are also vulnerable but I don't have others in my lab right now to test.  Hopefully VMware is quick to release patches that can be applied via VAMI.

[caption id="attachment_2646" align="aligncenter" width="747"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/09/vco-bash.jpg"><img class="size-full wp-image-2646" src="http://www.virtxpert.com/wp-content/uploads/2014/09/vco-bash.jpg" alt="vco-bash-bug" width="747" height="88" /></a> vCenter Orchestrator Appliance[/caption]

[caption id="attachment_2648" align="aligncenter" width="726"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/09/vcac-bash1.png"><img class="size-full wp-image-2648" src="http://www.virtxpert.com/wp-content/uploads/2014/09/vcac-bash1.png" alt="vcac-appliance-bash-bug" width="726" height="120" /></a> vCAC Appliance[/caption]