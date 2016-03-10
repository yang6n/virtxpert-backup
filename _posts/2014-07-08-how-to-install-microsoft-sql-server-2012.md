---
ID: 2315
post_title: How to install Microsoft SQL Server 2012
author: Jonathan Frappier
post_date: 2014-07-08 09:17:38
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/how-to-install-microsoft-sql-server-2012/
published: true
dsq_thread_id:
  - "2827036152"
---
Why, because you may not be a SQL person, so here it is!

You've probably download SQL Server 2012 as a DVD ISO, move the ISO some place accessible by your server; maybe a datastore where you can mount the ISO or expanded so you can access the files directly on the server - I have mine save to the desktop of the server I am installing it on.
<ul>
	<li>Double click setup.exe, click the Yes button on the User Account Control dialog box</li>
	<li>Click on Installation</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/07/SQL-splash-screen.png"><img class="aligncenter wp-image-2318" src="http://www.virtxpert.com/wp-content/uploads/2014/07/SQL-splash-screen2.png" alt="SQL-splash-screen2" width="585" height="167" /></a>
<ul>
	<li> On the installation page, we will do a New SQL Server stand-alone installation.  If you were setting up a failover cluster or upgrading you could select those options, however we will not get into that here.</li>
	<li>The installation will check to ensure it can be installed, verifying you have administrator permissions, .NET, etc (click the image below to see the checks), if there are no errors click the OK button to continue.</li>
</ul>
<!--more-->

<a href="http://www.virtxpert.com/wp-content/uploads/2014/07/SQL-precheck-screen2.png"><img class="aligncenter wp-image-2320" src="http://www.virtxpert.com/wp-content/uploads/2014/07/SQL-precheck-screen.png" alt="SQL-precheck-screen" width="574" height="172" /></a>
<ul>
	<li>Next, enter your product key or select the Specify a free edition radio button which will allow you to install the full version in Evaluation mode or the free Express version and click the Next button</li>
	<li>Accept the license terms and click the Next button</li>
	<li>You can chose to check for updates, or not, for example your lab may be isolated.  Click the Next button.</li>
	<li>The installation of setup files will now start</li>
</ul>
<img class="aligncenter  wp-image-2322" src="http://www.virtxpert.com/wp-content/uploads/2014/07/sql-support-install.png" alt="sql-support-install" width="615" height="251" />
<ul>
	<li>The installer will then check several additional setup requirements, fix any warnings or errors.  For example if Windows Firewall is enabled you will get a warning to remind you to open ports.  I've opted to disable Windows Firewall for local network traffic between my servers.  Once you are set, click the Next button.</li>
	<li>Select which set of feature sets you wish to install, the default SQL Server Feature Installation will allow you to select the components you want in the next step, so click Next!</li>
	<li>At a minimum, select Database Engine and Management Tools - Complete.  You can chose to install others such as replication if you want to test those.  On this screen you also select the install directory.  In production cases I like to keep this on its own drive/LUN if possible though you may just install on the OS drive.</li>
	<li>A third set of installation verification will run, click the Next button.</li>
	<li>Now, you can chose to install a default instance or a named instance.  Named instances allow you to run separate SQL executables to really isoalte databases, for example in a multi-tenant environment where security requirements are very script and do not allow for database level security.  Choose Default instance and click the Next button.</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/07/SQL-instance-select.png"><img class="aligncenter  wp-image-2325" src="http://www.virtxpert.com/wp-content/uploads/2014/07/SQL-instance-select.png" alt="SQL-instance-select" width="635" height="475" /></a>
<ul>
	<li>The installer will verify you have adequate space on the destination drive, click the Next button.</li>
	<li>On the Server Configuration page you will define the accounts under which these services will run and whether they should start manually or automatically.  Make sure to change SQL Server Agent to start automatically.  There is also a Collation tab; certain applications require a specific Collation setting - verify which you need and select accordingly though this can be changed latter, click the Next button.</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/07/sql-services-start.png"><img class="aligncenter  wp-image-2327" src="http://www.virtxpert.com/wp-content/uploads/2014/07/sql-services-start.png" alt="sql-services-start" width="660" height="256" /></a>
<ul>
	<li>The Database Engine Configuration screen is one of the most important in my opinion.  On this screen you select your authentication mode - Windows or Mixed.  Many applications require Mixed Mode so the application can authenticate directly to the SQL server.  Understand your application requirements and select appropriately.  Another important item set on this page is Data Directories (not sure why this is "hidden" on its own tab), here you can define the location of your database and log files.  In production environments these typically are on separate LUNS to support the database workload.  Both of these can be changed later, but know you can set them here.</li>
	<li>Select Mixed Mode and enter a strong SA (the "System Administrator" account) password and click the Add Current User button to ensure the account you are installing as has permission to manage SQL.  If required, change the data directories then click the Next button.</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/07/SQL-mixed-complete.png"><img class="aligncenter  wp-image-2328" src="http://www.virtxpert.com/wp-content/uploads/2014/07/SQL-mixed-complete.png" alt="SQL-mixed-complete" width="646" height="482" /></a>
<ul>
	<li>Decide whether you want to enable error reporting and click the Next button.</li>
	<li>Yet another validation check, click Next if there are no errors.</li>
	<li>Finally, verify all of the settings you selected and click the Install button.</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/07/sql-ready-install.png"><img class="aligncenter  wp-image-2329" src="http://www.virtxpert.com/wp-content/uploads/2014/07/sql-ready-install.png" alt="sql-ready-install" width="635" height="476" /></a>
<ul>
	<li>Depending on the capabilities of your server, SQL will be ready in a few minutes...or in a lower powered lab it may be time to grab lunch.</li>
	<li>Once the install finishes, verify everything was successful and click the close button, you should  now be able to launch the SQL Server Management Studio and connect to your server.  You can log in using Windows authentication with the account you added during installation, or SQL Server authentication using the SA user and password set during installation.</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/07/sql-login.png"><img class="aligncenter  wp-image-2334" src="http://www.virtxpert.com/wp-content/uploads/2014/07/sql-login.png" alt="sql-login" width="322" height="243" /></a>

<a href="http://www.virtxpert.com/wp-content/uploads/2014/07/sql-mgmt-studio.png"><img class="aligncenter  wp-image-2335" src="http://www.virtxpert.com/wp-content/uploads/2014/07/sql-mgmt-studio.png" alt="sql-mgmt-studio" width="729" height="299" /></a>

One last item you might like to do is verify that TCP/IP is enabled, this is done by launching SQL Server Configuration Manager.  I believe this was changed in 2008, in 2005 the default was to leave TCP/IP disabled, because you know who needs network access to SQL services but I still like to check :)  Happy SQL'ing!

<a href="http://www.virtxpert.com/wp-content/uploads/2014/07/sql-config-manager.png"><img class="aligncenter size-full wp-image-2337" src="http://www.virtxpert.com/wp-content/uploads/2014/07/sql-config-manager.png" alt="sql-config-manager" width="486" height="268" /></a>