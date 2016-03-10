---
ID: 3891
post_title: 'Meet Meat &#8211; The free Git collaboration tool'
author: Jonathan Frappier
post_date: 2015-07-24 14:44:04
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/meet-meat-the-free-git-collaboration-tool/
published: true
dsq_thread_id:
  - "3967388081"
---
Man, I thought I came up with that headline before anyone else; turns out Meat is already using it. What is Meat you ask? From their mouths; "Git is a free collaboration platform with built-in deployments"

Git at its core is a version control system, and since Meat is based on Git it will do that. If you want to learn more about version control with Git <a href="https://www.git-tower.com/learn/" target="_blank">check out these great tutorials from Git-Tower</a>. But why use Meat, GitHub is already free for certain types of teams/repositories? One of the cool things about Meat is you can run it within your own data center, so for organizations with strict security requirements, or that just are quite ready to take the plunge you can benefit from Git version control privately...oh and did I mention it is (currently) free?

Okay, but then why not just run Git if I don't want to use GitHub? Another great question. The team over at Meat has built some very nice tools into their solution. While some of this tools may not be trendy cli things, they do have a use case for junior developers or other collaborators who may not have a comfort level with cli tools.

First up, they have built a web based editor (I need to see how it treats these edits in the lab, I would hope its not means to by pass the very thing it is meant to be "version control") so you can browse and view files.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/07/meat.png"><img class="aligncenter size-full wp-image-3892" src="http://www.virtxpert.com/wp-content/uploads/2015/07/meat.png" alt="meat" width="534" height="454" /></a>

Beyond just code repository, there is also a release management tool that allows you to deploy your code directly to your servers, and even appears to support automated deployments. You could now potentially replace two separate tools such as Git/GitHub and Jenkins with Meat.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/07/meat-deployment.png"><img class="aligncenter size-full wp-image-3893" src="http://www.virtxpert.com/wp-content/uploads/2015/07/meat-deployment.png" alt="meat-deployment" width="684" height="447" /></a>

&nbsp;

You can also stage actions to happen in a specific order, for example uploading files to S3 or sending notifications. I have a question out on Twitter to find out if these actions are idempotent; that is to say will they always run, or only if they need to run. For example, in Ansible if I say to create a file, but the file has already been created, it won't do work that has already been done. This is in contrast to scripts which, without proper checking and handling, will just do the thing they are asked to do even if its not needed.

There are many more features available, my next step will be to install the local version into my lab. Meat is delivered as an OVA, so folks familiar with VMware shouldn't have a problem installing this in their labs. If you are interested in trying it out, <a href="https://getmeat.io/" target="_blank">head over to getmeat.io</a> and sign up! Hopefully more to come here soon