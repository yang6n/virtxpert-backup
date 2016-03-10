---
ID: 466
post_title: 'VMware Business Continuity &#038; Disaster Recovery (BCDR Design) Notes from Module 3'
author: Jonathan Frappier
post_date: 2013-02-25 20:17:40
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vmware-business-continuity-disaster-recovery-bcdr-design-notes-from-module-3/
published: true
dsq_thread_id:
  - "1105255712"
---
Notes from the Disaster Recovery free course on MyLearn

BCPs and DRPs are complex. Each decision has positive or negative impact. DRPs must exist before BCP decision trees.

<strong>Level of Service</strong>
Will recovery site provide same level of service as production?
No - plan for some apps not running, or running with lower level of service/performance. Follow BIA guidelines for what apps are needed/required.
Yes - Is it a dedicated recovery site?
Yes - Ensure enough capacity, can be very expensive.
No - Does it provide enough capacity for original ops + recovery ops?
Yes - Has extra capacity, consider distributed DRP (multiple recovery sites)

<strong>Production Impact</strong>
Will recovery operations impact production systems at the recovery site (if site is not a dedicated recovery site)

Should prod apps in recovery site (e.g. apps that are running during normal business) but shutdown during recovery? Run with less capacity?
Ensure recovery site has enough capacity to run necessary apps for prod + recovery.

<strong>Backup Design</strong>
Same backup design during BCP period that was used at the recovery site?
No - ensure critical data is protected, reduce backups during BCP period to what only what is required. Dont forget offsite backups.

Yes - do you have the same infrastructure?
No - see above “no”
Yes - simplifies backup design in BCP, increased protection due to not eliminating some backups, cost are increased

<strong>Power Management</strong>
Will DPM (dynamic power management) be used during BCP period?
No - ensure capacity/cost to run
Yes - Helps reduce cost if there is enough capacity to run all work loads.

<strong>Personnel Facilities</strong>
Will employee workspace be provided?
No - Have remote control management (VDI) to ensure staff has access. Possible strain on staff if long BCP
Yes - will they have the same amount space?
No - smaller workspace is more cost effective for limited period of operations. Have remote control
Yes - Mainiating space, improves morale - more costly.

<strong>Failback speed</strong>
Once the primary site is back online, should failback be attempted quickly?
No - slow failback, less stressful, more chance of success but operations at recovery site tend to be more expensive and slower/limited
Yes - minimizes negative impact of operating at remote site. Faster failback can be error prone

<strong>Failback design</strong>
Will failback be modular (done in pieces or all at one)?
No - if all failback at once, hard to test and implement. Unsuccessful failback can be as bad as original disaster.
Yes - Easier to test, less traumatic. Still requires careful testing/system dependencies.

<strong>Failback order</strong>
Will failback order be based on BIA priority?
No - If apps are first brought online during DRP, it may not be first to failback. Infrastructure services typically must come first to support failback. If apps at recovery site is working well, take time and test properly.
Yes - If app is deemed high priority during DRP and has reduced capacity at recovery site, try to return to production as soon as possible.