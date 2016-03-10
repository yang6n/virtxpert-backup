---
ID: 4365
post_title: 'Getting to know PostgreSQL &#8211; Installation'
author: Jonathan Frappier
post_date: 2016-03-09 09:43:00
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/getting-know-postgresql/
published: true
dsq_thread_id:
  - "4647683205"
---
PostgreSQL, or as it is commonly referred to Postgres, is a free an open source relational database platform. There is also has a commercial version for those customers who wish to have support from which is available from EnterpriseDB. In this post, I will review basic installation options, since the first step of getting to know the product is installing it.

My goal with this series is to better understand the basics of supporting Postgres, for example to understand how it is configured and where configuration files are, where the data directories are located, and where log files are located.

The installation differs slightly from Microsoft SQL Server for example. With Microsoft SQL Server, you provide several configuration parameters during the installation process. With Postgres the installation will depend on your operating system and is typically just a single command:
<h3>Installing PostgreSQL on Ubuntu</h3>
<pre>sudo apt-get install postgres</pre>
<h3>Installing PostgreSQL on CentOS/RHEL</h3>
<pre>sudo yum install postgress</pre>
<h3>Installing PostgreSQL on Windows</h3>
<pre>choco install postgresql</pre>
<h3>Installing PostgreSQL on OSX/Mac</h3>
Download from <a href="http://postgresapp.com/" target="_blank">http://postgresapp.com/</a> and move to /Applications

Additionally, you can install from source by <a href="http://www.postgresql.org/docs/9.2/static/install-short.html" target="_blank">following the directions in the official documentation</a> or it is also available as a Docker container from <a href="https://hub.docker.com/_/postgres/" target="_blank">Docker Hub</a> (if you are working with containers). Since PostgreSQL is open source, you may also find other variants used in various appliances. For example, both the Unitrends UEB appliance, the vRealize Automation appliance, and VMware vCenter server appliance utilize it within their appliances.

In my next post, I will take a look at some of the configuration options. In the mean time, folks with a <a href="https://app.pluralsight.com/library/courses/postgresql-getting-started/table-of-contents" target="_blank">Pluralsight subscription can take a look at this course which is only ~ 2 hours</a>.

&nbsp;