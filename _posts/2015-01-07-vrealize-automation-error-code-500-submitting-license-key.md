---
ID: 3429
post_title: 'vRealize Automation Error Code: 500 when submitting license key'
author: Jonathan Frappier
post_date: 2015-01-07 10:18:42
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vrealize-automation-error-code-500-submitting-license-key/
published: true
dsq_thread_id:
  - "3398758537"
---
Chalk this up in the "useful error messages" column. When you attempt to enter a license key in the vRealize Automation appliance you receive "Error code: 500."

<a href="http://www.virtxpert.com/wp-content/uploads/2015/01/error500.png"><img class="aligncenter size-full wp-image-3430" src="http://www.virtxpert.com/wp-content/uploads/2015/01/error500.png" alt="error500" width="826" height="328" /></a>

Now when I saw this I immediately thought "internal server error," however in the case of vRA it may simply be an expired or invalid license key. Before extensive troubleshooting validate that your license key is correct, and it has not expired.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/01/license-success.png"><img class="aligncenter size-full wp-image-3431" src="http://www.virtxpert.com/wp-content/uploads/2015/01/license-success.png" alt="license-success" width="829" height="328" /></a>