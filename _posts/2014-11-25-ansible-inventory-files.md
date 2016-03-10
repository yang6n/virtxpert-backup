---
ID: 3222
post_title: Ansible Inventory Files
author: Jonathan Frappier
post_date: 2014-11-25 12:00:39
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/ansible-inventory-files/
published: true
dsq_thread_id:
  - "3253763212"
---
In my last post on Ansible, the installation documentation walked us through a simple example of how to issue a command on a host by putting 127.0.0.1 in the inventory file.  Now as you know 127.0.0.1 is that server itself;  the real power of an automation tool is working on multiple systems.  You can manage which systems Ansible runs commands or playbooks on (more on playbooks in a future posts) by putting them in an inventory file - and what's really cool; Ansible does this all agentless!

If you look at your inventory file (/etc/ansible/hosts) you can see just the single IP address in there like this:

[caption id="attachment_3223" align="aligncenter" width="672"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/ansible-hosts-file.png"><img class="size-full wp-image-3223" src="http://www.virtxpert.com/wp-content/uploads/2014/11/ansible-hosts-file.png" alt="Ansible simple hosts file" width="672" height="424" /></a> Ansible simple inventory file[/caption]

Handy, but again I want to be able to perform operations on multiple systems.  I setup another linux system in my lab, in this case it has an IP address of 192.168.6.137 so all I need to do is add that file into my inventory file;
<pre>echo "192.168.6.137" &gt;&gt; /etc/ansible/hosts</pre>
Now the inventory file should look like this

[caption id="attachment_3225" align="aligncenter" width="677"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/ansible-hosts-file-two-hosts.png"><img class="size-full wp-image-3225" src="http://www.virtxpert.com/wp-content/uploads/2014/11/ansible-hosts-file-two-hosts.png" alt="Ansible hosts file with two hosts / IP" width="677" height="423" /></a> Ansible inventory file with two hosts / IP[/caption]

Just as a quick test, and in the case of sshpass to add the servers key to our list of known hosts.  Yup, I can SSH to 192.168.6.137.  Let's try the same example from the installation post:

[caption id="attachment_3227" align="aligncenter" width="673"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/ansible-ping-multiple-hosts.png"><img class="size-full wp-image-3227" src="http://www.virtxpert.com/wp-content/uploads/2014/11/ansible-ping-multiple-hosts.png" alt="Ansible ping multiple hosts" width="673" height="425" /></a> Ansible ping multiple hosts[/caption]

Just like that, we can now perform tasks on multiple hosts; very cool.  But I suspect many people are managing more than two hosts (though even with just two I'd highly suggest Ansible), or even if there are two you may have a different purpose for each host - say a web and database server.  You may not want to install PostgreSQL or MySQL on your web server, but with the above scenario you'd be running your Ansible commands on all of the hosts in your inventory file - would you edit your inventory file every time you needed to do something; kind of defeats the point of automation.  Have no fear, we can logically group items in the inventory file.  Using the previous example lets call the Ansible server our "web" server and .137 our "db" server; your inventory file would look something like this:

[caption id="attachment_3229" align="aligncenter" width="676"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/ansible-hosts-groups.png"><img class="size-full wp-image-3229" src="http://www.virtxpert.com/wp-content/uploads/2014/11/ansible-hosts-groups.png" alt="Ansible hosts file with groups" width="676" height="428" /></a> Ansible inventory file with groups[/caption]

Now, if we issue the following command what do you think will happen?
<pre>ansible db -m ping --ask-pass</pre>
If you guessed that it would only run the command on 192.168.6.137 you would be correct!

[caption id="attachment_3231" align="aligncenter" width="675"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/ansible-ping-db.png"><img class="size-full wp-image-3231" src="http://www.virtxpert.com/wp-content/uploads/2014/11/ansible-ping-db.png" alt="Ansible ping only DB group" width="675" height="426" /></a> Ansible ping only DB group[/caption]

One last thing I will show you here on inventory files; you can also do thinks like match names or numbers.  For example say you have a range of IP address you use, rather than listing each IP address you could do something like

192.168.6.[1:254]

This would include every IP address in the 192.168.6.x range.  Taking that bit of knowledge, I have this example below:

[caption id="attachment_3232" align="aligncenter" width="673"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/ansible-hosts-group-range.png"><img class="size-full wp-image-3232" src="http://www.virtxpert.com/wp-content/uploads/2014/11/ansible-hosts-group-range.png" alt="Ansible Inventory file match pattern" width="673" height="426" /></a> Ansible Inventory file match pattern[/caption]

Going back to our ping command example, what would happen if I run
<pre>ansible 192-sub -m ping --ask-pass</pre>
Yup, it would attempt to run on each of the 3 IP address in my range - 192.168.6.136, .137 and .138.  Since in my case only one of those hosts is alive, I have one success and two failures!

[caption id="attachment_3233" align="aligncenter" width="675"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/ansible-ping.png"><img class="size-full wp-image-3233" src="http://www.virtxpert.com/wp-content/uploads/2014/11/ansible-ping.png" alt="Ansible ping results" width="675" height="426" /></a> Ansible ping results[/caption]

There is actually much more you can do with inventory files here, <a href="http://docs.ansible.com/intro_inventory.html" target="_blank">check out the Ansible documentation</a> on this as its well written and informative.  While this is getting more awesomer by the moment (yes I said more awesomer), setting up playbooks continues with the awesomeness!