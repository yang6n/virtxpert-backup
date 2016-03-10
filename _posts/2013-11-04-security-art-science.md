---
ID: 1456
post_title: Security is an art, not a science
author: Jonathan Frappier
post_date: 2013-11-04 10:02:33
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/security-art-science/
published: true
dsq_thread_id:
  - "1935498668"
---
I recent conversation with a friend reminded me of some scenarios around security for the sake of security, and not based in the reality of business needs.  Security is certainly a fine line to walk, my definition of security is "The balance between safe guarding critical information and business operations."  I find myself in many conversations, seemingly in an argument against security, but that is not it at all.  If I am arguing against a certain security setting its because

A) The change or setting is not widely accepted or

B) The change, while secure in nature, does not add to the overall security of the critical information we need to protect and impedes business operation.

Let's review a couple of examples from some previous companies/customers I have worked for.

At company AB, the security officer only allowed certain individuals to recall backup tapes from our off-site storage vendor, so far I am cool with this.  However, IT - the team ultimately responsible for doing the data restore, was not on the approved list for recalls, this created a couple of problems.  First, when it was discovered that tapes needed to be recalled, we were often delayed in requesting the recall because the person who could was not available.  In a few cases this resulted in the tape return being delayed until the next business day.  Now I understand wanting to limit the list of who can recall tapes, but not including IT was not in anyway protecting the critical information on these tapes; after all we were the ones doing the backups and had physical access to all the servers storing the data, if I really wanted it I had better ways to get it than from a backup tape and it impeded business operation by delaying our ability to respond to customer request.  I think this example shows exactly what I mean by security being a balance; limiting access to recall tapes is certainly "secure" but it didn't factor in the operational considerations.

At another company, our web development team insisted that certain servers required a BIOS password in order to boot.  The goal was to prevent data loss and unauthorized access.  Again, I follow the logic but disagree that its the appropriate solution to secure a server.  This caused many problems when web developers were installing software, patches or if we had an unexpected outage caused by a crash (Windows, power outage, whatever) because the server could no longer boot until someone entered the password.  The boot password at start up prevented the servers from coming back online if they were rebooted (for any reason) and prevented the development team from being able to access them in these scenarios.  The servers were already secured in our server room which had limited badge based access already.  If the boot password was preventing unauthorized access, we had bigger problems already, and even if the computer was booted, you still needed a user account and password with access to the server.  So for the sake of "security" there was again a case of negative operational impact without adding any necessary security processes.

For the folks that deal with security (which should be all of us), what do you think?  Do you have any examples of security practice not actually securing anything and causing a negative impact on operations?  I certainly have more, like a company who acquired us and insisted exposing SSL secured logins to a website using AD authentication was insecure; yet exposed access to Citrix via SSL and authenticated users via AD but I will leave those memories for me and Frank!

&nbsp;