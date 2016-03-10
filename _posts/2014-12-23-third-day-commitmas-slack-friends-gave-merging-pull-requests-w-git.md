---
ID: 3395
post_title: 'On the third day of Commitmas, my slack friends gave to me &#8211; Merging Pull Requests w Git'
author: Jonathan Frappier
post_date: 2014-12-23 10:42:00
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/third-day-commitmas-slack-friends-gave-merging-pull-requests-w-git/
published: true
dsq_thread_id:
  - "3352719000"
---
[display-posts category="commitmas" display-posts posts_per_page="15"]

Today I was chatting with Tim Jabaut in a Slack room Matthew Brender created for Commitmas (ping him or Josh Cohen to get in) and he shared a nice <a href="http://daringfireball.net/projects/markdown/syntax#em" target="_blank">markdown cheat sheet</a> (I seem to be all about <a href="https://training.github.com/kit/downloads/github-git-cheat-sheet.pdf" target="_blank">cheat sheets</a> during Commitmas). If you have <a href="https://github.com/mjbrender/12-days-of-commitmas" target="_blank">looked at the Commitmas GitHub page</a> you see that Matt and others have made his page pretty; it has been done using markdown. I tried adding some simple markdown to my README file on my <a href="https://github.com/jfrappier/ansible-test-playbooks" target="_blank">Ansible Test Playbooks</a> page but they were just coming over as ##, not as headings.

So, troubleshooting in this new era - it is certainly not done by emailing someone a file! Tim forked my repository to have a look; my README file needed a .MD extension to properly interpret the markdown syntax. With the change complete, Tim issued a pull request which you can see below

<a href="http://www.virtxpert.com/wp-content/uploads/2014/12/git-pull-request.png"><img class="aligncenter size-full wp-image-3396" src="http://www.virtxpert.com/wp-content/uploads/2014/12/git-pull-request.png" alt="git-pull-request" width="1012" height="600" /></a>The question now becomes, how do I merge that change? GitHub was nice enough to drop me an email with some tips.

First, I need to merge the changes:
<pre>git pull <a href="https://github.com/tjabaut/ansible-test-playbooks" target="_blank">https://github.com/tjabaut/<wbr />ansible-test-playbooks</a> master</pre>
Once that is done, you can see I have the changes from Tim in my local repository - my README file is now named README.md

<a href="http://www.virtxpert.com/wp-content/uploads/2014/12/git-pull-local.png"><img class="aligncenter size-full wp-image-3397" src="http://www.virtxpert.com/wp-content/uploads/2014/12/git-pull-local.png" alt="git-pull-local" width="672" height="227" /></a>

I can now inspect changes to the file that Tim made; for example it may not be something as trivial as a file name. If this were a change say to an Ansible playbook I might want to review what those changes before putting them into the repository. With the file(s) local to me now, I can:
<pre>git add .

git push</pre>
to merge this change back into the repository. Here you can see the changes before and after my git push.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/12/git-repo-merged.png"><img class="aligncenter size-full wp-image-3398" src="http://www.virtxpert.com/wp-content/uploads/2014/12/git-repo-merged.png" alt="git-repo-merged" width="1018" height="844" /></a>

&nbsp;