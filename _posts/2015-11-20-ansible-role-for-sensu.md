---
ID: 4146
post_title: Ansible Role for Sensu
author: Jonathan Frappier
post_date: 2015-11-20 15:42:26
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/ansible-role-for-sensu/
published: true
dsq_thread_id:
  - "4337005574"
---
I am looking into various monitoring products, and since I may need to install them again, that means automation. With some help from Sarah Zelechoski and Larry Smith, I have the first pass done on an Ansible role for Sensu. There may be better ones out there, or you <a href="https://sensuapp.org/docs/latest/installation-overview" target="_blank">might just want to follow the directions manually</a> but so far this role gets the install working up through the base install with examples. This is just as much about me getting better with Ansible, don't like how I did something? PRs welcome as that is how I will learn from those with more experience.

The role is still a work in progress, so very much as some clean up to do, but should get you going quickly on Ubuntu 14.04. Here is a screenshot of the sensu server log:

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/sensu-running.png"><img class="aligncenter size-full wp-image-4148" src="http://www.virtxpert.com/wp-content/uploads/2015/11/sensu-running.png" alt="sensu-running" width="820" height="255" /></a>

You can grab it from https://github.com/jfrappier/ansible-sensu-role

<a href="https://github.com/jfrappier/ansible-sensu-role"><img class="aligncenter size-full wp-image-4149" src="http://www.virtxpert.com/wp-content/uploads/2015/11/github.png" alt="github" width="1000" height="908" /></a>