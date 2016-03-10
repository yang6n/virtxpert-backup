---
ID: 3265
post_title: >
  Ansible Playbooks – A more advanced
  example
author: Jonathan Frappier
post_date: 2014-11-26 09:00:30
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/ansible-playbooks-advanced-example/
published: true
dsq_thread_id:
  - "3264745757"
---
[display-posts category="Ansible" display-posts posts_per_page="15"]

In my last post, I showed you a simple example of an Ansible playbook using yum to update a package.  Still really awesome, especially when you consider how often you might need to do that and how simple it is to handle that type of otherwise manual task.  In this post, I am going to try and put together a slightly more complicated playbook to look at some of the other options available.

<em>**Please note I am not necessarily trying to reflect best practice here, but rather demonstrate some of the different options available in an Ansible playbook.  There is likely an easier way to do this for production purposes**</em>

The simple playbook looks something like this:
<pre>---
- hosts: db
  remote_user: root
  tasks:
  - name: update mysql-libs-latest 
    yum: pkg=mysql-libs state=latest</pre>
So what else can we do?  Let's start at the top.  First and foremost you are probably not going to log into your systems as root, typically you log in with a user account and then use "sudo" to elevate your privileges.  I have created an account on my "db" server called virtxpert, and added that user to the sudoers file.  Now I can do something like this in my playbook:
<pre>---
- hosts: db
  remote_user: virtxpert
  sudo: yes
  tasks:  
  - name: update mysql-libs-latest 
    yum: pkg=mysql-libs state=latest</pre>
Since, as I mentioned in the last post playbooks take an idempotent stance, I can run that playbook again with the remote user being virtxpert and see no changes, because my single task was already complete.  With sudo a requirement now I also need to add --ask-sudo-pass to the command.

[caption id="attachment_3270" align="aligncenter" width="677"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/ansible-playbook-sudo.png"><img class="size-full wp-image-3270" src="http://www.virtxpert.com/wp-content/uploads/2014/11/ansible-playbook-sudo.png" alt="Ansible playbook with sudo" width="677" height="426" /></a> Ansible playbook with sudo[/caption]

As you can see here, everything "worked" as expected - there were no changes that needed to be made.  Now instead of just updating a package, lets install something generally a bit more complicated - PostgreSQL.  I could just do yum: pkg=postgresql state=;latest and in CentOS6.4 that would be Postgres 8.4 - but what if I want 9.x?  My playbook would look something like:
<pre>---
- hosts: db
  remote_user: virtxpert
  sudo: yes
  tasks:  
  - name: update mysql-libs-latest 
    yum: name=http://yum.postgresql.org/9.3/redhat/rhel-6-x86_64/pgdg-centos93-9.3-1.noarch.rpm state=present</pre>
And just like that, the playbook runs and I now have PostgreSQL 9.3 available!

<!--more-->

[caption id="attachment_3273" align="aligncenter" width="675"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/ansible-db-build-run.png"><img class="size-full wp-image-3273" src="http://www.virtxpert.com/wp-content/uploads/2014/11/ansible-db-build-run.png" alt="Ansible Playbook example output" width="675" height="426" /></a> Ansible Playbook example output[/caption]

[caption id="attachment_3274" align="aligncenter" width="675"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/ansible-available-postgres-after-playbook.png"><img class="size-full wp-image-3274" src="http://www.virtxpert.com/wp-content/uploads/2014/11/ansible-available-postgres-after-playbook.png" alt="Available PostgreSQL after Ansible playbook" width="675" height="729" /></a> Available PostgreSQL after Ansible playbook[/caption]

Now I can do something like this in my playbook to ensure I get the version I want installed versus what comes with core:
<pre>---
- hosts: db
  remote_user: virtxpert
  sudo: yes
  tasks:  
  - name: update mysql-libs-latest 
    yum: name=http://yum.postgresql.org/9.3/redhat/rhel-6-x86_64/pgdg-centos93-9.3-1.noarch.rpm state=present
  - name: install PostgreSQL 9.3
    yum: pkg=postgresql93-server state=latest</pre>
Wow, just wow - a few lines of Ansible and PostgreSQL 9.3 is installed.

[caption id="attachment_3277" align="aligncenter" width="675"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/ansible-install-postgresql-9.png"><img class="size-full wp-image-3277" src="http://www.virtxpert.com/wp-content/uploads/2014/11/ansible-install-postgresql-9.png" alt="Ansible installed PostgreSQL 9 via Playbook" width="675" height="427" /></a> Ansible installed PostgreSQL 9 via Playbook[/caption]

You can also see it here on the database server itself

<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/postgres-installed-server.png"><img class="aligncenter size-full wp-image-3278" src="http://www.virtxpert.com/wp-content/uploads/2014/11/postgres-installed-server.png" alt="postgres-installed-server" width="675" height="357" /></a>

But after the installation, the PostgreSQL service is set to off and is not started.  We also have initialized PostgreSQL yet.  We could possibly use the args service option,but lets try the shell tasks to run service postgresql-9.3 initdb!
<pre>- name: initialize postgresql
    shell: service postgresql-9.3 initdb</pre>
Wow - how easy is that!  Now in the grand scheme of things, this might not be the best way to initialze PostgreSQL, after all we are just telling Ansible to run this command, it has no way to know whether it has been run before or not but I wanted to illustrate using this option.

Now, how could I do make sure that PostgreSQL starts with the server and starts up after the playbook is run?  Well now we can use what is called a handler for this.  For example we might want something like:
<pre>handlers:
    - name: start postgres
      service:  name=memcached state=restarted</pre>
The handlers section goes in the end of the playbook file, then we "notify" the handler from the task so our overall playbook looks something like this:
<pre>---
- hosts: db
  remote_user: virtxpert
  sudo: yes
  tasks:
  - name: install updated PostgreSQL PGDG
    yum: name=http://yum.postgresql.org/9.3/redhat/rhel-6-x86_64/pgdg-centos93-9.3-1.noarch.rpm state=present
  - name: install postgresql93-server
    yum: pkg=postgresql93-server state=latest
  - name: initialize postgresql
    shell: service postgresql-9.3 initdb
  notify:
     - start postgres

  handlers:
     - name: start postgres
     service: name=postgresql-9.3 state=started enabled=yes
</pre>
And just like that - PostgreSQL is now started - here is chkconfig --list and ps -ef | grep postgresql-9.3 from the DB server the playbook was run on.  You can see that postgresql-9.3 is now set to on since we set enabled=yes and started since we set state=started

<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/db-server-built-via-ansible.png"><img class="aligncenter size-full wp-image-3280" src="http://www.virtxpert.com/wp-content/uploads/2014/11/db-server-built-via-ansible.png" alt="db-server-built-via-ansible" width="676" height="728" /></a>

That's it for now on Ansible, next I think I want to look at the Ansible and VMware integration - stay tuned!