---
ID: 3324
post_title: >
  VMware Application Services Linux
  deployment hangs at agent_bootstrap node
  setup
author: Jonathan Frappier
post_date: 2014-12-01 09:30:27
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vmware-application-services-linux-deployment-hangs-agent_bootstrap-node-setup/
published: true
dsq_thread_id:
  - "3279764271"
---
When deploying an Application Services blueprint, you notice that the workflow does not move past the 2nd step in the provisioning process - agent_bootstrap node setup, however the previous step which renames the virtual machines appears to work fine.  In this scenario you have also successfully installed the AppD agent in the vSphere template.

[caption id="attachment_3325" align="aligncenter" width="821"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/application-services-hangs-agent_bootstrap.png"><img class="wp-image-3325 size-full" src="http://www.virtxpert.com/wp-content/uploads/2014/11/application-services-hangs-agent_bootstrap.png" alt="VMware Application Services / Application Director hangs at agent_bootstrap node setup" width="821" height="393" /></a> VMware Application Services / Application Director hangs at agent_bootstrap node setup[/caption]

If you log into the virtual machine, you can see that the vmware_appdirector_agent should be set to on, however when checking the running services (for example by running ps -ef | grep vmware_appdirector_agent) you do not see any processes running.

When working with vSphere templates that are used in Application Services / Application Director blueprints there are a few things to be aware of.  After the agent installation initially, you shutdown the virtual machine, however making changes to the template after the initial shutdown requires additional steps to be performed.   Not only do you need to remove the /etc/udev/rules/70-persistent-net.rules file and make sure the vmnic MAC is not in /etc/sysconfig/network-scripts/ifcfg-eth0 but you also need to run
<pre>/opt/vmware-appdirector/agent-boostrap/agent_reset.sh</pre>
This reset the agent configuration and allows it to start properly after being cloned.  Once the agent_reset script has been run, shutdown the host and convert it back to a template.  You should now be able to run your Application Services / Application Director blueprint (or at least get past that step :) )

[caption id="attachment_3328" align="aligncenter" width="824"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/application-services-completes-agent_bootstrap.png"><img class="size-full wp-image-3328" src="http://www.virtxpert.com/wp-content/uploads/2014/11/application-services-completes-agent_bootstrap.png" alt="VMware Application Services / Application Director agent_bootstrap completes node setup" width="824" height="394" /></a> VMware Application Services / Application Director agent_bootstrap completes node setup[/caption]