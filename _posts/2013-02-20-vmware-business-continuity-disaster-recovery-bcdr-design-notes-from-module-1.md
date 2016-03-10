---
ID: 502
post_title: 'VMware Business Continuity &#038; Disaster Recovery (BCDR Design) Notes from Module 1'
author: Jonathan Frappier
post_date: 2013-02-20 21:51:00
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vmware-business-continuity-disaster-recovery-bcdr-design-notes-from-module-1/
published: true
dsq_thread_id:
  - "1095861897"
---
Strictly a brain dump/note taking page.

Disaster - halts business; harms physical location but also digital/data loss.  If you lose your data, you are likely to go out of business - up to 90% within 1 year.

Services lost - web, email, finances, erp apps unavailable causing busines shutdown.  Redundant app servers do not protect against disaster in the same data center.

What is a disaster - Natural (tornado, hurricane, etc), Man made (infrastructure failure, terrorism).  Disaster depends on how your company designs its network, sets SLAs, builds redundancy.

Disaster is declared by an officer of the company or group of officers, implement DRP/BCP

<strong>3 Categories</strong>

Catastrophone:  Typically natural event, entire data center is destroyed.  Affects geographic area rendering local support services unavailable.

Disaster:  Localized to datacenter, unavailable day or longer.  65% that lose their DC for more than a week go out of business within a year.

Non-disaster:  Service disruption caused by a specific failure

Not a disaster:  Failure of hardware component, temporary service interruption such as power outage.  Small, isolated failures not built into BCP/DRP.

Disaster Recovery Plan (DRP) Objectives:
Minimize downtime:  Streamline processes.
Run book:  Guide to implement DRP, manually creation, maintained by hand.
Reduce risk:  DRP can’t fail, needs to be tested.  Requires additional hardware.
<p dir="ltr">Reduce cost:  Control cost, fast and simple = expensive.  Potentially double cost for duplicate data center.</p>
Physical DR process.  Data is replicated from production to recovery site via replication over WAN or moving via backups.

Complications:  Lots of data to identify and replicate, complex recovery process, inability to test.

RPO - Recovery Point Objective - how old can data be that is recovered
RTO - Recovery Time Objective - how long until back online

Hot site - ready in minutes/hours
Warm site - ready in days
Cold site - several days to bring online

SRM supports several storage vendors.

Failover - switching operations from primary site to recovery site.
Failback - switch back from recovery site to primary site - days to months to failback.

DRP - process, policies and procedures for recovery.  DR focused on technology.  DRP are plans.  Exact step by step procedure to bring systems online, keep personnel safe, protect assets, switch systems to remote site.  Includes network config, how to verify failover.

Non virtual - install OS, apps, drivers, restore data
Virtual - install hypervisor, mount snapshots/replicated luns, power on VMs

If DRP is not tested, you dont have a DRP - testing reveals oversights.

Test app data is protected, not enough time for documentation for configs etc and up to date.

Design DR in a modular fashion, test small parts before full test.  Tests should minimize disruption to production.

Once passes test, needs to be tested regularly.

Post disaster:  How to run at recovery site, less capacity, may be inconvenient for staff, plan for temporary housing.

Management of company questions for managers - shut down certain apps, when to failback = BCP.

DRP - plan/procedures during chaos of disaster on safeguarding assets and personnel and is procedure oriented to get systems online.

BCP - process of keeping company running, day to day ops at recovery site.  BCP for IT is different than Finance.  Each department should have a BCP.

BCP Address 3 things:
- Run ops at recovery site
- Issues
- Failback
DR/BC is not a product, no single product or group of product can give instant DR/BC

SRM helps, but needs other product and technology but needs planning.

DRP relies on storage technology, backups need to be offsite, replication has to be timely (consider which LUNs replicated), not all files need to be replicated (dont replicate OS, Swap, temp files).  Make library of ISOs, apps.

Good backup for small scale outages.

<strong>DRP - 11 Step Process:</strong>

- Enable management buy in - management must agree (CEO, CFO, CTO) its required and funded.  Management driven.  Ongoing significant expense.  Upper level management must allow staff time for testing.
- Business impact analysis -
<p dir="ltr">- Identify key assets (blueprints, IP, equipment, data centers, apps, data) and business functions, mapp functions to assets, identify interdependencies.</p>
<p dir="ltr">- Determination of loss criteria - what if you lose asset X, or is degraded.</p>
<p dir="ltr">- Max tolerable downtime for assets - assign value to assets based on loss criteria.  If down longer than MTD significant loss of business.</p>
<p dir="ltr">- Critical, minutes, Urgent 24 hrs, Important 72 hrs, Normal 7-14 days, Non-essential 30 days</p>
- Define RPO - Industry standard measurement, point in time to be recovered, amount of data loss.
- Define RTO - Industry standard measurement, how long can be down, includes fault detection and bringing app back online.
- Risk assessment - What are your risks - location based problems such as earthquakes, tornados.  Manmade problems - leak, auto accident.  Can't protect against all, determine likelihood.
- Examine regulatory compliance - Some laws may require specific technology, RPO, RTO.  Check legal requirements.
- Develop DRPs - Create outlines using above info, what has to come online first including infrascuture, what order for all systems, not critical / not in DRP, does it need to be in BCP?
- Design DR systems - Select remote recovery sites, dedicated or non-dedicated, hot-warm-cold?, storage and replication tech, WAN links, communication for operations (phones, mobile).
- Create run books - specific set of procedures, detailed, step by step, app specific.  Rebuild system from OS, restore accounts, create infrastructure settings (AD, LDAP, VLAN), reload software, config software, restore data.  Site specific.  Run book for each asset, order runbook based on when systems need to be brought online.  Hard to create/maintain, capture config changes.
- Develop BCPs - What to do when DRP is finished, now operated business.  What problems - access, less resources, remote access, physical problems (desks, phones, direct dial), plan for operations at remote site (backups, accounting).  Plan for failback - storage replication back.  Need failback procedures.
- Test DRPs and BCPs - You must test, problems will be found.