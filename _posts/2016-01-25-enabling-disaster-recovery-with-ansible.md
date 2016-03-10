---
ID: 4270
post_title: Enabling Disaster Recovery with Ansible
author: Jonathan Frappier
post_date: 2016-01-25 10:24:45
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/enabling-disaster-recovery-with-ansible/
published: true
dsq_thread_id:
  - "4521975677"
---
I always enjoy sharing my "ah-ha" moments, that is when you start to do something - or in this case are already doing something, that helps with other projects. This is a brief story about how we used Ansible to enable disaster recovery without needing to replicate virtual machines, or buy additional software.

I was working at a startup that had legal requirements to maintain a disaster recovery plan, yes Frank we had disaster recovery at a startup! The disaster recovery plan, however was put together in support of previous versions of our software, and needed to be updated to support our new version. On top of the legal requirements, we had a new potential customer who wanted to see our disaster recovery plan in action - this customer would be on our new platform, so the old plan wasn't an option!

It was a pretty standard application, nothing crazy or "web-scale" to the likes of a Netflix, there were several reverse proxies, application front ends, management systems, etc. There were certain application configuration files, and several auxiliary files used by the application on a day to day basis that were stored on the virtual machine running the application. While important, those configuration and auxiliary files could also be recovered from backups, but important nonetheless. The really important application data was stored and accessed by our application on a EMC Celerra NAS. The virtual machines running the application were also of the "pet" variety - tweaked, and updated, and patched since launch to get them working just right. We didn't want to lose this information.

As a VMware shop, it seemed pretty obvious what we needed to do, buy VMware SRM and go on with life. I spent several weeks researching SRM, understanding how it would work within our environment and coming up with a solution for replicating virtual machines to the DR site. At the time, we only replicated our Veeam backups to DR, along with replication of our production Celerra to a VNX at the DR site. My manager and I were talking through what we would need to do with SRM in order to reconfigure the application servers in order to work properly at the DR site, it was getting hairy but obviously doable.

I'd like to pause here and rewind a bit. While we were planning our new DR strategy, and ensuring we could meet customer timelines, one of my co-workers was in the process of migrating from bash scripts to manage and deploy software to a configuration management tool; we had selected Ansible but I suspect you could achieve similar results with other tools. The Ansible implementation was going great, that is to say Ansible was very easy to deploy, we were just making sure that modules were being leveraged in the correct way rather than just making a big playbook with a bunch of shell or raw modules using the same commands as the bash script.

That's when the light bulb light up! As we were talking through how we would use SRM to alter the configuration files for the application, we realized that Ansible was already managing the configuration of the application, the application configuration files stored on the virtual machine which would need to be edited to support the network at the DR site all of a sudden seemed a little bit less important. We still, however had this auxiliary files the application would access (think public keys for decryption information, etc) that were stored on the virtual machine. What should we do? Well we were already storing the actual application data on a NAS, which was already being replicated and available at the DR site; what if we moved that auxiliary type data into a share and mounted it so it could be accessed as well? Once replication was setup, all we needed to do now was have Ansible mount the file system so it could be accessed, we tested this theory out and sure enough it worked.

But, as many shops have done, there were hand made tweaks to the application servers to improve performance, could we get away with losing that information? As you might expected, we couldn't, but we made the decision to work through performance issues and add those to the Ansible playbook so moving forward, there was nothing specific to a virtual machine in any environment that couldn't be managed, controlled, and configured through Ansible. What we didn't have the option of then, that you could do today is use a tool like ScriptRock to monitor and record the configuration of your servers, as well as monitor and alert on drift.

Our application could now be fully deployed in production, as well as any other environment we needed, including DR with just a basic virtual machine template and an Ansible playbook.