---
ID: 453
post_title: 'VMware Business Continuity &#038; Disaster Recovery (BCDR Design) Notes from Module 2'
author: Jonathan Frappier
post_date: 2013-02-22 06:30:27
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vmware-business-continuity-disaster-recovery-bcdr-design-notes-from-module-2/
published: true
dsq_thread_id:
  - "1099616137"
---
More note taking from, Using Decision Tree to create a Disaster Recovery Plan section of the BCDR Design MyLearn course

<b><b>Complex task to create.  Decision trees to create DRPs.  Have Business Impact Analysis and risk assessment, have RPO and RTO ready.</b></b>

<b>
Application Protection
</b>
Should the application be protected:
If yes - BIA should decide if application is protected
Is the data separate from application, on separate server or files?
If yes protect both servers/data
Should app be combined with other apps?
If no, protect independently

Sample decision tree

<a href="http://www2.virtxpert.com/wp-content/uploads/2013/03/sample-application-decision-tree.jpg"><img class="aligncenter size-full wp-image-539" alt="sample-application-decision-tree" src="http://www2.virtxpert.com/wp-content/uploads/2013/03/sample-application-decision-tree.jpg" width="969" height="727" /></a>

<b>Restoration Priority</b>

Is the app infrastructure related (DHCP, AD) which other servers rely on.
If yes, restore first.
If no, BIA determines how critical it is to the business.
If critical, restore prior to other apps, but not before infrastructure.

<b>Recovery site selection and location </b>

Single site is a dedicated recovery sites, generally simplifies DRP.
Is it extremely remote?
If yes, how will staff get/stay there?
Is it Hot/warm/cold? Hot = more expensive.  Warm = less expensive but longer to bring online.
Multi site are regional, multi-purpose recovery site.

<b>Recovery site connection</b>

Are you replicating data over WAN links?
If yes, are they redundant?
Yes = higher cost, no = less reliable if link is down data cannot replicate.
If no, longer recovery time while tape/data manually delivered

<b>Backup Design</b>

Full or mixed (full, incremental, differential) - may differ from app to app
Diff + Full lowers complexity, but slower backups that incremental
Full only = easiest restore, longer backups, more costly due to space

<b>Storage Architecture</b>

Will OS, apps + data mixed onto same storage/LUNS
If yes - makes DR harder, backups larger, replicating LUNs take more time due to moving all files
Suggest moving swap files to diff datastore/LUNs, have VMDKs with data only on separate file, possibly LUN but increases complexity of VM management

Sample decision tree

<a href="http://www2.virtxpert.com/wp-content/uploads/2013/03/sample-storage-design-tree.jpg"><img class="aligncenter size-full wp-image-541" alt="sample-storage-design-tree" src="http://www2.virtxpert.com/wp-content/uploads/2013/03/sample-storage-design-tree.jpg" width="962" height="724" /></a>

<b>Replication Design</b>
Will you replicate this LUN?
Non-replicated LUN will only be available if loaded from backup media.
Replicated LUNS, will it be frequently replicated?
If yes, more options for RPO, but more bandwidth needed.
Keep multiple snapshots?  If yes more storage space.

<b>Power and facility design</b>
Will you manage power?
If no, you have to provide power and cooling at all time.
If cold site, only need AC during operation.  Need to ensure power.
If yes, cost savings from power and cooling while systems are not in use.

<b>DRP Testing</b>
Can you test part of it without testing entire plan?
If no, will you test complete plan more than once a year?
If no, test once a year at minimum, generally need 3 test cycles before working properly
If yes, helps perfect plan but more expensive/time consuming.
If yes, does it interfere with production?
If yes, harder to test as interferes with business.

<b>**Design test plan modularly, harder but testing easier**</b>

<strong>Disaster Declaration</strong>

Should a disaster be declared?
If no, business continues normally, solve outages locally using normal procedures.
If yes, is it a single person to declare disaster?
Committees may need to approve.  If partial DRP can be implemented, easier to implement for only some systems
Single person can act quicker, but committee may have more reasoned judgement.