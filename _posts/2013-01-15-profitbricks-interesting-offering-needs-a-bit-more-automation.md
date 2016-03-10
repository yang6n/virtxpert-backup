---
ID: 349
post_title: 'ProfitBricks &#8211; Interesting offering, needs a bit more automation'
author: Jonathan Frappier
post_date: 2013-01-15 20:47:48
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/profitbricks-interesting-offering-needs-a-bit-more-automation/
published: true
jabber_published:
  - "1358300868"
publicize_reach:
  - 'a:2:{s:7:"twitter";a:1:{i:1983177;i:555;}s:2:"wp";a:1:{i:0;i:16;}}'
publicize_twitter_user:
  - jfrappier
email_notification:
  - "1358300870"
reddit:
  - 'a:2:{s:5:"count";i:0;s:4:"time";i:1359052850;}'
dsq_thread_id:
  - "1090476023"
---
<em>Disclaimer:  I had interviewed with ProfitBricks and think they are a very interesting company with a unique offering and very smart and passionate people, everyone I met passed the "Lunch Test".  This post is not meant to be either positive or negative or as any type of incentive, it is simply the first impression of their service as an end user/customer.</em>

<a href="https://www.profitbricks.com" target="_blank">ProfitBricks </a>is a start up in the Infrastructure as a Service (IaaS) / cloud provider market - competing head to head with AWS, Rackspace and the like.  Their key differentiators (based soley on their website) for me is <a href="http://en.wikipedia.org/wiki/InfiniBand" target="_blank">InfiniBand</a> and live upscaling for CPU cores and RAM for your VMs - the only provider in the industry to offer this.  They claim to have the first graphical design tool, but I think that award goes to GoGrid who offered a graphical tool as far back as 2006/2007 (but that is neither here nor their).  The ProfitBricks Data Center Designer (DCD) is very polished and easy to use, as it should be as it is also the crux of their offering as this is the tool you use to build out your virtual data center.

My use case for tonight was simple, a single web server configuration but could also see potential for DR scenarios since I can live scale my CPU cores and RAM, assuming I can install my hypervisor of choice as a VM within their DCD and use some replication technology to get my VMs replicating on a regular basis to my storage devices, but that article will be for a later date - tonight its boring old single web server.

<em></em><em>Note:  I emailed their support email address at 8:01PM EST because of the errors I was receiving using the DCD and received a response 17 minutes later.  I have a feeling Amazon might struggle to provide that type of response time.</em>

The DCD, however, is where I ran into my first problem.  I signed up for an account and immediately received my account verification email - par for the course in 2013 but they came through as expected.  Once I clicked the link to verify my account, I headed over to the DCD to build my data center.

<a href="http://jonathanfrappier.files.wordpress.com/2013/01/activated.jpg"><img class="aligncenter size-full wp-image-350" alt="activated" src="http://jonathanfrappier.files.wordpress.com/2013/01/activated.jpg" width="544" height="450" /></a>

Now based on the email above, I figured I was good to go.  The DCD was very intuitive to use, though I did have a little bit of a head start as I got to see it demoed by an SE during my interview.  One item I would have missed in my haste to get it setup was actually linking the components together (internet to server, server to storage) as you can see in the image below (not connected in the first image).

<a href="http://jonathanfrappier.files.wordpress.com/2013/01/nolinks.jpg"><img class="aligncenter size-medium wp-image-351" alt="nolinks" src="http://jonathanfrappier.files.wordpress.com/2013/01/nolinks.jpg?w=300" width="300" height="186" /></a>

<a href="http://jonathanfrappier.files.wordpress.com/2013/01/linked.jpg"><img class="aligncenter size-medium wp-image-352" alt="linked" src="http://jonathanfrappier.files.wordpress.com/2013/01/linked.jpg?w=300" width="300" height="164" /></a>

Once you see it done it makes all the sense in the world, at least it did to me.  Now my needs are pretty simple right now as I just need a server capable of hosting multiple websites and could have just as easily went to GoDaddy and upgrade my $3 a month account but that doesn't seem nearly as fun.  Once I finished my single server design I clicked saved and then tried to provision my data center - this is where I received my first error.

<a href="http://jonathanfrappier.files.wordpress.com/2013/01/provisionerror.jpg"><img class="aligncenter size-full wp-image-353" alt="provisionerror" src="http://jonathanfrappier.files.wordpress.com/2013/01/provisionerror.jpg" width="362" height="290" /></a>

Now, as we saw earlier in the article, I had successfully activated my account.  Figured it was a glitch, I was logged in when I activated it so maybe the DCD just needed a refresh so I logged off and back on, same error.  I emailed support (see troubleshooting 101) to find out what I was doing wrong.  I did get a response in 17 minutes, impressive to say the least.  The problem - my account isn't really activated until someone in sales activates it.... okay - I guess?  I can certainly see wanting an SE or sales person to get in touch with customers to make sure they are using the platform properly, but they are the very definition of "cloud" - I want it now, not in 12 hours, not even in 2 or 3 hours - now.   Cloud = instant, on-demand.  So for now I can't tell you any more about my experience, other than if I was a person in a garage coding the next great web-app I would have probably moved on to another hosting provider by now if I was told I had to wait 12 hours for sales.  Also, in fairness there is a phone number listed on the error so I might be able to call and have my account activated now but I am sticking to original expectation that this should be automated and available on-demand.

And William if you are reading this, I might suggest making the account activation message more clear that my account isn't really activated.  Maybe say your account has been verified, your personal contact will be in touch within N hours to finish activating your account.  Well, actually what I suggest is to make this truly on demand.

<em>Update 8:46PM - Sales activated my account.  45 minutes is not to bad, I had to wait about 15-20 minutes for my vCloud Beta account to be ready.  I wonder if the support person who quoted my 12 hours was mis-informed for someone recognized my name!</em>