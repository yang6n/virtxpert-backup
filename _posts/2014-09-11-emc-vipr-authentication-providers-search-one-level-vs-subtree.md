---
ID: 2602
post_title: 'EMC ViPR Authentication Providers Search:  One Level vs Subtree'
author: Jonathan Frappier
post_date: 2014-09-11 16:44:25
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/emc-vipr-authentication-providers-search-one-level-vs-subtree/
published: true
dsq_thread_id:
  - "3009560537"
---
<a href="http://www.virtxpert.com/wp-content/uploads/2014/09/ViPR-logo.png"><img class="alignleft  wp-image-2604" src="http://www.virtxpert.com/wp-content/uploads/2014/09/ViPR-logo.png" alt="ViPR-logo" width="176" height="178" /></a>I was setting up ViPR to use Active Directory to authenticate users and one option was a bit unclear. You use the Search Base and Search Scope options to define which AD users ViPR will authenticate.  The Search Scope option provides two choices:  One Level and Subtree.  I was a bit confused by One Level, would it search just the specified OU/CN or would it search up to one level below?

One Level will search JUST the specified base DN, so for example to allow only users in ou=corp,dc=domain,dc=local you would use that as the search base and set the search scope to one level.  If you wanted users in all OU's under corp you would just set the search scope to Subtree.

There is another very useful option when setting up the Authentication Provider; Group Whitelist.  You can populate the Group Whitelist with only those groups (and thus group members that you want to be able to log in.  Say for example you wanted all users except sales to have access to log into ViPR, and sales was in an OU nested under corp.  If you set your search base to ou=corp,dc=domain,dc=local and search scope to subtree they could log in.  However, if you added/created in AD group that did NOT include sales and placed it in the group whitelist field those user accounts that were not in the group, in this case sales, would not be able to authenticate.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/09/vipr-ad-search.jpg"><img class="aligncenter size-full wp-image-2603" src="http://www.virtxpert.com/wp-content/uploads/2014/09/vipr-ad-search.jpg" alt="vipr-ad-search" width="702" height="384" /></a>

There you go, easy peasy AD integration in ViPR!