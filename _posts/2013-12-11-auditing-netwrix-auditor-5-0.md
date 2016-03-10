---
ID: 1653
post_title: >
  Auditing Active Directory with Netwrix
  Auditor 5.0
author: Jonathan Frappier
post_date: 2013-12-11 14:14:43
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/auditing-netwrix-auditor-5-0/
published: true
dsq_thread_id:
  - "2044244745"
---
I have walked into enough environments where there was no auditing in place to verify controls or policies were actually followed.  After finding and trying out <a href="http://www.netwrix.com/netwrix_auditor_supported_systems.html" target="_blank">Netwrix Auditor</a> I can't understand why.  The trial of Netwrix Auditor 5.0 was extremely easy which made getting started with auditing my lab environment for this POC very easy.  Netwrix Auditor comes with several modules to help you automate and monitor including:
<ul>
	<li>Active Directory and Group Policy</li>
	<li>Windows Server and the various applications such as IIS, Exchange, SQL and SharePoint you'd likely find as well as Event Log monitoring</li>
	<li>VMware</li>
	<li>EMC VNX, VNXe and Celerra CIFS share auditing</li>
	<li>Cisco network devices</li>
</ul>
Beyond what is already available today, they are developing a new <a href="http://www.netwrix.com/network_device_audit.html" target="_blank">Network Device Auditing</a> tool, currently in Beta.

In this post I am going to cover the configuration and use for Active Directory.  During the installation you should have a service account available so that Netwrix can connect to your Active Directory, SMTP IP address and, if you are not installing on a Domain Controller, Group Policy Management Console installed.  If you are coming over from some of the great<a href="http://www.netwrix.com/top_7_freeware_tools.html?source=productsmenu" target="_blank"> free tools</a> Netwrix offers, some of these steps may not be needed but I set this up on a clean server.
<ul>
	<li>You are first presented with a screen to select the modules you would like installed.  Because Netwrix licensing is based on the number of users, and most of these are useful to me I use the "Install All" option.</li>
</ul>
<p style="text-align: center;"><a href="http://www.virtxpert.com/wp-content/uploads/2013/12/netwrixinstall.jpg"><img class="aligncenter  wp-image-1654" alt="netwrixinstall" src="http://www.virtxpert.com/wp-content/uploads/2013/12/netwrixinstall.jpg" width="568" height="480" /></a></p>

<ul>
	<li>The remainder of the install is of the next, next finish variety.</li>
	<li>Before you get into using the software there are a few items you need to configure which they have done an excellent job at documenting which you can find in the <a href="http://www.netwrix.com/download/QuickStart/NetWrix_Active_Directory_Change_Reporter_Enterprise_Edition_Quick_Start_Guide.pdf" target="_blank">Netwrix Active Directory Quick Start Guide</a> found <a href="http://www.netwrix.com/download/QuickStart/NetWrix_Active_Directory_Change_Reporter_Enterprise_Edition_Quick_Start_Guide.pdf" target="_blank">here</a>.</li>
	<li>Launch Netwrix Auditor, click on Managed Objects, then Create New Managed Object.</li>
	<li>Select Domain and follow the wizard entering your service account, SMTP details and target systems in your environment.</li>
	<li>You'll be presented with an option to configure reports using SQL Express or an existing SQL instance.  Obviously this should fit your use case, maintenance etc.  For purposes of my POC I am skipping this for now.</li>
	<li>I am also skipping the use of agents for now, as this is strictly a POC but agents are used to collect data from each server.</li>
	<li>Select to have Netrwix change your AD and group policy audit settings so it can be logged properly.</li>
	<li>Select your change summary recipients</li>
	<li>Configure real time alert options such as changes to your Domain Admin group.  I selected all of these options as I want to see these type of changes in real time.</li>
	<li><em>*Here if you do not have the Group Policy Management Console installed you will received a prompt, but could continue.</em></li>
	<li><em></em>Next cover the Inactive Users feature which allows you to manage accounts not being used, I am curious as to how to views Service Accounts.  Once of my favorite features is its ability to delete old computer accounts after a certain time period.</li>
	<li>Another great feature is the Password Expiration Notifier, which as you might guess will let your users know their password will expire.  In the past I've had to manage this via ad-hoc scripts, but its built right into Netwrix!</li>
	<li>Now the wizard will finish the configuration.</li>
	<li>Expand Managed Objects select your domain and click on Run to perform an initial data collection.</li>
</ul>
Now that the install is finished up and initial collection finished, head over to your DC and make a few changes that correspond to the real time alerts you configured.  Within a few minutes you should have alerts on your changes.

<strong>Summary</strong>

In just a few minutes I was able to go from manually combing logs for changes to having an easily installed product (I didn't read any documentation on setting this up) which can monitor and alert me on critical Active Directory changes.  Whats even better, we have barely scratched the service of the capabilities on Netwrix Auditor, as I mentioned initially there are SAN/filer auditing capabilities, tools to notify users their passwords expire and VMware environment monitoring.
<p style="text-align: center;"></p>