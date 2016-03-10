---
ID: 151
post_title: >
  Setting up Alienvault / OSSIM and Snare
  to collect Windows Event Logs
author: Jonathan Frappier
post_date: 2012-09-23 17:47:03
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/setting-up-alienvault-ossim-and-snare-to-collect-windows-event-logs/
published: true
dsq_thread_id:
  - "1124846015"
jabber_published:
  - "1348422423"
email_notification:
  - "1348422424"
tagazine-media:
  - 'a:7:{s:7:"primary";s:0:"";s:6:"images";a:0:{}s:6:"videos";a:0:{}s:11:"image_count";i:0;s:6:"author";s:7:"7110326";s:7:"blog_id";s:8:"38472741";s:9:"mod_stamp";s:19:"2012-09-23 17:47:03";}'
reddit:
  - 'a:2:{s:5:"count";i:0;s:4:"time";i:1358396112;}'
---
Recently, I implemented a Security Information and Event Management (SIEM) tool called Alienvault / OSSIM  to monitor servers/event logs to ensure compliance with several customer security agreements.  I chose Alienvault because it combined several open source tools, providing a single pane of glass view into what would otherwise be several different tools (oh and I had no budget to do this with).  During the implementation I hit a snag when configuring Alienvalt to monitor Windows Server event logs.  After combing through the forums I found a combination of problems that needed to be fixed – hopefully this will help out others (while giving credit to all the posts we used to find the solution to our problem).

First, follow the documentation for setting up Alienvault and Snare (<a href="http://communities.alienvault.com/docs/collect/Snare_windows.pdf" target="_blank">here</a>).  When you get to the ‘That’s all’ line, that is where the fun begins (c’mon did you expect it to be THAT easy…it is Linux).  First off, I found that the Registry file you were told import did not import properly, I had to change the following key in the Windows Registry: HKLMSOFTWAREInterSect AllianceAuditServiceNetworkDestPort – change this key to 514.  It was set to 6161.  Now I could see events appearing in the SYSLOG on our OSSIM server (you can do this by SSHing to your OSSIM server and running a tail -f ./var/log/syslog).

The second problem was the SNARE plugin was set to read and normalize the information from a log file that did not exist.  To correct, again SSH to your OSSIM server and edit the snare.cfg file by typing vi ./etc/ossim/agent/plugins/snare.cfg (<a href="http://www.lagmonster.org/docs/vi.html" target="_blank">quick vi reference sheet</a>).  Comment out the source log line that reads location=/var/log/snare.log by placing a # in front of it, and entering a new line which reads location=/var/log/syslog and restart the OSSIM agent by running ./etc/init.d/ossim-agent restart.

Now all seemed swell, BUT (again c’mon its linux there is always a but) when we tried to add custom events to the SNARE configuration they would not appear even though I could see them hit the SYSLOG.  I tested the config file against the rules thanks to this <a href="https://www.alienvault.com/forum/index.php?t=msg&amp;goto=11110&amp;S=aeff4b798095bfa89d45711ff32a743f" target="_blank">post</a>.  The first step was to create a test log file which I did by running grep -i 011104 ./var/log/syslog &gt;&gt; ./var/log/logtest.log.  Replace 011104 with the category ID from SNARE that matches your specific event.  Now I ran ./usr/share/ossim/scripts/regexp.py ./var/log/logtest.log /etc/ossim/agent/plugins/snare.cfg V to make sure it was matching the rules in the SNARE config file (snare.cfg) – which it was.  I found this updated <a href="https://www.assembla.com/code/os-sim/git-2/nodes/5c0f27f2c64560f0506ebd1bf8b9547b16b86f92/os-sim/agent/etc/agent/plugins/snare.cfg" target="_blank">config file</a> thanks to <a href="http://www.ithowto.ro/2012/03/ossim-3-1-alienvault-snare-snarewindows-configuration-howto/" target="_blank">ithowto.ro</a> and replaced all of the events (just the last section of the file) in our SNARE config (for my Windows friends use FileZilla to SSH to your OSSIM server and navigate to the snare.cfg file, backup and replace it) and restarted the ossim agent again, but now we were not matching any of the rules.  After comparing the original snare.cfg with the one from the previous website, we pulled out the [Snare -zzz- Generic Rule] which we were matching to previously, dropped it at the top of the new list and renamed it it to [Snare-whywontyouwork] (I was a little grumpy after fighting this for 2 days), replaced the config file again and restarted the agent again and – like magic, our events were now appearing in the OSSIM web interface.  Why….1 word - linux.

A few other shout outs to folks in these posts:  <a href="http://labs.alienvault.com/labs/index.php/2007/tutorial-5-windows-event-logging/">http://labs.alienvault.com/labs/index.php/2007/tutorial-5-windows-event-logging/</a>, <a href="https://www.alienvault.com/forum/index.php?t=msg&amp;goto=7781&amp;S=0040ef7607b76619b65b9362027f16ac">https://www.alienvault.com/forum/index.php?t=msg&amp;goto=7781&amp;S=0040ef7607b76619b65b9362027f16ac</a>, <a href="http://forums.fedoraforum.org/archive/index.php/t-241555.html">http://forums.fedoraforum.org/archive/index.php/t-241555.html</a>, <a href="https://www.alienvault.com/forum/index.php?t=msg&amp;goto=11110&amp;S=aeff4b798095bfa89d45711ff32a743f">https://www.alienvault.com/forum/index.php?t=msg&amp;goto=11110&amp;S=aeff4b798095bfa89d45711ff32a743f</a>, <a href="http://stujordan.wordpress.com/2012/02/15/snare-plugin-not-working-on-alienvault-ossim-3-1/">http://stujordan.wordpress.com/2012/02/15/snare-plugin-not-working-on-alienvault-ossim-3-1/</a>