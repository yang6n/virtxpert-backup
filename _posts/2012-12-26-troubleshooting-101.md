---
ID: 310
post_title: Troubleshooting 101
author: Jonathan Frappier
post_date: 2012-12-26 08:11:29
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/troubleshooting-101/
published: true
jabber_published:
  - "1356527508"
tagazine-media:
  - 'a:7:{s:7:"primary";s:0:"";s:6:"images";a:0:{}s:6:"videos";a:0:{}s:11:"image_count";i:0;s:6:"author";s:7:"7110326";s:7:"blog_id";s:8:"38472741";s:9:"mod_stamp";s:19:"2012-12-26 13:11:48";}'
publicize_twitter_user:
  - jfrappier
email_notification:
  - "1356527510"
reddit:
  - 'a:2:{s:5:"count";i:0;s:4:"time";i:1357231399;}'
dsq_thread_id:
  - "1129257347"
---
Disclaimer - These are not all my ideas, simply a collection of ideas from people I have met over the year including some very smart folks from Softscape (former company), ICI and others.

When faced with a problem, error message, basically anything not working here are some tips to get you back quickly.
<ol>
	<li>Make a list.  Scott Lowe just presented on the ProfessionalVMware.com #vBrownBag (http://professionalvmware.com/?p=2931) and focused on the importance of tracking tasks so you are not bouncing back and forth and losing focus.  If nothing else, the below points might make a good list for you to walk through to ensure you are getting the right things done in a timely manner.</li>
	<li>Collect as much information you can about the problem.  Albert Einstein once said "If I had one hour to save the world, I would spend 55 minutes defining the problem and only five minutes finding the solution" and this should be a lesson for all of us in technology.  We need to understand the problem before we can solve it.  What is the operating system, patch level, software application and patch level, when did the problem start, what has changed since it started are all good data points to start with.</li>
	<li>Open a support ticket with the vendor.  This was a great bit of advice I received from Brad Maltz (<a href="https://twitter.com/bmaltz" target="_blank">@bmaltz</a>), chances are you are likely going to sit on hold, or have to wait for a support engineer to respond to your request so once you have collected as much information as you can, get the support case rolling.  While you are spending time troubleshooting you are also moving up the support queue to someone who might be able to help.  Worst case scenario, by the time they get back to you, you just close the case because you figured it out.</li>
	<li>Give the customer (remember internal IT departments you are an IT service provider, even if its just for one company) an specific time you will get back to them with an update.  Be clear about what the problem is, what system or systems are affected and that the next response may be nothing more than an update that you have no update.  Set a reminder in your calendar to send the update as well, you don't want to promise an update at 10A and then not follow through.  I have worked through issues where I sent 3 or 4 emails stating that the system was still down and working towards a resolution and that we would respond again within the next hour (or some other time interval that is appropriate for the problem).  Give yourself enough time to hopefully find an answer, but not so short that you keep stopping your work and not so long that the customer is just left wondering.</li>
	<li>What do the logs say?  If something isn't working, in theory there should be a log file with errors in it someplace (though I have certainly run into a few system crashes that happened so quickly the only error was that Windows didn't shutdown properly).  Make sure you have a good system to collect and analyze log files.</li>
	<li>What does the knowledge base say?  Just about every technology company publishes a knowledge base or KB where you can look up error messages, codes or type in symptoms.  Chances are you are not the first person in the world to run into this error/problem.  If the companies KB doesn't have anything, search the GKB (aka google.com).  In addition to the KB, customer support forums are also a great place to look.</li>
	<li>Check with your team.  The 5 steps above should have taken you no more than 10-15 minutes (collect info, open a ticket, review logs, search the KB), if you haven't yet heard back from technical support ask your team.  Remember you are not on an island alone, even if you are a single IT person shop there are others you can lean on.  Maybe there are people the affected department who have been at the company longer than you, if its a system thats been in place for a while they may have had this happen to them before and can tell you who helped them fix it the first time.</li>
	<li>Check in the social-media-o-sphere.  If you are in technology and not taking advantage of social media and the many smart, open and helpful people out there, then I hope this blog post will have you start looking into it.  LinkedIn and Twitter are my go to places if I am just beyond stumped.</li>
	<li>Review the original project documentation.  There are certainly (many) times this may not exist, and if you find yourself thinking that YOU don't have any documentation for your projects maybe its a good time to start.  Typically a consultant/vendor would provide a scope of work, project outline or similar documentation that should state what you are doing with this platform, why you are doing it and what is likely to go wrong in the environment given the design.</li>
	<li>Panic.  Just kidding.... well kind of... no - I am kidding (Still crack up over that comment Rob).  In all seriousness though, if by now you have not found a solution its probably time to start reaching out to local consultants/experts for the system or systems you are having problems with.  It may also be at this point that you realize a system restore is the only viable option and its time to break out the DR/backup and recovery plan so you can get the systems back online.</li>
	<li>Document and share it.  Thanks to Edward Henry (<a href="https://twitter.com/NetworkN3rd" target="_blank">@NetworkN3rd</a>) for the tip and reminder.  Once you have solved the problem, make sure to document the information you collected, the symptoms and how you resolved it.  If it happened once, it will probably happen again.  Share with your team, share via your online resources (customer forums, Twitter, blogs etc...) as others may see a problem, or similar problem in the future.</li>
</ol>
What do you think of the steps above?  Do you use similar steps?  What tips do you have?