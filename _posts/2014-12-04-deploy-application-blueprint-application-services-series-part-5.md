---
ID: 3191
post_title: 'Deploy an Application Blueprint &#8211; Application Services Series Part 5'
author: Jonathan Frappier
post_date: 2014-12-04 08:00:13
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/deploy-application-blueprint-application-services-series-part-5/
published: true
dsq_thread_id:
  - "3289861160"
---
[display-posts category="Application Services Lab" display-posts posts_per_page="15"]

In part 4 we published an application blueprint through Application Serivces, that is pretty awesome but we still really haven't done anything just yet.  I mean its all just about working but the real hard part is creating the application blueprints.  Just for fun, lets create a generic blueprint and run a deployment.  While logged into Application Services go to Applications and click on the green + (plus) button to create a new application.
<ul>
	<li>Name the application and select a business group, if you've followed along my various home lab series you would select StarWars here since it is the only business group we gave permission to in vRealize Automation.</li>
	<li>Click save, click Create Application Version then click Save</li>
	<li>Now you are able to create a blueprint; click Create Blueprint</li>
	<li>Drag the logical template to the design pane, again if you're following along with me this would be the CentOS 64 logical template</li>
</ul>
[caption id="attachment_3332" align="aligncenter" width="1679"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/12/apps-app-design.png"><img class="size-full wp-image-3332" src="http://www.virtxpert.com/wp-content/uploads/2014/12/apps-app-design.png" alt="VMware Application Services / Application Director application designer" width="1679" height="935" /></a> VMware Application Services / Application Director application designer[/caption]
<ul>
	<li>Now all this would do is create a virtual machine like you could do through vRealize Automation or vSphere; here however we also have several preconfigured services we can drag into our logical template to install applications.</li>
	<li>Let's do a typical single node web and database server</li>
	<li>Drag Apache, vFabric RabbitMQ and and vFabric Postgres into the logical template, it should look something like this:</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/12/apps-app-services-added.png"><img class="aligncenter size-full wp-image-3333" src="http://www.virtxpert.com/wp-content/uploads/2014/12/apps-app-services-added.png" alt="apps-app-services-added" width="372" height="364" /></a>Now one of the hardest parts about automating something is now all the dependencies.  In this scenario I happen to know a few things are missing, not because I am a genius but because I went through several iterations of this blueprint before getting it to work.  This, however also allows me to demo some other features of Application Services.  In my CentOS template, SELinux is enabled - now I could convert my template to a virtual machine, disable it, clean up the virtual machine machine again and convert it back to a template.  It's what I would have done not 6-8 months ago.  Now, however, I'll simply use the tools available to me, tools like Application Services or <a title="Ansible Playbooks – A more advanced example" href="http://www.virtxpert.com/ansible-playbooks-advanced-example/">Ansible</a> to put the virtual machine into the state I want it:
<ul>
	<li>From the Application Components page, drag two "script" items into the logical template</li>
	<li>Edit the first script by clicking on it; name it (no spaces), click on Actions, click "Click here to Edit," copy the following into the window and click the reboot checkbox</li>
</ul>
#!/bin/bash
# set SELinux disabled
cp /etc/selinux/config /etc/selinux/config.bak
sed -i s/SELINUX=permissive/SELINUX=disabled/g /etc/selinux/config
<ul>
	<li>SELinux will now be disabled upon reboot.</li>
	<li>We also have to tweak the EPEL install to allow it to pull data properly (seems to be a known issues right now).  Rather than letting the EPEL package install as part of the services we used earlier, we can also do that in a script and configure the options we need for it to work.</li>
	<li>Edit the 2nd script as you did before but copy the following into the window</li>
</ul>
#!/bin/bash
# install EPEL
yum -y install http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
sed -i "s/mirrorlist=https/mirrorlist=http/" /etc/yum.repos.d/epel.repo
<ul>
	<li>Click the OK button, you should now see something like this:</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/12/apps-blueprint-configd.png"><img class="aligncenter size-full wp-image-3334" src="http://www.virtxpert.com/wp-content/uploads/2014/12/apps-blueprint-configd.png" alt="apps-blueprint-configd" width="280" height="306" /></a>
<ul>
	<li>Now click the deploy button, name the deployment, and select the business group</li>
	<li>Click Map Details, ensure all details match what you have setup, and click Next</li>
	<li>Provide a name to your virtual machine and edit CPU and memory as needed (and to match your vRA blueprint limits) - click Next</li>
	<li>Review the deployment blueprint and click Next</li>
	<li>Click the deploy  button (you could also publish to vRA here as we did in part 4, but I'm just demonstrating the deployment)</li>
	<li>The deployment will start</li>
</ul>
Now at one point I wasn't sure it was working, I could see Application Services say it was working (system was under 80-90% load consistently) however I wanted to see what vSphere was doing.  As you an see in the two screenshots below, the virtual machines are being deployed as you might expect (they are from two different deployments so yes the dates are different)

[caption id="attachment_3194" align="aligncenter" width="1203"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/apps-clone-in-vsphere-web.png"><img class="size-full wp-image-3194" src="http://www.virtxpert.com/wp-content/uploads/2014/11/apps-clone-in-vsphere-web.png" alt="Application Services - virtual machined deployed via the web client" width="1203" height="116" /></a> Application Services - virtual machined deployed via the web client[/caption]

[caption id="attachment_3179" align="aligncenter" width="1023"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/apps-clone-in-vsphere-client.png"><img class="size-full wp-image-3179" src="http://www.virtxpert.com/wp-content/uploads/2014/11/apps-clone-in-vsphere-client.png" alt="VMware Application Services deployment viewed in vSphere Client" width="1023" height="76" /></a> VMware Application Services deployment viewed in vSphere Client[/caption]

In addition, you can zoom in on the Execution Plan pane to see what step the deployment is currently on

[caption id="attachment_3195" align="aligncenter" width="821"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/apps-provisioning.png"><img class="size-full wp-image-3195" src="http://www.virtxpert.com/wp-content/uploads/2014/11/apps-provisioning.png" alt="Application Services provisioning a virtual machine" width="821" height="373" /></a> Application Services provisioning a virtual machine[/caption]

This process took quite a while in my lab, but it I am pretty resource bound now.  Now, as I mentioned this is an iterative processes, good chance it may have failed in your environment, review errors and run the deployment again.  After working through any specific environment issues you should be able to successfully deploy the application components.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/12/apps-successful.png"><img class="aligncenter size-full wp-image-3335" src="http://www.virtxpert.com/wp-content/uploads/2014/12/apps-successful.png" alt="apps-successful" width="820" height="397" /></a>