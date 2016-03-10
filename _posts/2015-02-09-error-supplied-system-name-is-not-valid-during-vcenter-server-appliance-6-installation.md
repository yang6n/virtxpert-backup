---
ID: 3528
post_title: 'Error: Supplied System Name is not valid during vCenter Server Appliance 6 installation'
author: Jonathan Frappier
post_date: 2015-02-09 10:00:26
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/error-supplied-system-name-is-not-valid-during-vcenter-server-appliance-6-installation/
published: true
dsq_thread_id:
  - "3499619221"
---
During the installation of of the VMware vCenter Server Appliance (VCSA) 6.0 or the Platform Services Controller (PSC) Appliance 6.0, you receive the following message:

Firstboot script execution Error.

And/or

The supplied System Name [name] is not valid

VMware vCenter Server Appliance (VCSA) and Platform Services Controller (PSC) error during installation - supplied system name is not valid

[caption id="attachment_3529" align="aligncenter" width="965"]<a href="http://www.virtxpert.com/wp-content/uploads/2015/02/vmware-vcsa-psc-appliance-6-error-system-name-not-valid.png"><img class="size-full wp-image-3529" src="http://www.virtxpert.com/wp-content/uploads/2015/02/vmware-vcsa-psc-appliance-6-error-system-name-not-valid.png" alt="VMware vCenter Server Appliance (VCSA) and Platform Services Controller (PSC) error during installation - supplied system name is not valid" width="965" height="615" /></a> VMware vCenter Server Appliance (VCSA) and Platform Services Controller (PSC) error during installation - supplied system name is not valid[/caption]

Additionally, logs found at %USERPROFILE%\AppData\Roaming\VMware\vSphere\vcsa\sessions\session_####\logs do not provide additional details, only

2015-02-06 22:41:09.330738 Progress Controller: [VCSA ERROR] - First Boot error

This problem is likely due to incorrect DNS configuration, either in the DNS server IP address provided during the VCSA or PSC installation or there is no matching DNS record.

Verify that both forward and reverse DNS lookup zones exist and re-run the installation, validating that DNS is working. Below is an example of running nslookup FQDN. The first when the record doesn't exist, the 2nd after it has been added. Ensure you resolve the expected IP address from NSLOOKUP and re-run the installer.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/02/dns.png"><img class="aligncenter size-full wp-image-3530" src="http://www.virtxpert.com/wp-content/uploads/2015/02/dns.png" alt="dns" width="633" height="270" /></a>

&nbsp;