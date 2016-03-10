---
ID: 2311
post_title: 'I was DevOps before it was cool &#8211; My Pets and Cattle story'
author: Jonathan Frappier
post_date: 2014-07-03 08:48:10
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/devops-cool-pets-cattle-story/
published: true
dsq_thread_id:
  - "2814689693"
---
<a href="http://www.virtxpert.com/wp-content/uploads/2014/07/devops.png"><img class="alignleft size-medium wp-image-2314" src="http://www.virtxpert.com/wp-content/uploads/2014/07/devops-270x300.png" alt="devops" width="270" height="300" /></a>Looking back over my career, I can see several scenarios where I was fortunate enough to have worked with a forward thinking team.  One such time I was working at a HR SaaS company in 2007, deployment times were in hours, migrations as well as backups were days. Our problem, nothing was standardized; some customers were on servers with one OS and one version of the software and others were on another server with a different OS and very few were configured the same way. Same with our database layer, some were on default instances, some on named instances, some with DB and log backups, some without and none of the DB dumps were in the same location.

After talking to the VP of IT and CTO we decided to start standardizing, a key step in my opinion in achieving ITaaS/Automation (those steps by the way 1. Understand business requirements, 2. Document business requirements, 3. Standardize by creating standard operating procedures from 1 and 2, 4. Automate and everything after that starts to fall into place).

We, IT and release engineering, which today might categorized as a DevOps culture, worked closely with the development team to identify application requirements and best practices.  Thanks to the people I worked with and the respect we had for one another we were able to work together to identify and document many changes that should (and ultimately were) beneficial to our operations.  We then started to manually apply those changes by following the SOPs we created during a data center migration. As physical servers were moved, we reconfigured the application so that everything was configured in exactly the same manner – application files were in the same spot, web and database server settings were exactly the same. Over the course of the data center migration, we validated these settings – fewer application errors as well as quicker response to alerts and application errors when they occurred. Life was starting to look good.

In addition to a more stable environment, that was easier to monitor and troubleshoot we also saw deployment times go to minutes instead of hours, and migrations in many cases to &lt; 1 hour from days. Another side effect from all of this, we were able to drastically decrease our backup window because we no longer had to account for non-standard systems; we knew exactly where everything was all the time – our multi-day full backups were now achieved in about 6 hours.

While doing this manually was working, it wasn't sustainable. Engineering then built tools that automated the configuration of the web servers as well as the application deployment. We added new tools to centralize automated processes that were spread across various batch files on various servers – we knew when they worked and when they failed and we could fix them with but one or two button clicks. This wasn't achieved overnight however, it was a working process conceived and supported across development, QA, IT and release engineering. We had to change the mindset of people – no more cowboys just “getting stuff done” – you did it our way, the same way, all the time and we were all better for it in the end.

When servers started to have problems, we didn’t spend hours troubleshooting them anymore, we spun up a new image, kicked off the installation procedures that were automated and our application could be back online in minutes.  The longest part of the process was copying files from point A to point B.  My VM’s were cattle years ago.

Life was good, the people I worked with were all unicorns – we weren't the smartest people in the world, or the most talented but we had pride in ourselves to get the job done, we cared about one another in a way, both personally and professionally I've never experienced since. We hung together even on holiday weekends when things weren’t going well all making sure our pieces were in place (I did es tag fam no longer get) so we could help the other get over hurdles even if they weren't our own (Igor, Jay, John, and so many more - I love you guys).

DevOps is more about people than it is about the tools you use, while we have tools today like Ansible and Docker that make achieving DevOps/ITaaS/Cloud...whatever you call it easier, you can't do it without people.

I was DevOps before it was cool…then we got sold (FWIW - the company that bought us was much larger, lots of money and swagger and their IT and release group couldn't touch our 6 person team)!