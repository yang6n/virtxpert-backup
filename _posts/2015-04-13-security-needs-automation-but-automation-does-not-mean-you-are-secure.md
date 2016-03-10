---
ID: 3638
post_title: >
  Security needs automation, but
  automation does not mean you are secure
author: Jonathan Frappier
post_date: 2015-04-13 08:00:10
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/security-needs-automation-but-automation-does-not-mean-you-are-secure/
published: true
dsq_thread_id:
  - "3677784470"
---
A couple of weeks ago a question was posted on the Ansible LinkedIn group <a href="http://www.ansible.com/security-stig" target="_blank">stemming from an Ansible role for security CentOS</a>. The question, whether Automation is the only way to ensure security. My brief social media shorted response was
<blockquote>Completely agree. If you aren't automating then you can't really claim to be secure</blockquote>
This caused some fuss on the post, with most disagreeing with me. Now I stand by my answer, you cannot be secure if you are not automating, but to further my answer, you are not necessarily secure just because you are automating. Security is not just something you turn on, said another way its not binary, you don't just turn on security. Security consists of many layers, not the least of which is truly understanding your companies business, goals, requirements, processes, and people. With that understanding, you can now apply any specific security measures you may need to abide by. For example if accept credit cards then appropriate safe guards need to be taken to ensure data is encrypted and <a href="https://www.pcisecuritystandards.org/pdfs/pci_fs_data_storage.pdf" target="_blank">certain elements such as the validation number are not stored</a>.

Now, if you are not adhering to those requirements, there is no automation process in the world that can secure you. However, even with the most specific of run books, security teams, engineers, and auditors ensuring you have done everything technically possible to ensure security, you cannot truly say you are secure with a means to automate the installation, and configuration as you have defined them.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/04/heartbleed.png"><img class="alignleft  wp-image-3666" src="http://www.virtxpert.com/wp-content/uploads/2015/04/heartbleed-248x300.png" alt="heartbleed" width="162" height="196" /></a>Another argument in the group discussion was that automation can also lead to widespread vulnerabilities by opening security holes. And while this is true, my previous statements still hold true - you need to have the proper security processes, and details in place before you automate them. Now, say for example, something like Heartbleed comes along again - how quickly would it take you to patch even 10 systems? What about 100? or 1000 if you are doing it by hand? Much longer than it would take to leverage something to patch the systems automatically.

Automation, configuration management, devops; none of these things are a panacea - however security teams <del>should</del> need be relying on automation, not manual efforts to configure, and secure systems.