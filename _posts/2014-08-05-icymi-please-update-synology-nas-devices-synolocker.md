---
ID: 2449
post_title: 'ICYMI &#8211; Please Update your @Synology NAS devices &#8211; SynoLocker'
author: Jonathan Frappier
post_date: 2014-08-05 18:01:27
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/icymi-please-update-synology-nas-devices-synolocker/
published: true
dsq_thread_id:
  - "2903629483"
---
It's been a hard summer on <span class="il" style="color: #222222;">Synology</span>.  Earlier in the summer reports of a vulnerability that allowed hackers to use publicly accessible <span class="il" style="color: #222222;">Synology</span> devices to mine BitCoin.  Now comes news of another "vulnerability" known as SynoLocker that allows hackers to seize control and encrypt the contents of a users device - <em><strong>HOWEVER</strong> </em>- it appears that this only affects<span class="il" style="color: #222222;">Synology</span> devices with firmware prior to December 2013.  That means your device, that you placed on the public internet, has gone un-patched for almost 9 months.

<span class="il" style="color: #222222;">Synology</span> is in a tough spot, they provide devices for SMBs who typically do not have the IT resources of larger companies.  Having come from several SMBs and startups, they also tend to try to save a few bucks by hiring inexperienced help.  I was once at an SMB (less than 300 people) whose accounting department was 9 people.  NINE people because, well the CFO wanted it that way.  IT was 3 total.  We simply couldn't keep up patches on all of our devices.  Thankfully the 3 person team was very smart and we had things setup securely (e.g. no unsecured devices on the public internet).  I've also gone into companies where IT management thought using "P@ssw0rd" for all their device and account passwords was "best practice" because "that's what we used in my Microsoft class."

SMBs need to stop cutting of their noses to spite their face, invest properly in IT so your staff knows how to manage these devices and secure them. (that rant has zero to do with Synology).

If you are using a Synology device please update it ASAP.  Here is the official response from <span class="il" style="color: #222222;">Synology</span>:
<blockquote>
<p style="color: #101010;"><span class="il" style="color: #222222;">Synology</span>® Continues to Encourage Users to Update</p>

<div style="color: #4b4b4b;">

<b>Washington, Bellevue—August 5th, 2014 </b>—We’d like to provide a brief update regarding the recent ransomware called “SynoLocker,” which is currently affecting certain <span class="il" style="color: #222222;">Synology</span> NAS servers.

</div>
<div style="color: #4b4b4b;">We are fully dedicated to investigating this issue and possible solutions. Based on our current observations, this issue only affects <span class="il" style="color: #222222;">Synology</span> NAS servers running some older versions of DSM (DSM 4.3-3810 or earlier), by exploiting a security vulnerability that was fixed and patched in December, 2013. Furthermore, to prevent spread of the issue we have only enabled QuickConnect to secure versions of DSM. At present, we have not observed this vulnerability in DSM 5.0.</div>
<div style="color: #4b4b4b;"></div>
<div style="color: #4b4b4b;">For <span class="il" style="color: #222222;">Synology</span> NAS servers running DSM 4.3-3810 or earlier, and if users encounter any of the below symptoms, we recommend they shutdown their system and contact our technical support team here: <a style="color: #1155cc;" href="https://myds.synology.com/support/support_form.php:" target="_blank">https://myds.<span class="il" style="color: #222222;">synology</span>.<wbr />com/support/support_form.php:</a></div>
<div style="color: #4b4b4b;"></div>
<div style="color: #4b4b4b;">When attempting to log in to DSM, a screen appears informing users that data has been encrypted and a fee is required to unlock data.</div>
<ul style="color: #222222;">
	<li style="color: #4b4b4b;">A process called “synosync” is running in Resource Monitor.</li>
	<li style="color: #4b4b4b;">DSM 4.3-3810 or earlier is installed, but the system says the latest version is installed at Control Panel &gt; DSM Update.</li>
</ul>
<div style="color: #4b4b4b;">For users who have not encountered any of the symptoms stated above, we highly recommend downloading and installing DSM 5.0, or any version below:</div>
<ul style="color: #222222;">
	<li style="color: #4b4b4b;">For DSM 4.3, please install DSM 4.3-3827 or later</li>
	<li style="color: #4b4b4b;">For DSM 4.1 or DSM 4.2, please install DSM 4.2-3243 or later</li>
	<li style="color: #4b4b4b;">For DSM 4.0, please install DSM 4.0-2259 or later</li>
</ul>
<div style="color: #4b4b4b;">DSM can be updated by going to Control Panel &gt; DSM Update. Users can also manually download and install the latest version from our Download Center here: <a style="color: #1155cc;" href="http://www.synology.com/support/download" target="_blank">http://www.<span class="il" style="color: #222222;">synology</span>.com/<wbr />support/download</a>.</div>
<div style="color: #4b4b4b;">If users notice any strange behavior or suspect their <span class="il" style="color: #222222;">Synology</span> NAS server has been affected by the above issue, we encourage them to contact us at <a style="color: #1155cc;" href="mailto:security@synology.com" target="_blank">security@<span class="il" style="color: #222222;">synology</span>.com</a>.</div>
<div style="color: #4b4b4b;">We sincerely apologize for any problems or inconvenience this issue has caused our users. We will keep you updated with the latest information as we address this issue.</div></blockquote>