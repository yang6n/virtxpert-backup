---
ID: 1372
post_title: Getting Started with Embotics vCommander
author: Jonathan Frappier
post_date: 2013-09-12 09:41:09
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/getting-started-embotics-vcommander/
published: true
dsq_thread_id:
  - "1752185117"
---
I finally had the time to sit down and try out <a href="http://www.embotics.com/software/" target="_blank">Embotics vCommander</a>, which claims to be an easy to use "Cloud Management Platform" that requires no training to get up and running (we'll see as I am writing this post as of my first login to vCommander).  The setup process, for purposes of a demo/test environment is straight forward.  The only gotcha that came across was entering the service account user, if your service account user is a local user, but your machine is joined to a domain, you will need to enter the computer name in the domain field.  My lab machine is joined to a domain but didn't want to add test accounts to my AD so maybe you wouldn't run into this...but in case you did there it is.

During the registration process you should receive a 30-day license key and login and password for the software, I didn't so I emailed sales@embotics.com and they got back to me promptly with the key - bad impression on not getting the email, followed by a good impression for quick follow-up and a non-pushy sales person; for those keeping score at home that's a +1 to Embotics so far.

Once you are logged in, you are presented with several tasks to configure vCommander (honestly I am not sure why more software vendors don't do this)
<p style="text-align: center;"><a href="http://www.virtxpert.com/wp-content/uploads/2013/09/emboticssetup.png"><img class="aligncenter  wp-image-1373" alt="emboticssetup" src="http://www.virtxpert.com/wp-content/uploads/2013/09/emboticssetup.png" width="493" height="339" /></a></p>
<p style="text-align: left;">Following the steps laid out on the screen works as expected, and I was able to see the datacenter/vCenter I added being added to vCommander's inventory, which when finished appeared under the Views menu.</p>
<p style="text-align: center;"><a href="http://www.virtxpert.com/wp-content/uploads/2013/09/emboticsvcenteradd.png"><img class="aligncenter  wp-image-1375" alt="emboticsvcenteradd" src="http://www.virtxpert.com/wp-content/uploads/2013/09/emboticsvcenteradd.png" width="566" height="258" /></a></p>
<p style="text-align: left;">As I am doing only high level evaluations right now, the core features, at least to me, of the product appear under their 'solve' menu which presents several tasks which vCommander can help you automate such as the ability to see changes to a VM over the last 7 days (This unfortunately didn't work for me because my lab was just recently built, would be nice to still show what it was able to scan for versus throwing an error, I'll test that feature out again next week to see if it worked).  It also provides a useful dashboard for displaying VM and host resource utilization (CPU and Memory only) to help you right size your VMs or identify hosts that may be highly utilized.  For example, there is a predefined search to identify VM's with idle CPU which showed me several VM's that had multiple vCPU's assigned but were not being utilized; this could help in identifying VM's that you could reconfigure to use less resources (thus making more resources available and likely improve the VM performance).</p>
<p style="text-align: left;">The biggest reason, however, I started to finally look at vCommander was for the self service portal which allows your teams to request VMs without the need for either you to do it manually, or for other teams to have access directly to vCenter.  By accessing the Self Service section, I was able to add a portal user, assign it to a portal role (I used the built in developer role but you can create your own) and then configured the Service Portal.  Similar to the setup when I first logged in, this was all very clearly laid out on the main 'solve' screen.  Once you configure your roles, users and portals you then have to configure the types of service requests available (this was only very obvious as opposed to ridiculously obvious on the self service setup screen, if you logged into the portal you would quickly see there is nothing you can request).</p>
<p style="text-align: left;">When you click on Configure Service requests, you are taken to another screen with several steps laid out to make it clear as to what you need to do in order to configure these for your portal.  Again, follow the wizard and it is pretty clear on all the steps you need to perform.  When adding entries to the service catalog, the wizard suggested I could add VMs and templates, however none of my VMs appeared until I converted them to templates.  I was surprised to see that it would work off an existing VM, so I wasn't surprised when that didn't seem to work so make sure you have templates available.  For lab purposes this should work fine, however if you're deploying this for production use you will want to configure your setting for chargebacks as my 1vCPU/512MB VM had a cost of $260K (Updated, apparently I gave the VM/Template 512GB of RAM, not 512MB!)!</p>
<p style="text-align: left;">Since this is getting a bit long, I'll wrap up with by configuring the Approval Workflow which allows you to pass scripts and decide whether to automatically process the request and a Completion Workflow which allows you to define after the deployment which allows you to power on the VM, set VM expiration times or process more scripts (hopefully to pass configuration settings into the VM such as PoSH scripts for adding roles or basic commands like YUM in linux to add certain packages - look for a future blog post on this).</p>
<p style="text-align: left;">So, if Embotics is correct, and I don't need any training I should be able to log in as my test user, request my VM and have it deployed....so here it goes!</p>

<ul>
	<li>Logged into the self service portal</li>
	<li>Clicked new request</li>
	<li>Added the VM to the request</li>
	<li>And clicked submit...</li>
</ul>
All that worked, however I received an error in the admin panel that the managed system was not suitable for for automatic deployments (this was probably because my VM template had 512GB assigned, I'll get that fixed, retest and update this post with the results).  Via the admin panel, I am able to see the request, clicked deploy and followed the wizard - now I can see the the deployment is in progress in both the admin panel and self service portal as well as in vCenter.

<strong>**Update 1:  In order for automated provisioning to work, you need to go to the Provisioning Configuration tab and add a destination.  Once I added this, my requests started processing automatically**</strong>

<strong>Conclusion</strong>

<strong></strong>The install was certainly very easy and the wizards/setup screens within the app were nicely laid out, though there could be a little refinement to the setup steps to walk through setting up charge back info.  However, overall, I think this is a very interesting product, and very easy to use.  From install to logging into the Self Service Portal and starting a VM deployment took less than an hour!