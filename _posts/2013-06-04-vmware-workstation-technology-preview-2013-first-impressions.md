---
ID: 1021
post_title: 'VMware Workstation Technology Preview 2013 &#8211; First Impressions'
author: Jonathan Frappier
post_date: 2013-06-04 12:39:49
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/vmware-workstation-technology-preview-2013-first-impressions/
published: true
dsq_thread_id:
  - "1359638750"
---
<em>Updated 6/5/13</em>

The VMware Workstation 2013 Technology Preview is available for download at the VMTN forums (<a href="http://communities.vmware.com/community/vmtn/beta/workstation_2013">http://communities.vmware.com/community/vmtn/beta/workstation_2013</a>).  Among the many improvements from Workstation 9, and those VMware is specifically looking for feedback on includes:
<ul>
	<li>Creating and running Virtual Machines using the latest operating systems - Window 8.1, Ubuntu 13.04, Fedora 18 etc.</li>
	<li>Running Restricted virtual machines with an expiration date</li>
	<li>Converting physical machines to virtual machines</li>
	<li>Graphics performance and multi-monitor support</li>
	<li>Performance of Virtual Machines running up to 16 vCPUs</li>
	<li>General stability, application compatibility and usability</li>
</ul>
<strong>Installation</strong>

The Windows installation as I would expect in 2013 (the year not the product version) was smooth and went off without a hitch.  The UI is unchanged from version 9, so those wanting something prettier to look aren't going to get that in the tech preview.  After the installation, my first task was to install Ubuntu 13.04 - after all VMware did ask for that first!  I created a typical VM, selecting to install the OS later with Ubuntu 64-bit as the version and gave myself 2GB of RAM.  Once the VM was created I assigned by Ubuntu ISO to the CD drive and went off to install land.

A few notes during the install that I think are worth mentioning, mostly because I don't recall these items from Workstation 9.
<ul>
	<li>During the power on process, I received a notification about several devices that I could connect to my VM including my laptop webcam and smart card reader.  I mention this only because I ran several Ubuntu VMs in Workstation 9 and never received a notification; a nice touch to know what you can add.</li>
	<li>Ubuntu was able to detect the network card from my laptop without VMware Tools being installed, this allowed me to download updates if I chose during the installation - this could be just as much a new OS with drivers available as it is Workstation.</li>
	<li>I am able to freely move the mouse between my VM window and host OS (Windows 7 64-bit) again without VMware Tools installed.</li>
</ul>
Now I did have a hang up after the installation finished, again not sure if this is Ubuntu or Workstation but the VM hung at "*Asking all remaining processes to terminate..." but the VM started right up after hitting the power button.  The VM Tools still comes packaged as a handy tar/gz file (I blame Linux for this).  Once extracted, I ran the following command to set my super user password<!--more-->
<pre>sudo passwd</pre>
Now that the password was updated I ran
<pre>sudo ./vmware-install.pl</pre>
Now interestingly enough, there was already an /etc/vmware-tools directory.  I followed <a href="http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&amp;cmd=displayKC&amp;externalId=1013159" target="_blank">KB 1013159</a> and removed the 'locations' file and re-ran the installer.  After being prompted to overwrite several files (I probably should have removed the whole /etc/vmware-tools folder since I didn't put it there) the install ran and told me it completed, however Ubuntu believed there was a problem with the install.  I reported the problem but also verified that VMware Tools WAS in fact running by running
<pre> initctl list</pre>
Thank you <a href="http://www.testools.net/2013/01/install-vmware-tools-in-ubuntu-easy-way.html" target="_blank">testtools.net</a>, coming from a Fedora/RedHat world I had been wondering what the chkconfig --list equivalent was.

<em>Update</em>

Now that my VM is running, I wanted to test running my VM across multiple monitors.  To enable this, click on the 'Cycle Multiple Monitors' button in the toolbar as pictured below.

<a href="http://www.virtxpert.com/wp-content/uploads/2013/06/multipledisplaysvmwareworkstation.png"><img class="aligncenter size-full wp-image-1043" alt="multipledisplaysvmwareworkstation" src="http://www.virtxpert.com/wp-content/uploads/2013/06/multipledisplaysvmwareworkstation.png" width="690" height="54" /></a>

&nbsp;

Once enabled, running my Ubuntu VM on multiple monitors has been just as seamless as my laptop is with Windows nativity on my laptop.

<strong>Conclusion</strong>

Yup, it works.  VMware Workstation has certainly been solid for me for many years, now its time to beat on this VM and make sure its still stable!  Sorry this morphed into a Ubuntu post at the end!