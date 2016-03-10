---
ID: 3817
post_title: >
  vRealize Application Services Home Lab
  Upgrade
author: Jonathan Frappier
post_date: 2015-05-28 08:00:07
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vrealize-application-services-home-lab-upgrade/
published: true
dsq_thread_id:
  - "3800756296"
---
As I did in the previous post with vRealize Automation, it is now time to upgrade vRealize Application services, again based on <a href="http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&amp;cmd=displayKC&amp;externalId=2109760" target="_blank">KB2109760</a> this would be the second item to upgrade before upgrading vCenter with embedded SSO. Not that it is horribly difficult, but there is no management interface as we had with the vRealize Automation appliance so we will have to download the files, copy them to the appliance and start the upgrade.

Before you being, ensure you can log into the console of the application services virtual appliance as root and SSH as darwin_user. If you are unable to SSH as darwin_user follow the directions <a href="http://pubs.vmware.com/vra-62/index.jsp#com.vmware.vra.appservices.using.doc/GUID-337196A4-4929-4CAD-B572-4A0E74046CC5.html" target="_blank">here</a> to enable the darwin_user account. Now, download the <strong id="aui_3_2_0_1337">VMware vRealize Automation Application Services 6.2.0 upgrade installer </strong>from downloads.vmware.com. Once the file has been download, copy the .tgz file to the appliance, for example if you are using Windows you might use WinSCP to copy the file. Once the file is on the system, SSH to the appliance and navigate to the directory you placed the file in. For example here you can see the tgz file in the 62-upg folder I created.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/05/apps-upg-step1.png"><img class="aligncenter size-full wp-image-3819" src="http://www.virtxpert.com/wp-content/uploads/2015/05/apps-upg-step1.png" alt="apps-upg-step1" width="674" height="422" /></a>

Next, untar the file by running tar xvfz ApplicationServices-6.2.0.0-2299597_Upgrade_Installer.tgz (or the appropriate build number based on your download). Once all the files have been extracted, you should have an install.sh file ready to run (no need to chmod to be executable). Run the install as root by running sudo ./install.sh (or sudo -su, then ./install.sh as the VMware docs state)

<a href="http://www.virtxpert.com/wp-content/uploads/2015/05/apps-upg-step2.png"><img class="aligncenter size-full wp-image-3822" src="http://www.virtxpert.com/wp-content/uploads/2015/05/apps-upg-step2.png" alt="apps-upg-step2" width="675" height="422" /></a>

Type Y to start the upgrade and the rest is scripted for you. Once the installer finishes, restart the vRealize Automation appliance and Application Services appliance, when the appliance reboots, you should be able to log in at https://{appsservicesURL}:8443/darwin/org/{vratenant} - for example https://vxprt-apps01.vxprt.local:8443/darwin/org/vsphere.local

<a href="http://www.virtxpert.com/wp-content/uploads/2015/05/apps-upgrade-ui.png"><img class="aligncenter size-full wp-image-3826" src="http://www.virtxpert.com/wp-content/uploads/2015/05/apps-upgrade-ui.png" alt="apps-upgrade-ui" width="985" height="612" /></a>

You are now on Application Services 6.2 (as seen in the lower right corner in the above screenshot).