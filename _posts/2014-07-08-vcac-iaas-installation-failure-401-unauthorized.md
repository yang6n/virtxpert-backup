---
ID: 2339
post_title: 'vCAC IaaS Installation Failure &#8211; 401 Unauthorized'
author: Jonathan Frappier
post_date: 2014-07-08 08:33:26
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vcac-iaas-installation-failure-401-unauthorized/
published: true
dsq_thread_id:
  - "2826923310"
---
There are quite a few good posts out there on vCloud Automation Center installations, many of which I have read several times over now however my installation of the vCAC IaaS components was not going according to plan.  I had started with our "gold" Windows Server 2012 template, this template was fully patched so after cloning it I promptly removed the .NET 4.5.1 patch (aka KB 2881468) but I was still running into problems.

I had added the necessary Windows features in order to properly run <a href="https://twitter.com/vTagion" target="_blank">Brian Graf's</a> (@vTagion) IaaS preparation script and it ran without error, in addition I passed all of the vCAC IaaS component installer checks so I thought I was in good shape.  After a few minutes, just after the database was created and populated my installation failed, during the "Registering solution user in the VA..." stage.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/07/vcac-iaas-failure.png"><img class="aligncenter size-full wp-image-2340" src="http://www.virtxpert.com/wp-content/uploads/2014/07/vcac-iaas-failure.png" alt="vcac-iaas-failure" width="792" height="593" /></a>

&nbsp;

The vCAC installer was kind enough to tell me about the failure and asked me if I wanted to open the logs, which clearly I did.  The error was a bit odd, it was receiving a 401 or unauthorized error as you can see here:

<a href="http://www.virtxpert.com/wp-content/uploads/2014/07/vcac-iaas-error-log.png"><img class="aligncenter  wp-image-2341" src="http://www.virtxpert.com/wp-content/uploads/2014/07/vcac-iaas-error-log.png" alt="vcac-iaas-error-log" width="936" height="667" /></a>

&nbsp;

One problem with the logs, however, was it was obfuscating the URL, username and password it was actually trying to connect to so I wasn't sure if it was ehc-pod2-vcac01 or ehc-pod2-vcac02 (maybe I should my naming scheme).  I started with the assumption that the 401 must be coming from my Windows Server 2012 IIS instance based on the logs and that the vCAC appliance has little to configure beyond the deployment so I was fairly certain it was not Apache (or whatever it runs...I'm on vacation and not checking right now).  The only piece that made me wonder if my assumption was right was that the vCAC IaaS installer was successfully binding port 443 to the default website as well as adding the virtual directory and app pool to IIS.

To make sure there wasn't some problem with the template, I built a vanilla Windows Server 2012 virtual machine, added the features, ran the script, passed the prereq check but it failed again.  This new VM had no patches so I was confident there was another problem.

Next, I manually reviewed all of the role and feature requirements (...actually next I complained on Twitter :) and when I was sure everything was setup properly I started looking through IIS settings.  I ran through a couple more installs with the same result before coming across this security setting which can be found by clicking on the Default Website and clicking on Basic Settings.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/07/IIS.png"><img class="aligncenter size-full wp-image-2342" src="http://www.virtxpert.com/wp-content/uploads/2014/07/IIS.png" alt="IIS" width="529" height="288" /></a>

&nbsp;

<a href="http://www.virtxpert.com/wp-content/uploads/2014/07/iis-basic-settings.png"><img class="aligncenter size-full wp-image-2343" src="http://www.virtxpert.com/wp-content/uploads/2014/07/iis-basic-settings.png" alt="iis-basic-settings" width="609" height="350" /></a>

&nbsp;

The default value was actually set to use Application user (pass-through authentication).  When I clicked the test settings button pictured above, the Application User was not able to access the physical path to the website folder (C:\Inetpub\WWWRoot)

<a href="http://www.virtxpert.com/wp-content/uploads/2014/07/iis-app-passthrough.png"><img class="aligncenter size-full wp-image-2344" src="http://www.virtxpert.com/wp-content/uploads/2014/07/iis-app-passthrough.png" alt="iis-app-passthrough" width="440" height="225" /></a>

With nothing left to lose, I change this to the Active Directory user object I was using to run the vCAC services, restarted IIS and then this happened

<a href="http://www.virtxpert.com/wp-content/uploads/2014/07/iaas-install-success.png"><img class="aligncenter size-full wp-image-2345" src="http://www.virtxpert.com/wp-content/uploads/2014/07/iaas-install-success.png" alt="iaas-install-success" width="795" height="594" /></a>

&nbsp;

That was about 10PM on the 4th of July...which was thankfully a complete washout in Massachusetts so I wasn't missing any festivities, the next day I left on vacation and haven't had time to research it much beyond that.  I have however re-read a couple of install posts as well as the vCAC documentation and see no mention of changing this setting.  If I missed it shame on me, but if you are getting 401 unauthorized messages during the Registering Solution User in the VA step try this work around.

&nbsp;