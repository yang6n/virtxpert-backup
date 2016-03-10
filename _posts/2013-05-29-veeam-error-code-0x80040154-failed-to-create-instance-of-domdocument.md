---
ID: 1001
post_title: 'Veeam Error code: 0x80040154 Failed to create instance of DOMDocument'
author: Jonathan Frappier
post_date: 2013-05-29 14:11:07
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/veeam-error-code-0x80040154-failed-to-create-instance-of-domdocument/
published: true
dsq_thread_id:
  - "1335280054"
---
We recently came across an error that I could not find in Veeam's support site (though it did return several hundred, seemingly unrelated entries), the error was
<pre>Error code: 0x80040154 Failed to create instance of DOMDocument</pre>
This caused our backups to fail.  I sent a tweet to <a href="https://twitter.com/veeam" target="_blank">@Veeam</a> to see if they had anymore and in typical awesome fashion they responded within minutes.  Right now there is a private hotfix so you will need to contact support, once I get to review the cause I will let you know.  As a band-aid, restarting the Veeam Backup Proxy Service seems to clear this.