---
ID: 1067
post_title: >
  Cannot Launch UCS KVM Cannot run program
  C:\\Program
author: Jonathan Frappier
post_date: 2013-06-12 11:24:26
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/cannot-launch-ucs-kvm-cannot-run-program-cprogram/
published: true
dsq_thread_id:
  - "1393824862"
---
First a huge thank you to everyone, if you are reading this or if you are someone who has never heard my name but participates in forums for whatever your passion.  Last week I was trying to access the virtual KVM for a UCS server, in typical Cisco/Java fashion is quite specific to a version of Java and if you dont have it, you will have problems.

The error is:  Cannot run program "C:\\Program":  Create Process error=2, the system could not find the file specified.

<a href="http://www.virtxpert.com/wp-content/uploads/2013/06/error.png"><img class="aligncenter size-full wp-image-1068" alt="error" src="http://www.virtxpert.com/wp-content/uploads/2013/06/error.png" width="762" height="473" /></a>

Fortunately it was an easy <del>"fix"</del> workaround by simply launching the KVM from the main UCS login window versus trying to launch from inside UCS manager.  The workaround was found thanks to the Cisco Community forums, which I find myself constantly having open in addition to the VMware and EMC communities and TweetDeck.  The post, if you need to check on it, can be found here:  <a href="https://supportforums.cisco.com/thread/2212263">https://supportforums.cisco.com/thread/2212263</a>

Go to your UCS Manager login page and click Launch KVM Manager

<a href="http://www.virtxpert.com/wp-content/uploads/2013/06/kvmlaunch.png"><img class="aligncenter size-full wp-image-1069" alt="kvmlaunch" src="http://www.virtxpert.com/wp-content/uploads/2013/06/kvmlaunch.png" width="809" height="309" /></a>

You could also chose to uninstall Java and re-install it to a directory with no spaces in the name, for example c:\jre7.  Be careful to document all your specific Java requirements for various applications so you re-install the correct versions.

&nbsp;