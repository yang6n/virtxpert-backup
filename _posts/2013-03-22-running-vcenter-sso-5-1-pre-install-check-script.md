---
ID: 611
post_title: >
  Running vCenter SSO 5.1 Pre-Install
  Check Script
author: Jonathan Frappier
post_date: 2013-03-22 18:13:42
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/running-vcenter-sso-5-1-pre-install-check-script/
published: true
dsq_thread_id:
  - "1157388845"
---
Alan Renouf recently released a "fling" called the vCenter 5.1 Pre-Install Check which can help you make sure you configuration is correct for vCenter SSO, from the fling page:
<blockquote>"helps customers validate their environment and assess if it is ready for a 5.1.x upgrade. The script checks against known misconfiguration and issues raised with VMware Support. This script checks the Windows Server and Active Directory configuration and provides an on screen report of known issues or configuration issues, the script also provides a text report which can help with further trouble shooting"</blockquote>
Since I am setting up a new lab environment to test VMware Horizon Workspace, I figured this would also be a good opportunity to test this fling.  As part of my my environment I installed a new Windows 2008 R2 Domain Controller, also running DNS and configured my reverse look-up zone (specifically called out as a requirement for Horizon).  Next, I installed another Windows 2008 R2 VM which I will use to install vCenter.  At this point, it is a vanilla Windows 2008 R2 installed fully patched.  Keep in mind the system requirements below, and don't forget to log into the domain versus local machine (always burns me):
<ul>
	<li>Windows 2003/ Windows 2008/2008 R2 on 64bit in a domain environment.</li>
	<li>.Net Framework 3.5.0 or above</li>
	<li>PowerShell 2.0 or above</li>
	<li>PowerShell must be able to run scripts (Execution Policy must be assigned correctly)</li>
	<li>PowerShell must be launched as Administrator</li>
	<li>Run in 64 Bit PowerShell (Do not run in PowerShell (x86))</li>
</ul>
I <a href="http://labs.vmware.com/flings/vcenter-5-1-pre-install-check-script">downloaded the Fling</a> on my new 2008 R2 VM which was joined to the lab domain.  I launched the PowerShell prompt (as administrator), set my execution policy to unrestricted (Set-ExecutionPolicy unrestricted since the ps1 file is not signed.) and ran PreCheckv2.ps1, selected R for run and the GUI for the script launched.  The box below should be changed if you are using for an upgrade versus a new install, click the 'Run Checks' button when you are ready to proceed.
<p style="text-align: center;"><a href="http://www.virtxpert.com/wp-content/uploads/2013/03/changedomain.jpg"><img class=" wp-image-612 aligncenter" alt="changedomain" src="http://www.virtxpert.com/wp-content/uploads/2013/03/changedomain.jpg" width="796" height="153" /></a></p>
<p style="text-align: left;">During my installation check, the script found issues with DNS which I needed to resolve.  One thing I really like is the link to the associated VMware Knowledge Base article on the particular issue.</p>
<p style="text-align: left;"><a href="http://www.virtxpert.com/wp-content/uploads/2013/03/dnsprobs.jpg"><img class="aligncenter size-full wp-image-613" alt="dnsprobs" src="http://www.virtxpert.com/wp-content/uploads/2013/03/dnsprobs.jpg" width="934" height="102" /></a></p>
<p style="text-align: left;">This is definitely a great tool that I will be using during deployments going forward.</p>