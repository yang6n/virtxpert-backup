---
ID: 2087
post_title: 'Design considerations for deploying the vCenter Server Appliance #VCSA'
author: Jonathan Frappier
post_date: 2014-03-26 10:59:21
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/design-considerations-deploying-vcenter-server-appliance-vcsa/
published: true
dsq_thread_id:
  - "2515382667"
---
The vCenter Server Appliance (VCSA) is a hardened appliance providing a stream lined deployment option for installing vCenter.  As of vSphere 5.5, the VCSA supports up to 100 hosts or 3000 VMs with the built in PostgreSQL database.  With an external Oracle database, you can support 1000 hosts or 10000 VMs (via <a href="http://www.vmware.com/pdf/vsphere5/r55/vsphere-55-configuration-maximums.pdf" target="_blank">vSphere 5.5 Configuration Maximums, Section 7</a>) however there are some key design considerations when deciding on using the VCSA versus installing vCenter on Windows.

<strong>Licensing</strong>

While the VCSA is deployed as a Linux based appliance, vCenter still needs to be licensed.  If you are deploying multiple instances of the VCSA, multiple vCenter licenses will be required.  Additional licensing may be required for other supporting infrastructure such as monitoring and backups.

<strong>Data Center Sizing</strong>

As previously mentioned, the VCSA supports up to 100 hosts or 3000 VMs with the built in PostgreSQL database.  Plan for appropriate growth based on business requirements to ensure you will not grow beyond the maximum supported configuration.  Additionally, you may chose to license and install multiple instances of vCenter to stay within the supported configuration maximums or for hard separation of resources (for example QA VCSA and DEV VCSA).

Some overhead should be left to support unplanned growth.

<strong>VMware Update Manager (VUM)</strong>

VMware Update Manager (VUM) is a Windows 64-bit only application used to install updates to to the vSphere environment.  Since the VCSA is a Linux based operating system, VUM could not be installed on the same machine as vCenter (though its generally recommended to separate these anyways).  VUM also requires either Microsoft SQL or Oracle, it cannot use share the built in PostgreSQL database in the VCSA.  Separate Windows and SQL or Oracle licensing, backup and monitoring software needs to be considered to support VUM.

<strong>Linked Mode</strong>

Linked Mode allows you to join multiple, separate vCenter instances together to allow for management of each vCenter.  Linked Mode is not supported when using the VCSA.

<strong>Supporting Tools</strong>

There are some common tools provided from VMware that will not work on the VCSA which include PowerCLI and vCLI.  You can install PowerCLI and vCLI on a separate Windows based computer.  Additionally, you could install the vSphere Management Appliance (vMA) to provide vCLI functionality.  vCenter Orchestrator which can install with vCenter on Windows is not bundled with the VCSA.  vCenter Orchestrator can be installed on a separate Windows based computer or by downloading the vCO appliance which, similar to the VCSA, is a hardened Linux based appliance.  Considerations must be made for these additional servers such as operating system, backup and/or monitoring licenses and support procedures.

<strong>Operating System Support</strong>

Many organizations rely on Microsoft Windows and as such, the skills of the internal support group may focus on Windows skill sets.  The VCSA is a hardened Linux based appliance, some additional training may be required for your support staff to troubleshoot common issues such as networking, routing or application issues.

<strong>Networking</strong>

The VCSA only supports IPv4.  Organizations who have deployed IPv6 only will not be able to use the VCSA.

<strong>Database Support</strong>

As of vSphere 5.5 Update 1, the VCSA supports only the built in PostgreSQL database, or an external Oracle database.  There is currently no support for Microsoft SQL Server or MySQL.  Organizations who do not have expertise in PostgreSQL or Oracle need to determine if they are capable of learning and supporting one of these two platforms.  Additionally, Oracle will add additional license costs to this deployment scenario.

<strong>Backup Support</strong>

Backup software should be evaluated to ensure it supports backup and recovery of virtual machines directly to ESXi hosts without an operational vCenter.  If the backup software currently in use requires vCenter, you may have difficulty recovering the VCSA should there be any problems which prevents vCenter from running.  Additionally, a processes should be implemented to backup and restore the supporting database platform, either PostgreSQL or Oracle.  The built in PostgreSQL database provides the normal tools to perform and schedule database dumps.  Test backup and recovery of the database to a test instance of the VCSA to ensure you can recover.

<strong>Monitoring</strong>

Some monitoring tools require an agent be installed in the guest operating system.  Ensure that current monitoring tools will support the VCSA, either through an agent or monitoring via vCenter or SSH.

<strong>Summary</strong>

While the VCSA has been much improved in 5.5, organizations must understand these considerations before choosing to use the vCenter Server Appliance versus installing vCenter on Windows.

&nbsp;

&nbsp;