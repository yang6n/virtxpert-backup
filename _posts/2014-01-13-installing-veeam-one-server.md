---
ID: 1799
post_title: Installing Veeam ONE Server
author: Jonathan Frappier
post_date: 2014-01-13 14:21:54
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/installing-veeam-one-server/
published: true
dsq_thread_id:
  - "2117656970"
---
<em>**Note that this post was not paid for, reviewed by or in any other way altered by Veeam.  The opinions in this post are my own.  Veeam is a sponsor of virtxpert.com**</em>

In a previous post, I covered the installation of VMware vCenter Operations Manager (vCOPS) as I search for a good monitoring solution.  Since vCOPS and Veeam ONE come in both a free and paid version, I figured this would be a good comparison to vCOPS.  There a few requirements you can do to prepare for the install, or allow the install to configure these for you during the installation.
<ul>
	<li>You will need a service account for Veeam ONE</li>
	<li>The Visual C++ 2010 SP1 Redistributable package</li>
	<li>IIS with several components (see screenshot below)</li>
	<li>If you are using an external SQL database, the connection information for that database</li>
	<li>An account to connect to vCenter</li>
</ul>
You can download either Veeam ONE or Veeam ONE Free at <a href="http://www.veeam.com/downloads/" target="_blank">http://www.veeam.com/downloads/</a>.  It will download as an ISO which you can mount to your VM or extract the contents.  Once the CD mounts you will get the main spash screen.
<p style="text-align: center;"><a href="http://www.virtxpert.com/wp-content/uploads/2014/01/veeamon-splash2.jpg"><img class="aligncenter  wp-image-1803" alt="veeamon-splash2" src="http://www.virtxpert.com/wp-content/uploads/2014/01/veeamon-splash2.jpg" width="598" height="379" /></a></p>

<ul>
	<li>Click on Veeam ONE Server, if its not already installed, it will prompt you to install the Visual C++ 2010 Redistributable.  If you needed it, you will have to reboot here.</li>
	<li>Restart the installer after the reboot and click <span style="color: #3366ff;"><strong>Next</strong></span></li>
	<li>Accept the license agreement and click <strong><span style="color: #3366ff;">Next</span></strong></li>
	<li>Select the license key, or chose to install the FREE version.  Here I will enter my trial key and click <span style="color: #3366ff;"><strong>Next</strong></span></li>
	<li>Chose Typical or Advanced, Advanced allows you to chose whether to install the server and web GUI components, click <span style="color: #3366ff;"><strong>Next</strong></span></li>
	<li>The Veeam ONE setup will check for other application requirements, specifically IIS and its required components.  If the status is failed, you can click the "<span style="color: #3366ff;"><strong>install</strong></span>" button here to install these components.</li>
</ul>
<p style="text-align: center;"><a href="http://www.virtxpert.com/wp-content/uploads/2014/01/veeamone-iis-reqs.png"><img class="aligncenter  wp-image-1809" alt="veeamone-iis-reqs" src="http://www.virtxpert.com/wp-content/uploads/2014/01/veeamone-iis-reqs.png" width="398" height="361" /></a></p>

<ul>
	<li>Once the missing items are installed, you can click the <span style="color: #3366ff;"><strong>Next</strong></span> button, which was not available in the previous screenshot.</li>
	<li>Select the installation directory and click <strong><span style="color: #3366ff;">Next</span></strong></li>
	<li>Chose your SQL instance, either an existing instance or a new instance installed by Veeam, here I will use a new local instance of SQL.  Click <span style="color: #3366ff;"><strong>Next</strong></span></li>
	<li>Enter the website ports, or as I'd suggest keep the defaults and click <span style="color: #3366ff;"><strong>Next</strong></span></li>
	<li>Chose what type of infrastructure you are connecting to, either vCenter or Hyper-V (or skip until later).  Here I will select <span style="color: #3366ff;"><strong>VMware vCenter Server</strong></span></li>
	<li>Enter the account to connect to vCenter, I'd suggest a dedicated account and click Next</li>
	<li>If you are using Veeam Backup and Replication, or Veeam Enterprise manager, enter those credentials or click <span style="color: #3366ff;"><strong>Configure connection settings later</strong> </span>and click <span style="color: #3366ff;"><strong>Next</strong></span>, then <span style="color: #3366ff;"><strong>install</strong></span></li>
	<li>Here, the installation will proceed with the options you entered.  If you were using Veeam to install SQL Express, the install will take a few extra minutes.</li>
	<li>The installation will require you to log off (presumably because of how they do authentication) click yes to log off now, or no to do it later, I'd suggest doing it later so you can edit the Veeam ONE local groups and add users.</li>
</ul>
The installation created several local groups on the machine Veeam was installed on, Veeam ONE Administrators, Veeam ONE Dashboards and Veeam ONE Users, so that you can provide access to the application.  Assuming you installed as an administrator, you will probably want to add other users or groups so they can install and run the Veeam ONE Monitor Client.  Once added, now log off and log back in.

Now that you're back, you have 3 icons on your desktop - Veeam ONE Business View, Veeam ONE Monitor and Veeam ONE Reporter.  Launch Veeam ONE Monitor, make sure the application is launched as an account that was added to the Veeam One Users group.  Here you can configure SMTP and SNMP notifications if you choose.  Once done, you are dropped into the dashboard and can start navigating through you vSphere infrastructure to see any errors. One interesting item, compared to vCOPS; vCOPS found and alerted on a datastore that was almost full.  Veeam ONE reports all datastores as okay - there is about 60GB free but just goes to show a difference in interpretation between different products.  The Veeam ONE Business View is available as a website, so this can given out without the need to install the client.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/01/veeamone-dash.jpg"><img class="aligncenter size-large wp-image-1818" alt="veeamone-dash" src="http://www.virtxpert.com/wp-content/uploads/2014/01/veeamone-dash-1024x301.jpg" width="640" height="188" /></a>

<strong>Summary</strong> The installation of Veeam one was much easier than vCOPS, I felt there was a bit of fight in the vCOPS config but nothing outrageous.  The Veeam ONE interface is also very streamlined and, like vCOPS, I can drill down into specific areas of the infrastructure to see problems or error messages.  I do like the real time monitoring charts, for example I can see the MBps or write I/O for a particular datastore.  There are a few things missing in my opinion, I would prefer Veeam ONE was using a web interface rather than needing a client and add support for NFS datastores (I can't see datastore IO for NFS).  However, overall feel like this can be a useful tool, and slightly easier to use than vCOPS.