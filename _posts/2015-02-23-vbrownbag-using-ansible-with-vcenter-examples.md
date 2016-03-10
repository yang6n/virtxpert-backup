---
ID: 3561
post_title: '#vBrownBag Using Ansible with vCenter Examples'
author: Jonathan Frappier
post_date: 2015-02-23 10:00:19
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vbrownbag-using-ansible-with-vcenter-examples/
published: true
dsq_thread_id:
  - "3540859104"
---
I wanted to share some of the example Ansible playbooks used during last Wednesday's US #vBrownBag. During the show I went over examples of how you can use Ansible to create, clone, and update virtual machines in vCenter without the need for other provisioning tools. Based on my testing (and I'm still learning as well), the items noted in the comments are the bare minimum needed to run the playbook, even though the official documentation may currently state otherwise. If you are already using Ansible for configuration management, this is a handy option to have as you can perform the provisioning tasks without leaving Ansible.

All playbooks have been uploaded to my <a href="https://github.com/jfrappier/ansible-test-playbooks/" target="_blank">GitHub Ansible-Test-Playbooks</a> repository (https://github.com/jfrappier/ansible-test-playbooks/).