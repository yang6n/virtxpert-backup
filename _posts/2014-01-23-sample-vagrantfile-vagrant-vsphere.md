---
ID: 1897
post_title: Sample Vagrantfile for vagrant-vsphere
author: Jonathan Frappier
post_date: 2014-01-23 20:04:48
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/sample-vagrantfile-vagrant-vsphere/
published: true
dsq_thread_id:
  - "2166134558"
---
While there is a sample Vagrantfile for vagrant-vsphere at <a href="https://github.com/nsidc/vagrant-vsphere" target="_blank">https://github.com/nsidc/vagrant-vsphere</a>, I thought I'd share an example of one working for us (this is no thanks to me, but a co-worker who smashed through concrete walls of bad documentation to get it working).

Note that vsphere.clone_from_vm = yes is required if you do not have Enterprise Plus because cloning from a template currently requires a resource pool, the DRS if the host is in a cluster.  If you use templates, clone or convert it to a regular VM first.  Also note single quotes are required where noted, if there are no single quotes in a specific line then you do not need them.
<pre>Vagrant.configure("2") do |config|
  config.vm.box = 'dummy'
  config.vm.box_url = './example_box/dummy.box'

  config.vm.provider :vsphere do |vsphere|
    vsphere.host = 'vcenter.domain.tld'
    vsphere.name = 'name-of-your-vm'
    vsphere.clone_from_vm = true
    vsphere.template_name = 'Foldername/name-of-vm-youre-cloning'
    vsphere.user = 'domain\\user'
    vsphere.password = 'YOUR VMWARE PASSWORD'
    vsphere.insecure = true
  end
end</pre>