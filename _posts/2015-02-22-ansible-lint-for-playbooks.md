---
ID: 3563
post_title: Ansible-lint for playbooks
author: Jonathan Frappier
post_date: 2015-02-22 19:48:38
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/ansible-lint-for-playbooks/
published: true
dsq_thread_id:
  - "3539282764"
---
During the #vBrownBag DevOps series after-show from my Using Ansible to provision VM's in vCenter, Mike Marseglia asked about options for <a href="http://stackoverflow.com/questions/8503559/what-is-linting" target="_blank">linting</a> Ansible playbooks. Since I didn't know, I thought it would be worthwhile to look into it. There is an <a href="https://github.com/willthames/ansible-lint" target="_blank">Ansible-Lint repo on GitHub</a>, reading through the information, it seemed straight forward. Here I am going to have a look at installing and using it against some example playbooks.

Installation should be easy, assuming you've got the correct packages installed, see my previous <a title="Installing Ansible via Git" href="http://www.virtxpert.com/installing-ansible-via-git/" target="_blank">Ansible posts</a> - if you got through that install, you should be able to install this with a single line:
<pre>pip install ansible-lint</pre>
Once installed you should now be able to do something like this:
<pre>ansible-lint clone-vm.yml</pre>
The clone-vm.yml is from my #vBrownBag series. As you can see in this screenshot, it suggests I have some trailing whitespace

<a href="http://www.virtxpert.com/wp-content/uploads/2015/02/ansible-lint-whitespace.png"><img class="aligncenter size-full wp-image-3564" src="http://www.virtxpert.com/wp-content/uploads/2015/02/ansible-lint-whitespace.png" alt="ansible-lint-whitespace" width="672" height="189" /></a>Once I tiddy up the extra whitespace in the playbook, no suggestions are returned.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/02/ansible-lint-fixed.png"><img class="aligncenter size-full wp-image-3566" src="http://www.virtxpert.com/wp-content/uploads/2015/02/ansible-lint-fixed.png" alt="ansible-lint-fixed" width="675" height="192" /></a>That is a pretty basic example, let's say I've missed something such as a { when using vars_prompt, here you can see I have a missing backet for vm

<a href="http://www.virtxpert.com/wp-content/uploads/2015/02/ansible-lint-example2.png"><img class="aligncenter size-full wp-image-3569" src="http://www.virtxpert.com/wp-content/uploads/2015/02/ansible-lint-example2.png" alt="ansible-lint-example2" width="675" height="193" /></a>

Once again, now that it is fixed, no suggestions are returned. One thing that at least this specific tool does not help with is spacing errors, so your playbook will need to be valid, running ansible-lint here for example where my spacing is incorrect results in an general Ansible error, though it does point out where the error likely is:

<a href="http://www.virtxpert.com/wp-content/uploads/2015/02/ansible-lint-error.png"><img class="aligncenter size-full wp-image-3570" src="http://www.virtxpert.com/wp-content/uploads/2015/02/ansible-lint-error.png" alt="ansible-lint-error" width="676" height="616" /></a>

Going forward I'll certainly be looking into using this when writing a playbook to ensure general recommended practices are adhereed to. I'm still on the lookout for a tool that can help with spacing though!