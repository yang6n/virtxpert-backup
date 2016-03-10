---
ID: 4044
post_title: Code Anywhere with @Codeanywhere
author: Jonathan Frappier
post_date: 2015-11-05 18:26:42
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/code-anywhere-with-codeanywhere/
published: true
dsq_thread_id:
  - "4293558259"
---
As a Windows user in a DevOpsifed-Mac-Centric world, finding a good editor is a challenge - the best two native Windows text editors I have found are the good 'ol Notepad++ and more recently <a href="http://www.virtxpert.com/hands-on-with-microsoft-visual-studio-code-code/">Microsoft Visual Studio Code</a>. Recently I was introduced to a web based IDE called CodeAnywhere. There are a ton of great features packed in, but maybe the most impressive to me is the free container they provide you to actually test the code you are writing.

You can chose an empty development box or a number of preconfigured boxes running on either CentOS or Ubuntu using as PHP, Node.js or Python  to name <del>the SEO friendly ones</del> a few. In addition to the boxes I can use right within the web based editor, I can also connect to Google Drive, S3, or GitHub to access my files/code from any device without having to install anything.

For example, in the screenshot below I created a new project called test, connected my GitHub account and selected my Ansible test playbook repo. The wizard then helped me setup a Python container running on CentOS

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/create-container.png"><img class="aligncenter size-full wp-image-4045" src="http://www.virtxpert.com/wp-content/uploads/2015/11/create-container.png" alt="create-container" width="982" height="840" /></a>

Once the container is provisioned, I can see the specs for my environment, and have a console to it with all of the files from my selected GitHub repo ready to role! Here you can see I've opened one of my playbooks in vi in the console at the bottom of the screen and opened a file in the text editor in the top.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/container.png"><img class="aligncenter size-full wp-image-4046" src="http://www.virtxpert.com/wp-content/uploads/2015/11/container.png" alt="container" width="985" height="740" /></a>

I'll be using this for the most part going forward to see how comfortable it is compared to OS native applications. One item I hope they add is the ability to display markup languages split screen, similar to how I do in Microsoft Code and add support for Markdown. Not bad for a free web based IDE huh?