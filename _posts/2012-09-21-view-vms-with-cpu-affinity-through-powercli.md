---
ID: 146
post_title: >
  View VMs with CPU affinity through
  PowerCLI
author: Jonathan Frappier
post_date: 2012-09-21 12:22:20
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/view-vms-with-cpu-affinity-through-powercli/
published: true
jabber_published:
  - "1348230140"
email_notification:
  - "1348230141"
reddit:
  - 'a:2:{s:5:"count";i:0;s:4:"time";i:1357878358;}'
dsq_thread_id:
  - "1134442616"
---
Connect-VIServer server

Get-Cluster "Cluster Name" | Get-VM | Get-View | foreach {Write-output $._Name $_.Config.CpuAffinity.AffinitySet}