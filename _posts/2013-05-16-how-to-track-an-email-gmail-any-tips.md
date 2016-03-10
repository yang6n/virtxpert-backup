---
ID: 845
post_title: 'How to track an email (gmail) &#8211; any tips?'
author: Jonathan Frappier
post_date: 2013-05-16 15:20:10
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/how-to-track-an-email-gmail-any-tips/
published: true
dsq_thread_id:
  - "1295291925"
---
Recently a customer asked us to track who sent an email, typically if this was done on an Exchange server I had a few more logs to look at, however the email was from a Gmail account.  First thing I do to track an email is to check the SMTP header and verify it was sent from a specific server, which in this case (gmail.com) it appears to be.  Short version of the story I don't know of any way to track down a message but the client insisted we can so this is my story.  Any tips would be greatly appreciate if I missed something.

The SMTP headers in the email only states it was sent from a Gmail server, it shows no reference that it was sent from any of the customer servers.  If the message was sent from the customers server then we could see logs; the logs might show us the IP address of the device so long as it was on your network (mobile device, laptop etc…) and the time the message was sent, the user account logged in from that device but again the message headers of the email do not show any of that.

I have highlighted some parts of the message header that would be relevant.

The line below shows us that the spam filtering server, which acts as an SMTP relay received an SMTP request from a server called mail-ve0-f195.google.com at IP address 209.85.128.195 by our spam filter <em>smtprelay.domain.com</em>, being sent to user@domain.com.  A simple ping confirms the name resolution from the sending server.  SMTP has a very simple authentication process, basically the SMTP server of the sender issues a series of commands (which as an aside are very easy to spoof with any free SMTP service).  If in fact the person who sent the message spoofed a gmail address using a different SMTP server, such as smtp.fakedomain.com, we would see that as the sending server.

<!--more-->Received: from mail-ve0-f195.google.com (mail-ve0-f195.google.com [209.85.128.195]) by <em>smtprelay.domain.com</em> with ESMTP id XXXXXXXXXXXXXXXXX for user@domain.com

<a href="http://www.virtxpert.com/wp-content/uploads/2013/05/pinggmail.png"><img class="aligncenter size-full wp-image-846" alt="pinggmail" src="http://www.virtxpert.com/wp-content/uploads/2013/05/pinggmail.png" width="679" height="344" /></a>

To show the difference, you can see in the screenshot below I sent an email to an account I use for junk mail, junkaddress<a href="mailto:neojd78@yahoo.com">@yahoo.com</a> from <a href="mailto:fakejon@gmail.com">fakejon@gmail.com</a> by spoofing the gmail.com domain through a generic SMTP server.  It is actually very easy to “spoof” a from email address but the sending server, to my knowledge, can NOT be spoofed.

<a href="http://www.virtxpert.com/wp-content/uploads/2013/05/yahoo.png"><img class="aligncenter size-full wp-image-847" alt="yahoo" src="http://www.virtxpert.com/wp-content/uploads/2013/05/yahoo.png" width="665" height="205" /></a>

Now the difference here, since it wasn’t really sent from Gmail, the from server is NOT google.com, it was from <b>startdedicated.com</b>.   As we see in the SMTP header from the message we were asked to investigate, it its coming from google.com.

Received: from 127.0.0.1  <b>(EHLO zebra732.startdedicated.com)</b> (188.138.112.172) by mta1367.mail.gq1.yahoo.com with SMTP; Thu, 16 May 2013 06:28:56 -0700

Also, the configuration of the Exchange server is such that it will only accept SMTP connections from specific IP address.  This means the person trying this would have had to manually assign an IP address from the allowed server IP addresses in order to relay SMTP commands through the Exchange server.  If we assume for a moment they were able to do that, they would have then had to issue SMTP commands on the Exchange server similar to the following:

<a href="http://www.virtxpert.com/wp-content/uploads/2013/05/smtpcommands.png"><img class="aligncenter size-full wp-image-848" alt="smtpcommands" src="http://www.virtxpert.com/wp-content/uploads/2013/05/smtpcommands.png" width="670" height="329" /></a>

The message would then be received and appear to be from gmail.com as pictured:

<a href="http://www.virtxpert.com/wp-content/uploads/2013/05/fromfakegmail.png"><img class="aligncenter size-full wp-image-849" alt="fromfakegmail" src="http://www.virtxpert.com/wp-content/uploads/2013/05/fromfakegmail.png" width="956" height="222" /></a>

However, further investigating the SMTP header as we did with the Yahoo/Gmail example we would see that it came from <em>yourserver.domain.com</em>

Received: from <em>yourserver.domain.com</em> (<em>yourserver.domain.com</em> [nnn.nnn.nnn.nnn]) by <em>smtprelay.domain.com</em> with ESMTP id for &lt;me@domain.com&gt;; Thu, 16 May 2013 10:34:22 -0400 (EDT).

Again, if anyone can teach me a thing or two on this I would be very appreciative.

&nbsp;