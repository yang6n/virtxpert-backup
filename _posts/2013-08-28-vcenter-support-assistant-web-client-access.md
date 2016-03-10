---
ID: 1322
post_title: >
  vCenter Support Assistant Web Client
  Access
author: Jonathan Frappier
post_date: 2013-08-28 09:27:43
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vcenter-support-assistant-web-client-access/
published: true
dsq_thread_id:
  - "1660140803"
---
If you wish to use the VMware vCenter Web Client to access the vCenter Support Assistant, there are a few additional steps you need to perform on the OS you are accessing the appliance from.

1. Based on the OS that the vSphere web client is running on, navigate to the appropriate directory:
Windows 7 or Windows 2k8 server: C:\ProgramData\VMware\vSphere Web Client\
Windows XP: C:\Documents and Settings\All Users\Application Data\VMware\vSphere Web Client
Mac OS-X and Linux: /var/lib/vmware/vsphere-client

2. If the directory already contains a file named "webclient.properties", open it. Otherwise, create it.

3. In the file, please add the following line:
scriptPlugin.enabled=true

4. Restart the vSphere Web Client.