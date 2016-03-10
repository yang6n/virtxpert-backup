---
ID: 3895
post_title: >
  Installing Meat locally in VMware
  Workstation
author: Jonathan Frappier
post_date: 2015-07-27 08:00:28
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/installing-meat-locally-in-vmware-workstation/
published: true
dsq_thread_id:
  - "3975581089"
---
As I mentioned in my last post, Meat comes packaged as an OVA to easily deploy into VMware environments. The quickest path for testing for me was to install in VMware Workstation; simply click File &gt;&gt; Open and select the OVA. By default, it connects in bridged mode (e.g. on your network) however I run my lab behind the Workstation NAT so I made that change. Connect appropriately for your environment. Before you begin, add another virtual drive with at least 10GB of space.

Once the VM is powered on you should be prompted to connect to the IP address it received during boot via DHCP, or you have the option to configure networking via the console; both options shown here. Again, this will depend on your environment.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/07/mean3.png"><img class="aligncenter size-full wp-image-3896" src="http://www.virtxpert.com/wp-content/uploads/2015/07/mean3.png" alt="mean3" width="684" height="408" /></a>

When you navigate to the IP and port, in the case of Meat 8080, you'll be taken to the first step in the setup wizard.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/07/meat4.png"><img class="aligncenter size-full wp-image-3897" src="http://www.virtxpert.com/wp-content/uploads/2015/07/meat4.png" alt="meat4" width="665" height="267" /></a>

Start the installation, and accept the agreement. If you forgot to add additional space you will now be prompted to do so. Upload your license and the installation will begin.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/07/installation.png"><img class="aligncenter size-full wp-image-3898" src="http://www.virtxpert.com/wp-content/uploads/2015/07/installation.png" alt="installation" width="670" height="747" /></a>

Once done, you will be prompted to configure your workspace. In a workspace you can have a collection of different projects and users, permissions, groups and see activity feeds. For example, here is a workspace I created.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/07/workspace.png"><img class="aligncenter size-full wp-image-3900" src="http://www.virtxpert.com/wp-content/uploads/2015/07/workspace.png" alt="workspace" width="1674" height="875" /></a>

&nbsp;

As I would in GitHub, I can see the URLs to access the repository in my Git client via either HTTPS or SSH

<a href="http://www.virtxpert.com/wp-content/uploads/2015/07/details.png"><img class="aligncenter size-full wp-image-3901" src="http://www.virtxpert.com/wp-content/uploads/2015/07/details.png" alt="details" width="651" height="359" /></a>

I can also import from existing popular repositories such as Git, GitHub, or BitBucket which is useful for testing Meat out as you can bring your projects in that already exist.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/07/import.png"><img class="aligncenter size-full wp-image-3902" src="http://www.virtxpert.com/wp-content/uploads/2015/07/import.png" alt="import" width="820" height="440" /></a>

For example, here is my Ansible-Test-Playbooks repository from GitHub, imported into Meat. All I had to do was authorize Meat, and select the repository I wanted to import. It also supports readme files as you would be accustomed to in GitHub.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/07/imported.png"><img class="aligncenter size-full wp-image-3903" src="http://www.virtxpert.com/wp-content/uploads/2015/07/imported.png" alt="imported" width="784" height="581" /></a>

Not only did it import the repository, but a history of my commits as well!

<a href="http://www.virtxpert.com/wp-content/uploads/2015/07/import-commit-notes.png"><img class="aligncenter size-full wp-image-3905" src="http://www.virtxpert.com/wp-content/uploads/2015/07/import-commit-notes.png" alt="import-commit-notes" width="761" height="147" /></a>

As I mentioned in my previous post, I can edit files directly in Meat, and as I had hoped prompts me to commit those changes versus just by passing the typical <a href="http://www.virtxpert.com/on-the-second-day-of-commitmas-git-clone-git-add-git-commit-git-push/">commit/push process</a> those who use GitHub are familiar with. To boot, Meat automatically made notes of my changes, versus having to enter them in vim and then saving them before doing a git push.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/07/commits.png"><img class="aligncenter size-full wp-image-3904" src="http://www.virtxpert.com/wp-content/uploads/2015/07/commits.png" alt="commits" width="829" height="673" /></a>

You may also notice the reply box, this is a social aspect of Meat I hadn't mentioned. You can see a list of comments, adds, deletes, changes all from the activity stream as well. Here is my commit done via the Meat UI with a comment in the stream.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/07/activity.png"><img class="aligncenter size-full wp-image-3906" src="http://www.virtxpert.com/wp-content/uploads/2015/07/activity.png" alt="activity" width="820" height="420" /></a>

That's it for today, next I will be looking into Releases which is the ability to deploy code to servers directly from Meat.