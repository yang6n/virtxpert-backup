---
ID: 4053
post_title: 'Quick How To &#8211; Amazon Identity and Access Management (IAM)'
author: Jonathan Frappier
post_date: 2015-11-07 08:43:16
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/quick-how-to-amazon-identity-and-access-management-iam/
published: true
dsq_thread_id:
  - "4297859145"
---
My poor lab has had enough, time to rebuild. I've always used a Windows Domain for authentication, and you can make that reasonably small but during this rebuild I am going to try and leverage Amazon Directory Services...because cloud? Before creating your directory service, however, you should setup accounts in Identity and Access Management, or IAM. IAM is a free service, so you can use this without incurring any additional cost.

Log into the AWS Management Console and find Identity &amp; Access Management (green key icon) under Security &amp; Identity. First I am going to setup a directory services user and group. Whenever possible, and Amazon supports this, I assign permissions to group so it is easy to change who has access later on. It generally also makes it easy to audit.

Before getting started, I will also edit the default password policy which can be found under account settings in the left navigation pane. Chose a password policy that you are comfortable with, or for business that fits your security policies, then click Apply password policy.

For individual users accessing services, I use a different username than their regular accounts. I do this whether it is Microsoft AD or even local machine access. Click on Users &gt;&gt; Create New Users, enter a username and click create. Download the user credentials and store them in a safe place.

Click the checkbox for the user you just created and click User Actions &gt;&gt; Manage Password. Here you can set an auto generated password, or an administrator assigned password. This is also where you would force the user to change their password at next login. I assigned a specific password and set to require a new password at next sign-in.

In the details menu in the left navigation pane click on Groups &gt;&gt; Create new Group and enter a name for your group. For example vxprt-admins

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/iam-admins-group.png"><img class="aligncenter size-full wp-image-4054" src="http://www.virtxpert.com/wp-content/uploads/2015/11/iam-admins-group.png" alt="iam-admins-group" width="461" height="166" /></a>

Now click Next Step at the bottom of the page. You can now attach policies to the group, in this case I will select AWSDirectoryServiceFullAccess since the users in this group will be managing directory services. Click Next Step again, confirm the settings and click Create Group.

Click the checkbox for the group and click on Group Actions &gt;&gt; Add Users to Group; select the user or users you just created and click Add Users. Now that a user has been created, and assigned to a group with privileges click on Dashboard. Here you can find the IAM user sign in link. Copy the link and sign in with the user you just created - what were the results?

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/change-pw.png"><img class="aligncenter size-full wp-image-4057" src="http://www.virtxpert.com/wp-content/uploads/2015/11/change-pw.png" alt="change-pw" width="636" height="381" /></a>

Well if you were following along with my blog post, you should have been prompted to change the password as we see above. Now that you are signed in what do you see? Yea, I see everything as well, not exactly what I expected - let's poke around. Click on EC2 - well that is promising seems I am not authorized which is what I would expect based on the group privileges I assigned.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/group-ec2-access.png"><img class="aligncenter size-full wp-image-4058" src="http://www.virtxpert.com/wp-content/uploads/2015/11/group-ec2-access.png" alt="group-ec2-access" width="1026" height="163" /></a>

Now, just to confirm, click on Launch Instance  and select the Amazon Linux AMI

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/error.png"><img class="aligncenter size-full wp-image-4060" src="http://www.virtxpert.com/wp-content/uploads/2015/11/error.png" alt="error" width="732" height="115" /></a>

Cool - permissions working as expected so far. Now Navigate back to the console (the terracotta colored box on the top left side of the page) and click Directory Service... no errors! In my next post I will setup AWS Directory Serivces and hopefully down the road join my new lab vCenter to it.

&nbsp;