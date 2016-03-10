---
ID: 4252
post_title: Ansible all the VMware things
author: Jonathan Frappier
post_date: 2015-12-28 08:00:57
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/ansible-all-the-vmware-things/
published: true
dsq_thread_id:
  - "4440489115"
---
Last year, about this time I gave a demo on the #vBrownBag DevOps series about using Ansible with vSphere. At the time, there was functionality that allowed you to define new virtual machines, or clones of templates in an Ansible playbook; a very handy feature especially since you should have some form of configuration management anyways.

Fast forward a year - Ansible 2.0 (currently in RC/pre-GA) has added several new VMware specific modules to help you manage your VMware environment, you can see a <a href="http://docs.ansible.com/ansible/list_of_all_modules.html" target="_blank">full list of all modules on the Ansible Docs site</a> (one of my favorite documentation sites). In this post, I will give a brief overview of some of the modules before I dive in deeper to each one. *Note that since this is currently pre-GA, you will need to install from source to get the bits, other wise you will have access to all of these.

If I think about the typical deployment process, the first step after deploying vCenter would be to create a data center - Ansible has you covered with the <a href="http://docs.ansible.com/ansible/vmware_datacenter_module.html" target="_blank">vmware_datacenter</a> module. Next I would create a cluster and enable the required options such as HA and/or DRS - yup <a href="http://docs.ansible.com/ansible/vmware_cluster_module.html" target="_blank">Ansible has you covered there as well with vmware_cluster</a> - though currently this module is missing the ability to enable EVC, something I hope will be added.

Next I would add hosts to my cluster (<a href="http://docs.ansible.com/ansible/vmware_host_module.html" target="_blank">vmware_host</a>), configure 1 or more vmkernel adapters (<a href="http://docs.ansible.com/ansible/vmware_vmkernel_module.html" target="_blank">vmware_vmkernel</a>), provide the vmkernel adapter with an IP addres (<a href="http://docs.ansible.com/ansible/vmware_vmkernel_ip_config_module.html" target="_blank">vmware_vmkernel_ip_config</a>) and create a VDS (<a href="http://docs.ansible.com/ansible/vmware_dvswitch_module.html" target="_blank">vmware_dvswitch</a>), a standard switch for management (<a href="http://docs.ansible.com/ansible/vmware_vswitch_module.html" target="_blank">vmware_vswitch</a>) and necessary port groups (<a href="http://docs.ansible.com/ansible/vmware_portgroup_module.html" target="_blank">vmware_portgroup</a> for VSS and <a href="http://docs.ansible.com/ansible/vmware_dvs_portgroup_module.html" target="_blank">vmware_dvs_portgroup</a> for DVS).

There are also options manage host DNS using <a href="http://docs.ansible.com/ansible/vmware_dns_config_module.html" target="_blank">vmware_dns_config</a> - it's always a DNS problem right? So why not have configuration management for your hosts DNS settings? And I can event get to a the shell of a VM to execute processes using <a href="http://docs.ansible.com/ansible/vmware_vm_shell_module.html" target="_blank">vmware_vm_shell</a> - maybe an agent to be installed or even a script that can write back to my Ansible control machines hosts file so I can easily manage those new VMs from Ansible!

Summary

Ansible 2.0 has added a ton of great new modules, not only for VMware admins but several cloud providers. Having the ability to manage the configuration of my vCenter servers makes them much more "lightbulb" like - if its bad, nuke it and redeploy, makes for a easy documentation or DR setup.