---
ID: 486
post_title: Fun with SSL and Exchange 2013
author: Jonathan Frappier
post_date: 2013-02-28 14:10:32
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/fun-with-ssl-and-exchange-2013/
published: true
dsq_thread_id:
  - "1110749902"
---
Now that you are not able to order SSL certificates with internal Subject Alternative Names (SANs) I had a bit of hoop jumping to go through today during an Exchange 2013 install.  It was likely just as much a lack of prep-time but figured if it happend to me, it might happen to you.  Hopefully this helps someone along the way.

I had an Exchagne 2013 server installed with different URLs for internal and external access, this caused problems as soon as I tried to connect exchange (which I half expected) so it was an easy fix, go through the ECP and change the internal URLs to be the actual external URLs.  Sweet - most of my errors for SSL certs went away.

Next, in order to resolve the external FQ sub-domain name I created a zone called mail.externaldomain.com with a single a record (no name) pointing to the internal IP address. There was still one however in Outlook:

<strong>There is a problem with the proxy servers security certificate.</strong>
<strong> ...more errorie stuff...</strong>
<strong> Outlook is unable to connect to the proxy server.  (Error code 10)</strong>

To fix this, after several other failed attempts at various DNS trickery, I created an SRV record in my AD zone (ad.local for example)

domain:  ad.local
Service: _autodiscover &lt;&lt; manually typed
Protocol:  _tcp &lt;&lt; manually typed
Port:  443
Host offering this service:  mail.externaldomain.com &lt;&lt;repace with appropriate external name.

Now I was able to log in to Outlook with no errors, and connected with ActiveSync.