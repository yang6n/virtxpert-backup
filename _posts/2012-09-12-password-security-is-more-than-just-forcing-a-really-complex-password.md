---
ID: 126
post_title: >
  Password security is more than just
  forcing a really complex password
author: Jonathan Frappier
post_date: 2012-09-12 18:48:25
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/password-security-is-more-than-just-forcing-a-really-complex-password/
published: true
jabber_published:
  - "1347475706"
email_notification:
  - "1347475707"
tagazine-media:
  - 'a:7:{s:7:"primary";s:49:"http://imgs.xkcd.com/comics/password_strength.png";s:6:"images";a:1:{s:49:"http://imgs.xkcd.com/comics/password_strength.png";a:6:{s:8:"file_url";s:49:"http://imgs.xkcd.com/comics/password_strength.png";s:5:"width";i:740;s:6:"height";i:601;s:4:"type";s:5:"image";s:4:"area";i:444740;s:9:"file_path";s:0:"";}}s:6:"videos";a:0:{}s:11:"image_count";i:1;s:6:"author";s:7:"7110326";s:7:"blog_id";s:8:"38472741";s:9:"mod_stamp";s:19:"2012-09-12 18:48:25";}'
dsq_thread_id:
  - "1294236472"
---
Everyone seems to be all concerned about passwords lately, you know those things most people hate and us geeks have come up with a system so we don't forget ours (I can go back about 6 years).  More and more companies are enforcing stricter password policies to "protect their data" but in reality, most users don't have access to very sensitive data or even systems that could cause problems for other users on the network.  Now I am not suggesting passwords aren't needed, but auditors and other people responsible for setting password policies need to take into account everything that makes up "password security" - not just password length and complexity.

Most password policies have several layers:
<ol>
	<li>Password Length</li>
	<li>Password Complexity</li>
	<li>Account Lockout Threshold</li>
	<li>Account Lockout Duration</li>
	<li>Security Log Monitoring</li>
</ol>
Lets review and see how forcing long, complex passwords may not always be the best answer.  First, if we have learned nothing else from <a href="http://xkcd.com/936/" target="_blank">XKCD </a>its that longer passwords are better than single words with special characters and numbers, so IT and security practitioners enforcing longer passwords are on the path to being correct, however we should look at pass-phrases, not passwords.  Also consider that PCI compliance only requires a password to be 7 characters long.  Now a 7 letter password is quite easy to crack, if you have no other security measures in place you could expect a password like 'academy' to be compromised within 2 seconds (according to <a href="http://howsecureismypassword.net/">http://howsecureismypassword.net/</a>), an 8 letter word could be compromised in 52 seconds, a 12 letter password - 'disinfectant' would take 276 days!   Now if we go with a pass phrase 'i like frosted flakes' it would take 413 QUADRILLION YEARS!

<img class="aligncenter" title="&quot;Unlearn what you have learned&quot; - Yoda" src="http://imgs.xkcd.com/comics/password_strength.png" alt="" width="740" height="601" />

Password complexity, while a good habit, does not offer the affect people expect, especially when combined with very long password length policies.  Again, lets think about the XKCD example - whats a better password, one a person can remember or one that a person has to write down on a post it note attached to their laptop?  For my money, a "secure" password is one that exists it only one place - someones memory and a "weak" password is really only at risk once it has been targeted and compromised.  Its much easier to compromise a password when it is written down in front of you.  Lets consider the previous example passwords and do a common letter/special character replacement.  '@cad3my' would take 3 minutes to be cracked, quite a bit longer than 2 seconds but not very long at all if there are not other security measures in place.  'D1sinfe(t@nt' would take 344 Thousand years to crack - not to shabby at all, probably won't be around to worry about that so you are all set right?  Well thinking about the ability for someone to remember their passwords versus writing it down and having it instantly compromised, what do you think someone is more likely to remember - 'i like frosted flakes' or 'D1sinfe(t@nt'?  I like me some frosted flakes to.

Now, lets for a second pretend I am wrong and that a "weak" password is a hackers dream and there are hackers constantly on your network trying to crack passwords and logging into the receptionists email with derail the efforts of the entire company (not saying receptionist don't work hard or not valuable, but they probably don't have access to social security numbers or confidential company information).  Your Account Lockout Threshold should account for this.  Lets say Sam uses a very basic password and the hackers are secretly on your network because you have no other network or security monitoring in place and don't review your event logs, generally after 3 failed log in attempts your account is locked - problem solved now Sam or the hacker can't log in.  If you set this to a reasonably low number, I normally use 3, the hacker has 3 shots before the account is locked so even if they guessed/cracked the password on the 4th try, it will look like it is failed because the account is now locked.  Also, someone in IT has now been notified, and if it continues to happen hopefully a light bulb will go off in said IT persons head that something is fishy.

It's fun pretending to be wrong, so lets continue and Discuss Account Lockout Duration.  What's that - you have your network accounts set to re-enable after 15 minutes because you hate talking to people?  Well yea then you have a problem, but if you have good security practices in place your accounts will stay locked until someone unlocks the account, or even in a semi-lazy environment maybe it resets after 30 minutes or 1 hour.  Good news is a constant, brute force type attack will only get off 72 password attempts per day (3 attempts before its locked, locked for an hour, 3 more attempts before locking again - 3 x 24 = 72 passwords).

Last but not least, hopefully someone, somewhere in your IT group at least glances at event logs or has something like Splunk or Snare setup to capture and alert on certain events.  Even if you don't, someone would have to notice the uptick in help desk requests coming in and start to wonder what is happening and look into stopping the password cracking attempts.  Now some of you are saying, what about password expiration - forcing people to change passwords they finally remembered every 30, 60 or 90 days?   As I have said a couple of times previously, a password is only insecure when it actually has become compromised, so forcing password changes every 30 days is simply overkill - you can't crack my 'i love frosted flakes' password in ... well a long time so what are we solving by forcing people to replace them?

Password security is about much more than just length + complexity.  We have seen that a long, easy to remember password is just as secure from cracking as a single word with random characters replacing letters.  A good password is one someone can remember and not instantly compromised by being written down on a laptop or monitor.  We <strong>don't</strong> need special characters and case to make a secure password - just remember what cereal you are eating that week is more secure than than random character replacement.