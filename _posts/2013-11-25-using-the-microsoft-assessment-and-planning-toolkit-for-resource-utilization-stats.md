---
ID: 1568
post_title: >
  Using the Microsoft Assessment and
  Planning Toolkit for Resource
  Utilization Stats
author: Jonathan Frappier
post_date: 2013-11-25 09:59:18
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/using-the-microsoft-assessment-and-planning-toolkit-for-resource-utilization-stats/
published: true
dsq_thread_id:
  - "1991970826"
---
There are quite a few tools out there to collect resource utilization statistics about an environment, some may even have tools such as Nagios or SolarWinds already in place for everyday system monitoring.  What do you do when you need a small, lightweight tool to collect this information, and presumably don't have access to something like VMware Capacity Planner?  That is where the Microsoft Assessment and Planning Toolkit (MAP) comes in.

<strong>Introduction to MAP</strong>

MAP is a handy, lightweight tool for monitoring a large number of systems and collecting resource utilization statistics.  MAP 8.5 claims to support both Windows and Linux operating systems, however in my testing it was unable to determine CPU and Disk utilization statistics for Linux Operating Systems, specifically using CentOS 6.4 with the HAL package the <a href="http://social.technet.microsoft.com/wiki/contents/articles/1640.microsoft-assessment-and-planning-toolkit.aspx" target="_blank">Technet article</a> described.  This CentOS server was, however, a VM and I have not had a chance to try this on a bare metal installation.  At the very least, for larger Microsoft OS based environments, this could be a very useful tool for collecting key resource utilization statistics to start a virtualization project or just a get a better understanding about the needs of the environment for upgrade planning.

<strong>Installation</strong>

MAP does not ship with Windows so you will need to download it from Microsoft <a href=" http://www.microsoft.com/en-us/download/details.aspx?id=7826" target="_blank">here</a>, the only requirement is that .NET 4.0 or higher is installed.  The installation, in typical Microsoft fashion, is very straight forward.... Next, Next, Next, Next, Install type variety.  When MAP first loads, it will ask for a name for your inventory database, this is where it will store information collected.  MAP is using an embedded database but you could also connect it to an external database if you like.  You can name this anything you like, probably makes sense to be something useful to you that falls within your company standards.  You can see below I named my database something generic, but descriptive.

<a href="http://www.virtxpert.com/wp-content/uploads/2013/11/0464EN_01_04.jpg"><img class="aligncenter size-full wp-image-1570" alt="0464EN_01_04" src="http://www.virtxpert.com/wp-content/uploads/2013/11/0464EN_01_04.jpg" width="616" height="559" /></a>

&nbsp;

<strong>Using MAP</strong>

Once we have the database name in, use the 'Perform an Inventory' feature to, as you may have guessed, build an inventory of what we are using.  There are many pre-packaged scenarios but we will focus specifically on Windows Computers since the Linux/UNIX computers option doesnt seem to return much useful information.  Select Windows Computer option and click the Next button.  Here you will be asked how MAP should discover computers, there are a lot of options here, most even an entry level admin should be able to decipher so use what is best for your environment.  Once you are finished, MAP will proceed with the inventory.

Once the inventory is finished you will need to click on Server Virtualization, then click 'Collect performance data' so we can start to gather some useful resource utilization statistics about the environment.  Select the machines you wish to collect information on, the duration you wish to collect the information and click start.  If this is your first time using MAP, it may be worth your while to run this for a short period of time so you can understand the metrics collected and map that to what was happening in your environment.  By default MAP will run for an hour, though you can configure this for any time period you like.

<strong>Reviewing Resource Utilization Statistics</strong>

Once completed, you could run the results through one of the Microsoft-centric Wizards, for example if you were moving to Azure.  To look at the raw output, click on Environment in the left navigation pane where you should see the results of your inventory and performance metric collections.
<p style="text-align: center;"><a href="http://www.virtxpert.com/wp-content/uploads/2013/11/map.jpg"><img class="aligncenter  wp-image-1572" alt="map" src="http://www.virtxpert.com/wp-content/uploads/2013/11/map.jpg" width="637" height="511" /></a></p>
<p style="text-align: center;"></p>
<p style="text-align: left;">Click on the Performance Metrics card, then click the Performance Metrics Report button on the top right.  It will generate the report and save it to c:\users\useraccountrunningmap\MAP for you to view the report.</p>
<p style="text-align: left;"><strong>Summary</strong></p>
<p style="text-align: left;">MAP is a very useful, easy to install and lightweight tool and helps automate collecting the type of resource utilization statistics you are likely to be interested in for a virtualization project.</p>