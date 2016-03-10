---
ID: 739
post_title: 'Stupid group policy&#8230;'
author: Jonathan Frappier
post_date: 2013-04-10 12:32:45
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/stupid-group-policy/
published: true
dsq_thread_id:
  - "1299633487"
---
Well actually as in most "stupid computer" cases the computer was being smart and doing exactly what it was told.  My company recently did a network upgrade for one of our customers and everything was going swimmingly until two users called, they couldn't get to their network drives, well in reality they could but the group policy to map the drives was not working.  First step I took was to ensure I could read the sysvol folder on the DC's, sure enough I could but when I ran the login scripts (its complicated don't ask...) it prompted me for a password.

Well the login script for the drive mapping policy was being blocked because each users "personal" folder was set to be created if it didn't exist at login, thus making that user creator/owner but their folders already existed, however the "owner" was the domain admin so the drive mapping script would hang waiting for a password in the background!