---
ID: 443
post_title: >
  Removing a failed Exchange 2013 install
  on Windows 2008 R2
author: Jonathan Frappier
post_date: 2013-02-21 11:46:32
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/removing-a-failed-exchange-2013-install-on-windows-2008-r2/
published: true
dsq_thread_id:
  - "1096984979"
---
**Use this with caution, the server ended up completely sideways and we were not able to re-install Exchange, not sure yet if it was how it was uninstalled or carry over problems from the original installation**

One of our engineers was installing Exchange 2013 on Windows 2008 R2, however there were several errors during the install but all of the Exchange services installed.  Coming in from the outside my first inclination was to remove it and start from scratch with <a href="http://www.petri.co.il/how-to-install-exchange-server-2013.htm" target="_blank">a known good install guide</a>.  The engineer went into Programs to remove the software, however after about 10 minutes it failed because it was unable to stop the Hub Transport service.  Rather than uninstalling via the control panel, I launched a command prompt (Run as administrator) and navigated where the install files were located and ran the following command:

setup.exe /mode:uninstall /IAcceptExchangeServerLicenseTerms (is it me or is a bit annoying I always need the /IAcceptExchangeServerLicenseTerms switch?).

This uninstall went as expected and removed all the services and items that had been previously installed.