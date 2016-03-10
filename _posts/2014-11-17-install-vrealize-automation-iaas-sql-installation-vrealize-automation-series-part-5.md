---
ID: 3021
post_title: 'Install vRealize Automation IaaS SQL 2014 Installation &#8211; vRealize Automation Series Part 5'
author: Jonathan Frappier
post_date: 2014-11-17 08:00:26
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/install-vrealize-automation-iaas-sql-installation-vrealize-automation-series-part-5/
published: true
dsq_thread_id:
  - "3233744264"
---
[display-posts category="vRA Home Lab" display-posts posts_per_page="15"]

Almost time to install the IaaS components, but we still need a SQL server so lets get this party started, if you are<a title="How to install Microsoft SQL Server 2012" href="http://www.virtxpert.com/how-to-install-microsoft-sql-server-2012/"> installing SQL2012</a> you can check out my older post, in this post I will be installing 2014 with a bit less detail on selection choices.
<ul>
	<li>Navigate to your download location of SQL and launch the installer</li>
	<li>Click OK to allow the installer to extract the files to the requested location, the SQL Server Installation Center will launch</li>
	<li>Click on New SQL Server stand-alone installation</li>
	<li>Accept the license terms and click Next</li>
	<li>I am going to skip the updates here for the sake of time, so leave the update box unchecked and click Next</li>
	<li>On the Feature Selection screen I am only keeping Database Engine and sub components and Management Tools - Basic and Complete in the default directory</li>
	<li>On the Instance configuration select Default and click next</li>
	<li>On the Server Configuration page change SQL Server Browser to Automatic and click Next</li>
	<li>On the Database Engine Configuration page change to Mixed Mode and set the SA password</li>
	<li>On the Specify SQL Server administrators section add svc_vra_iaas (we can remove this user as a SQL admin after the installation of the IaaS components), click Next to proceed with the installation</li>
	<li>Once finished, click the Close button and close the Installation Center screen</li>
</ul>
Before we move on to installing the IaaS components, lets log into SQL and make sure everything is as we want
<ul>
	<li>Open the Start menu and type Management Studio</li>
	<li>Log in with with Windows Authentication</li>
	<li>Expand Security &gt;&gt; Logins</li>
	<li>Confirm VXPRT\svc_vra_iaas is listed, right click on that user and select Properties</li>
	<li>Click on Server Roles and ensure sysadmin is selected</li>
</ul>
&nbsp;

[caption id="attachment_3027" align="aligncenter" width="712"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/sql-svc_vra_iaas-permission.png"><img class="size-full wp-image-3027" src="http://www.virtxpert.com/wp-content/uploads/2014/11/sql-svc_vra_iaas-permission.png" alt="SQL Server sysadmin permission for vCAC / vRA Service account" width="712" height="641" /></a> SQL Server sysadmin permission for vCAC / vRA Service account[/caption]
<ul>
	<li>Close Management Studio</li>
	<li>Open the Start menu and type SQL Server Configuration Manager</li>
	<li>Expand SQL Server network Configuration</li>
	<li>Right click on TCP/IP and select enable; click OK when prompted</li>
	<li>Click on SQL Server Services</li>
	<li>Right click on SQL Server (MSSQLSERVER) and select Restart</li>
	<li>On the Start menu and type Services</li>
	<li>Ensure Distributed Transaction Coordinator is set for Automatic or Automatic (Delayed Start)</li>
	<li>Close Services</li>
</ul>
With SQL installed and our user account having sysadmin permission on the SQL server, its time to install the IaaS components!  Log out of the IaaS server and we'll pick this up in the next post.