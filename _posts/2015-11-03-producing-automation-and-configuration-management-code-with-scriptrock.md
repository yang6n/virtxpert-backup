---
ID: 4026
post_title: >
  Producing automation and configuration
  management code with ScriptRock
author: Jonathan Frappier
post_date: 2015-11-03 13:50:28
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/producing-automation-and-configuration-management-code-with-scriptrock/
published: true
dsq_thread_id:
  - "4286727717"
---
While ScriptRock is great at monitoring and reporting on configuration state, it is not a configuration management tool in the way that Ansible or CFEngine is. They do, however give you the capability of generating what they called "automation snippets" for many popular configuration management tools to either correct an item that has failed the policy check, or even create entire "automation snippets" to full configure a node.

For example, consider a web server that requires a specific version of Java, if the node fails the policy check because a newer version of Java was installed you could simply right click on the failed item and go to Create Automation Snippet and select the type of snippet - a playbook  for Ansbile, a Manifest for Puppet, etc...

As always, starting with a few nodes added to ScriptRock and you will need to drill down into one of those nodes. Since my previous posts were demo'd with Windows, I'll use Linux here just to mix it up a bit.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/scriptrock-inventory.png"><img class="aligncenter size-full wp-image-4032" src="http://www.virtxpert.com/wp-content/uploads/2015/11/scriptrock-inventory.png" alt="scriptrock-inventory" width="1140" height="436" /></a>

There are several areas you can right click to generate these snippets.

First, you can generate the automation snippet for all items right clicking the grey circle at the top

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/all-snippet.png"><img class="aligncenter size-full wp-image-4034" src="http://www.virtxpert.com/wp-content/uploads/2015/11/all-snippet.png" alt="all-snippet" width="832" height="407" /></a>

For example if I create an automation snippet here for Ansible, (Create Playbook Snippet) it will give me the code for every package, user, folder, etc... on the node

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/ansible-automation-snippet.png"><img class="aligncenter size-full wp-image-4035" src="http://www.virtxpert.com/wp-content/uploads/2015/11/ansible-automation-snippet.png" alt="ansible-automation-snippet" width="1143" height="692" /></a>

This is obviously noisy, but also very complete if you want to bring another node into the same configuration very easily. You could also create an automation snippet for a specific category such as EnvVars, files, or packages. Additionally you can also be as granular as a specific item, a likely scenario for a quick fix to a node that is not in compliance. Here you can see I searched for httpd, expanded Packages and selected the httpd package by itself.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/snippet-httpd.png"><img class="aligncenter size-full wp-image-4036" src="http://www.virtxpert.com/wp-content/uploads/2015/11/snippet-httpd.png" alt="snippet-httpd" width="686" height="312" /></a>

This will produce, as you might expect, just a snippet to ensure httpd is installed

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/snippet-httpd-only.png"><img class="aligncenter size-full wp-image-4037" src="http://www.virtxpert.com/wp-content/uploads/2015/11/snippet-httpd-only.png" alt="snippet-httpd-only" width="1085" height="331" /></a>

I think that is all I have for ScriptRock for now, as you can see this is a very handy tool for several use cases such as troubleshooting, ensuring device configuration, and even vulnerability scanning.