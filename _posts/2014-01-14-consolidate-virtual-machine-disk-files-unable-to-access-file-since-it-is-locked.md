---
ID: 1836
post_title: 'Consolidate virtual machine disk files <hostname> Unable to access file since it is locked'
author: Jonathan Frappier
post_date: 2014-01-14 07:55:33
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/consolidate-virtual-machine-disk-files-unable-to-access-file-since-it-is-locked/
published: true
dsq_thread_id:
  - "2120851972"
---
I recently ran into an error where an alarm was triggered due to a VM needing to be consolidated, however when I attempted to consolidate the log files It failed with the error "Consolidate virtual machine disk files &lt;hostname&gt;. Unable to access file since it is locked."  This occurred with the both the VM powered on and powered off.  VMware KB Article 2017072 suggested this could be caused by backup software snapshots, which in this case was unlikely because the VM is not backed up (throw away test VM if you are worried :) ).  There were several steps in the KB, however I was able to solve this simply with a storage vMotion to a new datastore, then consolidating the disk.