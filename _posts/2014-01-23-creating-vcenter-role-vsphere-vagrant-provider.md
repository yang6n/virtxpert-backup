---
ID: 1893
post_title: >
  Creating a vCenter role for the
  vagrant-vsphere provider
author: Jonathan Frappier
post_date: 2014-01-23 10:21:09
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/creating-vcenter-role-vsphere-vagrant-provider/
published: true
dsq_thread_id:
  - "2163883777"
---
Vagrant is a tool typically associated with VirtualBox or VMware Workstation/Fusion, however a vSphere provider is available <a href="https://github.com/nsidc/vagrant-vsphere" target="_blank">here</a>.  Vagrant is an easy way to spin up and delete VMs, if you are a #vBrownBag watcher you may have heard the term "vagrant up" several times during the <a href="http://openstack.prov12n.com/openstack_phase_1/" target="_blank">Couch to OpenStack series</a> this past summer.  You can learn more about Vagrant <a href="http://openstack.prov12n.com/couch-to-openstack-vagrant-primer-follow-up/" target="_blank">here</a> and <a href="http://www.youtube.com/watch?v=Mqcn-TT3lbM" target="_blank">here </a>thanks to <a href="https://twitter.com/VMTrooper" target="_blank">Trevor Roberts Jr</a>.

In this post, I will review the steps to grant access to a user account created in AD to vSphere for purposes of using the vSphere-Vagrant provided to "vagrant up" and "vagrant destroy" VMs.  A few notes, the vsphere-vagrant provider does not appear to like spaces in the password, or special characters in the username such as spaces, underscores or dashes.  Also, since Vagrant is connecting to vCenter, it needs some permission at the vcenter level versus granularly adding permissions to specific objects such as datacenters, hosts, datastores etc...

If Vagrant connected always to a specific host you SHOULD be able to provide permission to just the host, datastore(s) and networks.

In theory what I want to try to do, but haven't, is provide read-only access role at the vCenter level, then specific permissions in other areas such as defining the permissions on a specific cluster or datacenter, or the specific servers, VM folders, datastores, networks/vswitches and resource pools if present, as well as any other objects I may not be thinking about right now.

For now, as this is on a dev/test environment can be applied at the vCenter level and should work to provision VMs.
<ul>
	<li>Create an account in your AD, and optionally place the user in a group (assuming you may want to provide other accounts with this level of access, maybe a devvspherevagrant user etc)</li>
	<li>Log into the web client &gt;&gt; Administration &gt;&gt; Role Manager</li>
	<li>Click the green plus icon to add a role, name it vsphere-vagrant.  See below for the list of actual privileges provided.</li>
	<li>Once the role is created, navigate from Home to vCenter &gt;&gt; vCenter Servers, click on your vCenter server</li>
	<li>Click on the Manage tab &gt;&gt; Permissions tab and click the green + icon</li>
	<li>Click the add button, change to your domain, find the user or group and click the add button, click ok</li>
	<li>Select the vsphere-vagrant role created earlier anjd click ok</li>
</ul>
Vagrant Role Settings are based on the need to create, and remove VMs.  There may be a few extraneous privileges in here, this was a first pass at getting it working.

<strong>Role settings</strong>
- Datastore
<ul>
	<li>- Allocate space</li>
	<li>- Browse datastore</li>
	<li>- Remove file</li>
	<li>- Update virtual machine file</li>
</ul>
- Global
<ul>
	<li>- Log event</li>
	<li>- Cancel task</li>
</ul>
- Host
<ul>
	<li>- Create virtual machine</li>
	<li>- Delete virtual machine</li>
	<li>- Reconfigure virtual machine</li>
</ul>
- Network
<ul>
	<li>- Assign network</li>
</ul>
- Resource
<ul>
	<li>- Assign virtual machine to resource pool</li>
</ul>
- Tasks
<ul>
	<li>- Create task</li>
	<li>- Update task</li>
</ul>
- Virtual machine
- Configuration
<ul>
	<li>- Add new disk</li>
	<li>- Add or remove device</li>
	<li>- Advanced</li>
	<li>- Change CPU count</li>
	<li>- Change resource</li>
	<li>- Configure ManagedBy</li>
	<li>- Memory</li>
	<li>- Modify device settings</li>
	<li>- Remove disk</li>
	<li>- Rename</li>
	<li>- Settings</li>
	<li>- Swap file placement</li>
</ul>
- Guest operations
<ul>
	<li>- Guest Operations Modifications</li>
</ul>
- Interaction
<ul>
	<li>- Power on</li>
	<li>- Power off</li>
	<li>- Reset</li>
	<li>- Suspend</li>
	<li>- VMware Tools install</li>
</ul>
- Inventory
<ul>
	<li>- Create from existing</li>
	<li>- Create new</li>
	<li>- Move</li>
	<li>- Register</li>
	<li>- Remove</li>
	<li>- Unregister</li>
</ul>
- Provisioning
<ul>
	<li>- Allow disk access</li>
	<li>- Clone template</li>
	<li>- Clone virtual machine</li>
	<li>- Customize</li>
	<li>- Deploy template</li>
	<li>- Mark as virtual machine</li>
	<li>- Read customization speceifications</li>
</ul>