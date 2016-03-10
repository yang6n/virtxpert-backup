---
ID: 1556
post_title: Installing Ansible and AWX
author: Jonathan Frappier
post_date: 2013-11-22 09:58:10
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/installing-ansible-awx/
published: true
dsq_thread_id:
  - "1989169712"
---
I hope this Ansible post will turn into a series shortly, but every series starts with a first step and that first step is installing the platform to do some POCs.

<strong>What is Ansible</strong>

For those unfamiliar with Ansible, it is a configuration management platform, along the lines of Puppet or Chef which might be two of the more well known tools.  Ansible is relatively young, just having <a href="http://blog.ansibleworks.com/2013/11/21/ansible-1-4-released/" target="_blank">released version 1.4</a> on 11/21/13 which included 33 new modules (I hope to get into modules in a future post).  Ansible comes in<a href="http://www.ansibleworks.com/pricing/" target="_blank"> two versions</a>, a free command line only open source version and AWX, their enterprise platform.  Ansible does provide AWX free for up to 10 managed machines (physical or virtual).  Ansible uses SSH to communicate with the managed machines, no need to install any agents!  Another option that a co-worker found is called <a href="http://jpmens.net/2012/10/01/dramatically-speeding-up-ansible-runs/" target="_blank">Fireball-Mode</a> which uses <a href="http://zeromq.org/" target="_blank">0mq</a> (Zero-MQ) to more quickly run playbooks.  Playbooks are something I hope to cover in a future post,  but basically a analogous to cookbooks in Chef or manifests in Puppet.

With that brief intro out of the way, lets start installing!

<strong>Ansible Installation</strong>

I am going to skip the linux setup steps, so make sure you have a linux server to install this on.  This example will review installing on CentOS 6.4.  First we will install Ansible OSS, later AWX will sit on top of the Ansible install to provide the GUI/Management features such as role based access control.

First, we need to add an additional YUM repository as it is not part of the defaults.  The easiest way to do this is:
<pre>yum install http://mirror.oss.ou.edu/epel/6/i386/epel-release-6-8.noarch.rpm</pre>
Next, its a simple
<pre>yum install ansible</pre>
Yum as you would expect installs all the dependencies for Ansible to work, mostly Python packages.  At this point Ansible is installed, if you type Ansible in your shell you will see a list of the options available

<a href="http://www.virtxpert.com/wp-content/uploads/2013/11/ansibleoptions.png"><img class="aligncenter size-full wp-image-1557" alt="ansibleoptions" src="http://www.virtxpert.com/wp-content/uploads/2013/11/ansibleoptions.png" width="643" height="372" /></a>

Installing AWX is not to hard, however there was a step missed in the official AWX user guide that is not included in Anisble OSS:
<pre>yum install libselinux-python</pre>
Now that we have that package installed download AWX (if you dont have WGET in your VM, yum install wget) and extract
<pre>wget http://ansibleworks.com/releases/awx/setup/awx-setup-latest.tar.gz

tar -zxvf awx-setup-latest.tar.gz</pre>
At this point you could install, and Ansible would come up with the default username and password of admin / password but I would suggest edit /group_vars/all to change the admin password because you probably want to change the httpd server alias in this file anyways to have a valid hostname for your install, so
<pre>vi /awx-setup-ver#/group_vars/all</pre>
The ver# will change, when I wrote this it was 1.3.1, and as I mentioned above 1.4 was just released.  Now that you have everything installed, you can run
<pre>/awx-setup-ver$/setup.sh</pre>
or ./setup.sh if you are in that folder.  The install will start and being configuring all the various components.  Once complete you should be able to head to your servers IP address (no special ports needed) and log into AWX.

<a href="http://www.virtxpert.com/wp-content/uploads/2013/11/ansible.png"><img class="aligncenter size-full wp-image-1558" alt="ansible" src="http://www.virtxpert.com/wp-content/uploads/2013/11/ansible.png" width="598" height="377" /></a>

<a href="http://www.virtxpert.com/wp-content/uploads/2013/11/emptyansible.png"><img class="aligncenter size-full wp-image-1559" alt="emptyansible" src="http://www.virtxpert.com/wp-content/uploads/2013/11/emptyansible.png" width="628" height="496" /></a>

&nbsp;

<strong>Summary</strong>

In this post, we reviewed the basics for getting Ansible installed so you can log into the web interface.  In the next post I am going to review the hierarchy of Ansible.  One of my goals is to see if Ansible can be used with ESXi to do configuration management.  In its current state it does not work with the vMA because of the state change of the shell once you log into vCenter but wondering if it will work connecting directly to an ESXi host via SSH.