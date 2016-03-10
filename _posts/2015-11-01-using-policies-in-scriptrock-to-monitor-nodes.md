---
ID: 4009
post_title: >
  Using Policies in ScriptRock to monitor
  nodes
author: Jonathan Frappier
post_date: 2015-11-01 13:51:15
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/using-policies-in-scriptrock-to-monitor-nodes/
published: true
dsq_thread_id:
  - "4280395854"
---
In my last post, I took a look at using ScriptRock to compare two nodes to see if their configuration state was identical. While this might be useful for troubleshooting scenarios, in my last example ensuring a Domain Controller was configured properly, you wouldn't want to assume that a particular node is configured as desired at any given point in time - even if it is working as expected.

Consider a simple example of a web server. You may want to require HTTPS on some or all of the directories on the web server, however maybe a junior admin as removed this setting while troubleshooting and doesn't revert back to the original configuration. Now, both HTTP and HTTPS will work. Is the node in the desired state? Well it works but it isn't where you want it to be, and as such using this node as your reference might lead to other nodes being configured incorrectly.

The nice folks at ScriptRock have taken this into account and allow you to create <strong>policies</strong> to ensure nodes have the correct configuration. You can still use a known good node as a reference host to create the policy, however going forward the policy is its own item, and you don't rely on the original node to be in the correct state. In fact, you can use the policy from your reference node, on your reference node to ensure no unwanted changes have been made. Let's take a look.

If you haven't already, add a node or two to ScriptRock (<a href="http://www.virtxpert.com/comparing-windows-nodes-with-scriptrock/">see my previous post</a> - the examples are most useful with at least two nodes), now find the scan that you want to use as your policy. Here you can see I am using my Domain Controller again as a reference and have my scan from today selected.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/scriptrock-node.png"><img class="aligncenter size-full wp-image-4011" src="http://www.virtxpert.com/wp-content/uploads/2015/11/scriptrock-node.png" alt="scriptrock-node" width="1103" height="603" /></a>

Right click on the solid grey circle

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/create-policy.png"><img class="aligncenter size-full wp-image-4013" src="http://www.virtxpert.com/wp-content/uploads/2015/11/create-policy.png" alt="create-policy" width="362" height="275" /></a>

Go to Add to Policy &gt;&gt; All Nodes (or the group of your choice) &gt;&gt; New Policy. Enter a name for your policy, for example "Public IIS" or "Corporate DC" and click the build button. After a few moments, it will analyze the nodes in the folder you selected. Of course the reference node in this case should pass 100% as you see here

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/scriptrock-ref-node-policy.png"><img class="aligncenter size-full wp-image-4014" src="http://www.virtxpert.com/wp-content/uploads/2015/11/scriptrock-ref-node-policy.png" alt="scriptrock-ref-node-policy" width="1040" height="605" /></a>

A blue notice bar has also appeared at the top alert you that the policy has been appled to, in my case the Windows group, and it affects two nodes. Let's take a look at the other node. Navigate back to the your list of nodes (Nodes &gt;&gt; All Nodes or the group you selected) and I am going to click on the vxprt-iaas01 node which I added because I wanted another node that wouldn't match for testing/demo purposes.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/script-rock-compared-node.png"><img class="aligncenter size-full wp-image-4016" src="http://www.virtxpert.com/wp-content/uploads/2015/11/script-rock-compared-node.png" alt="script-rock-compared-node" width="1054" height="604" /></a>

Since I compared two nodes I knew were dissimilar, I see several failed checks as you might expect. Hopefully if you are comparing production nodes that should be the same you are not finding many failures!

While the ability to compare two nodes on the fly while troubleshooting is certainly useful, being able to create policies to ensure all nodes match the desired state you originally configured is a great feature, not only when you are on call and get paged at 2A.M. but to ease the pain/concerns during those annual security audits. If you didn't read the last post, it is probably also worth noting that ScriptRock is free for up to 10 nodes!