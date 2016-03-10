---
ID: 424
post_title: >
  Need servers in less than 2 minutes?
  Provisioning a server in the cloud with
  @ProfitBricks
author: Jonathan Frappier
post_date: 2013-02-18 08:07:43
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/need-servers-in-less-than-2-minutes-provisioning-a-server-in-the-cloud-with-profitbricks/
published: true
dsq_thread_id:
  - "1090498077"
---
For readers of this blog, you may recall <a href="http://virtxpert.com/profitbricks-interesting-offering-needs-a-bit-more-automation/" target="_blank">a post a few weeks ago about ProfitBricks</a>, I walked through their Data Center Design (DCD) tool and tried to provision a server.  While I noted in the first post I would prefer my account to be automatically enabled so I can quickly provision a server, they did follow-up and provision the account within a hour.  Now that my account has been provisioned, and I added the appropriate billing/credit card information so I can be billed for services it was time to get back to setting up a server to host this blog since it is horribly slow on GoDaddy.

Provisioning a server/data center in ProfitBricks cloud / infrastructure is quite easy, the one trick you may miss is adding and attaching storage to your server but that is actually quite easy if you are paying attention or read the aforementioned post.  So in just a few minutes, I can add a server, connect it to Infiniband storage and to the internet.
<p style="text-align: center;"><a href="http://www2.virtxpert.com/wp-content/uploads/2013/03/1.-dcd.jpg"><img class="aligncenter  wp-image-530" alt="1.-dcd" src="http://www2.virtxpert.com/wp-content/uploads/2013/03/1.-dcd.jpg" width="703" height="400" /></a></p>
Now its time to provision, I clicked the provision data center button in the DCD tool and it started to create my server.
<p style="text-align: center;"><a href="http://www2.virtxpert.com/wp-content/uploads/2013/03/2.-provisioning-status-730a.jpg"><img class="aligncenter  wp-image-531" alt="2.-provisioning-status-730a" src="http://www2.virtxpert.com/wp-content/uploads/2013/03/2.-provisioning-status-730a.jpg" width="255" height="263" /></a></p>
I clicked the button at 7:30AM, and while not a complex setup, it completed in less than 2 minutes!  So with a fully activated account, you can have a server up and running with an OS in less than 5 minutes!

<a href="http://www2.virtxpert.com/wp-content/uploads/2013/03/3.-provisioned-732a.jpg"><img class="aligncenter size-full wp-image-532" alt="3.-provisioned-732a" src="http://www2.virtxpert.com/wp-content/uploads/2013/03/3.-provisioned-732a.jpg" width="207" height="120" /></a>

One feature I am particularly fond of, the forced password change on their pre-configured OS images.  I received an email with my server IP, username and password and as soon as I SSH'd into my server I was forced to change the password.  Working with other hosting providers, this is not always the case and I can run on the default password provided.

<a href="http://www2.virtxpert.com/wp-content/uploads/2013/03/4.-forcepwchange.png"><img class="aligncenter size-full wp-image-533" alt="4.-forcepwchange" src="http://www2.virtxpert.com/wp-content/uploads/2013/03/4.-forcepwchange.png" width="560" height="180" /></a>

The next steps now are to A) dust of the linux command line dust and B) configure the server with the necessary tools so I can move virtxpert.com and compare speed and access to my current provider.

&nbsp;