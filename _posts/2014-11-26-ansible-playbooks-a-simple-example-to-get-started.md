---
ID: 3237
post_title: 'Ansible Playbooks &#8211; A simple example to get started'
author: Jonathan Frappier
post_date: 2014-11-26 08:00:56
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/ansible-playbooks-a-simple-example-to-get-started/
published: true
dsq_thread_id:
  - "3264587254"
---
[display-posts category="Ansible" display-posts posts_per_page="15"]

With Ansible installed, and a basic inventory file created we can now move beyond ad-hoc tasks (which by the way is still a great use case for Ansible) and take advantage of Playbooks.  Playbooks are a set of commands organized as required to perform complicated tasks.  Maybe you have provisioned dozens or hundreds of new virtual machines and you now need to make sure they are in the desired state - standardized versions of OpenSSL or MySQL for example, then deploy your custom software packages to those servers; that (simplistically) is where playbooks come in.

Ansible Playbooks are written in YAML format, generally considered a human readable syntax compared to say HTML other markup languages.  You can <a href="http://docs.ansible.com/YAMLSyntax.html" target="_blank">read more about YAML </a>on Ansible sites.  Let's take a basic use case here (time to move on from using ping).  I have a server installed with its included version of MySQL-libs - in my case CentOS 6.4 with mysql-libs 5.1.66-2.el6_3 but my requirements state I need to always be on the latest version of this package, currently 5.1.73

[caption id="attachment_3244" align="aligncenter" width="672"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/ansible-mysql-libs-version-example.png"><img class="size-full wp-image-3244" src="http://www.virtxpert.com/wp-content/uploads/2014/11/ansible-mysql-libs-version-example.png" alt="Checking mysql-libs version before running Ansible playbook" width="672" height="291" /></a> Checking mysql-libs version before running Ansible playbook[/caption]

On a single server, maybe even two or 3 I might just ssh or clusterssh to those servers and run the update command manually; again I'd probably suggest against that but as you get into 10s or 100s of systems that is not sustainable.  Enter Ansible playbooks.  Now I did not see (or missed) where the standard location for playbooks is, so I just created a playbooks folder in my Ansible folder, and named my file update-mysql-libs.yml.  First we need to define the hosts and user account we will run the playbook on.  Recall from my last posts I have a two groups in my inventory file; web and db.  In my case my playbook might start off like:
<pre>---
- hosts: db
  remote_user: root</pre>
This will instruct the playbook to run on all hosts in my db group from my inventory file.  Remote_user, as you might expect is the user which to run the command from.  Now we need a task or list of tasks to run; in my case maybe something like this will do:
<pre>tasks:
  - name: update mysql-libs-latest
    yum: pkg=mysql-libs state=latest</pre>
Neat thing about tasks, they only run if they need to.  If mysql-libs is alrady the latest version, why update it again?  Ansible will check whatever you are doing to see if it needs to be done, and if it does will bring it to the desired state.  Pretty simple example so far, here is what it looks like all together:

&nbsp;

Now, to run my playbook I use ansible-playbook instead of just ansible, for example:
<pre>ansible-playbook /ansible/playbooks/update-mysql-libs.yml</pre>
Oops, looks like I forgot to mention something.  Ansible prefers the use of SSH keys to systems, not passwords so running the above command gave me the following error:

[caption id="attachment_3249" align="aligncenter" width="676"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/ansible-playbook-failed-myfault.png"><img class="size-full wp-image-3249" src="http://www.virtxpert.com/wp-content/uploads/2014/11/ansible-playbook-failed-myfault.png" alt="Example failed Ansible playbook" width="676" height="426" /></a> Example failed Ansible playbook[/caption]

Guess its finally time to start using keys, guess that will be another post for all my Windows friends :)  I can, however run this as is and have it prompt for a password, I just need to add the --ask-pass flag as we did in the previous posts, so something like:
<pre>ansible-playbook /ansible/playbooks/update-mysql-libs.yml --ask-pass</pre>
As you can see Ansible prompted me for the SSH password, found the hosts from my [db] group in my inventory file and suggests that it changed 1 item.  Let's go check the version on our DB server (.137)

[caption id="attachment_3250" align="aligncenter" width="675"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/ansible-successful-playbook.png"><img class="size-full wp-image-3250" src="http://www.virtxpert.com/wp-content/uploads/2014/11/ansible-successful-playbook.png" alt="Ansible playbook successfully run" width="675" height="426" /></a> Ansible playbook successfully run[/caption]

&nbsp;

Yup, mysql-libs has been updated as expected!

[caption id="attachment_3251" align="aligncenter" width="673"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/ansible-remote-host-updated.png"><img class="size-full wp-image-3251" src="http://www.virtxpert.com/wp-content/uploads/2014/11/ansible-remote-host-updated.png" alt="Ansible remote host updated via playbook" width="673" height="421" /></a> Ansible remote host updated via playbook[/caption]

This was a simple playbook with 1 item in it, but playbooks can be much more complex.  In a future post, I hope to look at a more advanced playbook file, for now need to go figure out the whole SSH key thing.  Much of this post was summarized from <a href="http://docs.ansible.com/playbooks_intro.html" target="_blank">Ansible's official documentation</a> to provide a more simple example of what is possible if you are just getting started with Ansible.  Please check out their official documentation on Playbooks to see everything that is possible.