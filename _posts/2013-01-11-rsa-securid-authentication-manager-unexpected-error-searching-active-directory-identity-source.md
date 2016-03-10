---
ID: 347
post_title: >
  RSA SecurID Authentication Manager
  Unexpected Error searching Active
  Directory Identity Source
author: Jonathan Frappier
post_date: 2013-01-11 08:29:43
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/rsa-securid-authentication-manager-unexpected-error-searching-active-directory-identity-source/
published: true
jabber_published:
  - "1357910989"
publicize_twitter_user:
  - jfrappier
email_notification:
  - "1357910992"
publicize_reach:
  - 'a:2:{s:7:"twitter";a:1:{i:1983177;i:536;}s:2:"wp";a:1:{i:0;i:15;}}'
tagazine-media:
  - 'a:7:{s:7:"primary";s:0:"";s:6:"images";a:0:{}s:6:"videos";a:0:{}s:11:"image_count";i:0;s:6:"author";s:7:"7110326";s:7:"blog_id";s:8:"38472741";s:9:"mod_stamp";s:19:"2013-01-11 13:29:43";}'
reddit:
  - 'a:2:{s:5:"count";i:0;s:4:"time";i:1359052850;}'
dsq_thread_id:
  - "1117115659"
---
For some reason I can't get Mr. Mackey out of my head on this one - "Quotes are bad...mmmmkay."  I recently inherited a project to get SecurID working and, it seemed pretty straight forward.  I had setup SecurID at previous companies so I   was sure it was something obvious.

After reviewing the config, and reviewing the documentation from RSA - which is good, it doesn't read as a "Step-by-step to setting up AD" but it works.  I opened a support ticket with RSA (non-urgent) and they got back to me within just a couple hours.  The documentation provided by RSA for both the Authentication Manager installation and configuration and the firewall configuration were both spot on.

The problem was, when the identity source was originally setup in the RSA Operations Console, "quotes" were used around the user and user group base DN fields.  What was odd, if I entered an OU that didn't exist I would get an error, so it was seemingly reading the fields with the quotes but when I went to search for users in the Security Console I would get an 'unexpected' error.  Removing the quotes around the user and user group base DN fields fixed this problem.