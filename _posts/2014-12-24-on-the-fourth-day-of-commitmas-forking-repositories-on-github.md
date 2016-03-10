---
ID: 3402
post_title: 'On the fourth day of Commitmas &#8211; Forking repositories on GitHub'
author: Jonathan Frappier
post_date: 2014-12-24 09:59:16
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/on-the-fourth-day-of-commitmas-forking-repositories-on-github/
published: true
dsq_thread_id:
  - "3356153313"
---
[display-posts category="commitmas" display-posts posts_per_page="15"]

Yesterday Tim Jabut forked my Ansible test repo on GitHub to help me get markdown working and I merged that back into my repository. Today it is time to learn how to fork a repository on GitHub myself. If you take a look at a repository on GitHub, you'll see a Fork button on the upper right corner of the page:

<a href="http://www.virtxpert.com/wp-content/uploads/2014/12/git-fork.png"><img class="aligncenter size-full wp-image-3403" src="http://www.virtxpert.com/wp-content/uploads/2014/12/git-fork.png" alt="git-fork" width="1026" height="943" /></a>

Click the Fork button, after a few moments the page will return - notice the difference?

<a href="http://www.virtxpert.com/wp-content/uploads/2014/12/git-forked.png"><img class="aligncenter size-full wp-image-3406" src="http://www.virtxpert.com/wp-content/uploads/2014/12/git-forked.png" alt="git-forked" width="1017" height="639" /></a>

Yup, I now have a copy of this repository in my account. Switch over to your console and clone the repository locally. For example
<pre>git clone git@github.com:jfrappier/12-days-of-commitmas.git</pre>
I can now work on these files locally, for example here is the 12 Days of Commitmas (2014) opened in Markpad (choco install markpad)

<a href="http://www.virtxpert.com/wp-content/uploads/2014/12/markpad-commitmas.png"><img class="aligncenter size-full wp-image-3407" src="http://www.virtxpert.com/wp-content/uploads/2014/12/markpad-commitmas.png" alt="markpad-commitmas" width="1259" height="737" /></a>

With a few changes made, I commit my file back to my repository. Do you remember what commands we need to do that?

<pre>git add .

git commit

git push</pre>

And here we are, files are in <em>*my* </em>repository. Next we will look at issuing a pull request so the owner of the repository can merge my changes into their repository.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/12/git-forked-commit.png"><img class="aligncenter size-full wp-image-3408" src="http://www.virtxpert.com/wp-content/uploads/2014/12/git-forked-commit.png" alt="git-forked-commit" width="1012" height="551" /></a>