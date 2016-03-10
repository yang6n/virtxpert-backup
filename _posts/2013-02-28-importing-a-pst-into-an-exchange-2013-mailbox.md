---
ID: 475
post_title: >
  Importing a PST into an Exchange 2013
  mailbox
author: Jonathan Frappier
post_date: 2013-02-28 09:18:39
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/importing-a-pst-into-an-exchange-2013-mailbox/
published: true
dsq_thread_id:
  - "1110254319"
---
Thought I'd share since I am dusting off my Exchange PowerShell for a quick project.  Importing an PST should be fairly simple but for those that don't eat drink and sleep Exchange may forget that you have to grant permission to certain roles, even for a domain admin account.  This is a brand new server with 2008 R2 and Exchagne 2013 installed so I hadn't run it yet:

New-ManagementRoleAssignment –Role “Mailbox Import Export” –User "domainuser"

Replace domainuser with your domain and user account, that should finish up nicely and now you can...wait I still can't run the command?  Permissions are loaded when the shell starts so you now have to exit the PowerShell window and re-lauch.  Now you can run the New-MailboxImportRequest command

<a href="http://www2.virtxpert.com/wp-content/uploads/2013/03/command.png"><img class="aligncenter size-full wp-image-535" alt="command" src="http://www2.virtxpert.com/wp-content/uploads/2013/03/command.png" width="463" height="331" /></a>

Now, when you run the command you will see that it is "Queued"

<a href="http://www2.virtxpert.com/wp-content/uploads/2013/03/queue.png"><img class="aligncenter size-full wp-image-538" alt="queue" src="http://www2.virtxpert.com/wp-content/uploads/2013/03/queue.png" width="818" height="123" /></a>

To see the status of the import run Get-MailboxImportRequestStatistics -Identity MailboxMailboxImportName where 'mailbox' is the user account from the image above and 'MailboxImportName' is the name above.  So for example my command looked like

<a href="http://www2.virtxpert.com/wp-content/uploads/2013/03/status.png"><img class="aligncenter size-full wp-image-543" alt="status" src="http://www2.virtxpert.com/wp-content/uploads/2013/03/status.png" width="955" height="89" /></a>

&nbsp;