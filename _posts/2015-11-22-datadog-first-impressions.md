---
ID: 4165
post_title: DataDog First Impressions
author: Jonathan Frappier
post_date: 2015-11-22 19:13:18
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/datadog-first-impressions/
published: true
dsq_thread_id:
  - "4342399738"
---
After a sad first experience with another "Software as a Service" monitoring vendor which I can't sign up and get access to without first talking to a sales person, and because they don't publish their pricing, I decided to give DataDog a try. DataDog is free for up to 5 hosts, sufficient maybe for very small SMBs or for a specific, small application instance or $15 per host billed annually (or $18 a month billed monthly). <a href="https://www.datadoghq.com/pricing/#" target="_blank">You can sign up for DataDog free or pro</a> on their website, but for enterprsie support you'll have to talk to the dreaded sales person.

Once you sign up, you will need to select the services you use (though this doesn't seem to relate to the agents available); for example there are options for AWS, Docker, Google Cloud Platform, and vSphere (via Windows vCenter Agent, so it appears no VCSA), as well as other common applications such as Apache, Tomcat, PagerDuty, Microsoft IIS, and MicrosoftSQL (props to the DataDog team for including Microsoft technologies - they aren't the cool hipster things to use but damn stable and underrated in today's startupie/devopsie world).

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/datadog.png"><img class="aligncenter size-full wp-image-4167" src="http://www.virtxpert.com/wp-content/uploads/2015/11/datadog.png" alt="datadog" width="917" height="573" /></a>

As you can see above, I have selected AWS, IIS, vSphere, and SQL since these are things I have access to in my lab. Once complete, select your agent, I'll start with Ubuntu since that is what my Ansible control machine is running on. Once selected, you will get a command to run to pull down the agent.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/agent-datadog.png"><img class="aligncenter size-full wp-image-4171" src="http://www.virtxpert.com/wp-content/uploads/2015/11/agent-datadog.png" alt="agent-datadog" width="927" height="331" /></a>

The command/directions provided will change based on your operating system, as you might expect. You will need admin/sudo access for the agent installation, which will proceed when you enter the command provided.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/datadog-install-ubuntu.png"><img class="aligncenter size-full wp-image-4172" src="http://www.virtxpert.com/wp-content/uploads/2015/11/datadog-install-ubuntu.png" alt="datadog-install-ubuntu" width="676" height="342" /></a>

The agent will complete and connect to DataDog.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/data-dog-starting.png"><img class="aligncenter size-full wp-image-4173" src="http://www.virtxpert.com/wp-content/uploads/2015/11/data-dog-starting.png" alt="data-dog-starting" width="646" height="265" /></a>

Once you have finished select OS types on the DataDog wizard, click next. You will see information collected by DataDog, right off the bat it shows that the machine I added has NTP issues; makes sense since I never setup NTP!

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/data-dog-alert.png"><img class="aligncenter size-full wp-image-4175" src="http://www.virtxpert.com/wp-content/uploads/2015/11/data-dog-alert.png" alt="data-dog-alert" width="1170" height="365" /></a>

In addition to Events (which you are looking at above), you can also see
<ul>
	<li>Dashboards, which you will need to create</li>
	<li>Infrastructure lists or maps</li>
	<li>List of triggered monitors, and the ability to create new monitors</li>
	<li>Integration for the various systems I listed earlier</li>
</ul>
Time to let the agent do some work, I'll check back in on DataDog in a day or so to see how its doing collecting information as well as look at how easy (or not) it is to create new monitors (currently a primary complaint with Nagios and Sensu).