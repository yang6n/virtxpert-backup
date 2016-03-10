---
ID: 3384
post_title: 'On the second day of Commitmas &#8211; git clone, git add, git commit, git push'
author: Jonathan Frappier
post_date: 2014-12-22 20:56:36
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/on-the-second-day-of-commitmas-git-clone-git-add-git-commit-git-push/
published: true
dsq_thread_id:
  - "3350994595"
---
[display-posts category="commitmas" display-posts posts_per_page="15"]

Day two of commitmas, I have my Windows computer setup and SSH keys added to my GitHub account. Time to clone my existing repository to make a few edits. First, I created a directory on my computer called 'git' where I'll save all my work; cd to that directory and run git init

Now, log into GitHub and find the repository you wish to clone, in the lower right corner of the screen you will see the Git clone URL for the repository. In my case I want the SSH URL so click on SSH.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/12/git-clone.png"><img class="aligncenter size-full wp-image-3385" src="http://www.virtxpert.com/wp-content/uploads/2014/12/git-clone.png" alt="git-clone" width="1022" height="807" /></a>Now in your console type git clone git@github.com:jfrappier/ansible-test-playbooks.git or your repository; when prompted enter the passphrase for your SSH key. You should now have your files on your local machine.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/12/git-clone-local.png"><img class="aligncenter size-full wp-image-3386" src="http://www.virtxpert.com/wp-content/uploads/2014/12/git-clone-local.png" alt="git-clone-local" width="672" height="310" /></a>

Edit a file, for example the README file. Once the file has been edited and saved, we want to get the file back into the repository. To see what files have been changed, run git status. As you can see here my README file was modified.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/12/git-status.png"><img class="aligncenter size-full wp-image-3387" src="http://www.virtxpert.com/wp-content/uploads/2014/12/git-status.png" alt="git-status" width="672" height="196" /></a>

As you can also see in the screen show we need to run git add, for example git add README or git add . - with the file added you now commit your changes by running git commit (this launches vi so press i to go to insert mode, enter a note then press esc :wq enter). Finally, git push to put the file back into GitHub. As you can see here I just updated my README file.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/12/git-push.png"><img class="aligncenter size-full wp-image-3388" src="http://www.virtxpert.com/wp-content/uploads/2014/12/git-push.png" alt="git-push" width="803" height="450" /></a>Tomorrow we will get into forking!