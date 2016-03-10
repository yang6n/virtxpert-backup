---
ID: 3288
post_title: 'Quick and dirty GitHub for beginers &#8211; your first commit'
author: Jonathan Frappier
post_date: 2014-11-28 11:00:43
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/quick-and-dirty-github-for-beginers-your-first-commit/
published: true
dsq_thread_id:
  - "3271214975"
---
I started my Ansible series really with the intention of getting to know Git/GitHub a bit better but Ansible was so awesome I couldn't put it down.  Now that I have built a couple of example playbooks its time to "commit" those into GitHub.  For starters, we need Git/GitHub installed on our system.  In my case I am doing everything from my Ansible server, though you may want to do this on another system.  Thanks to yum, the install is pretty easy
<pre>yum install git</pre>
I had already run this on my Ansible server so I could "pull" the Ansible code.  Now I want to setup my username so:
<pre>git config --global user.name "yourusername"</pre>
Next register your email account for your GitHub account
<pre>git config --global user.email "youremail"</pre>
Now on to authentication, it's high time I stop using passwords for everything and setup SSH keys so, lets do that.  To create the public key enter:
<pre class="command-line"><span class="command">ssh-keygen -t rsa -C "<em>email@example.com</em>"</span></pre>
<ul>
	<li>While logged in as root it will save to /root/.ssh/id_rsa)</li>
	<li>Next enter your secure password</li>
	<li>With the key now created, log into GitHub and click on the gear icon (Settings) in the upper right corner</li>
	<li>Click on SSH keys</li>
	<li>Click the add SSH keys button</li>
	<li>Provide a title such as "ansible VM" or whatever used to identify the computer</li>
	<li>Back in your terminal window type</li>
</ul>
less /root/.ssh/id_rsa.pub
<ul>
	<li>Copy the contents of the file and paste it into the Key text box</li>
	<li>Click the Add key button</li>
	<li>Back in your terminal window type</li>
</ul>
ssh -T git@github.com
<ul>
	<li>Accept the key from github.com</li>
	<li>Enter the pass phrase for your key</li>
	<li>You should now be logged into GitHub with your keys!</li>
</ul>
[caption id="attachment_3290" align="aligncenter" width="643"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/login-github-ssh-key.png"><img class="size-full wp-image-3290" src="http://www.virtxpert.com/wp-content/uploads/2014/11/login-github-ssh-key.png" alt="Login for GitHub via SSH key" width="643" height="53" /></a> Login for GitHub via SSH key[/caption]
<ul>
	<li>Now, switch the to folder where you are saving your Ansible playbooks</li>
	<li>Type git init</li>
	<li>Type git add .</li>
	<li>Type git commit -m 'playbooks'</li>
	<li>Find the URL from your Git repository (create one if you haven't), make sure to click on SSH, not HTTPS and copy that</li>
</ul>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/git-hub-repository-url21.png"><img class="aligncenter wp-image-3295 size-full" src="http://www.virtxpert.com/wp-content/uploads/2014/11/git-hub-repository-url21.png" alt="" width="1037" height="690" /></a>
<ul>
	<li>Type git remote add origin git@github.com:user/repository.git</li>
	<li>Type git remote -v</li>
	<li>Type git push origin master then enter the pass phrase for your SSH key</li>
</ul>
Now if I go to my repository, I can see my .yml files checked in!

[caption id="attachment_3293" align="aligncenter" width="1052"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/git-hub-files-checkedin.png"><img class="size-full wp-image-3293" src="http://www.virtxpert.com/wp-content/uploads/2014/11/git-hub-files-checkedin.png" alt="GitHub files checked into repository" width="1052" height="557" /></a> GitHub files checked into repository[/caption]

From now on, as we create or update our playbooks we can check them into GitHub for safe keeping and sharing!