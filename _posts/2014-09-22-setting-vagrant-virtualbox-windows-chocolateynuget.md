---
ID: 2610
post_title: >
  Setting up Vagrant and VirtualBox on
  Windows with @chocolateynuget
author: Jonathan Frappier
post_date: 2014-09-22 07:13:08
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/setting-vagrant-virtualbox-windows-chocolateynuget/
published: true
dsq_thread_id:
  - "3042219327"
---
Automate all the things - right?  Well why would I want to manually go to a webpage, download and run the installer when all I need is a few commands to do so.  For those users that have not yet seen Chocolatey, it is a command line package manager/installer; you can get more information from their website <a href="https://chocolatey.org/" target="_blank">here</a> (<a href="https://chocolatey.org/" target="_blank">https://chocolatey.org/</a>), not to dissimilar to yum or apt-get (though probably with less packages).  Installing chocolatey is easy, no need to download anything manually - there is a simple command for that (from an elevated (e.g. run as administrator) Windows command prompt):
<pre>@powershell -NoProfile -ExecutionPolicy unrestricted -Command "iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))" &amp;&amp; SET PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin</pre>
<a href="http://www.virtxpert.com/wp-content/uploads/2014/09/chocolatey-cmd-install.jpg"><img class="size-full wp-image-2612 aligncenter" src="http://www.virtxpert.com/wp-content/uploads/2014/09/chocolatey-cmd-install.jpg" alt="chocolatey-cmd-install" width="843" height="138" /></a>

The command above will download and install all of the required Chocolatey components (note it set your PowerShell Execution Policy to unrestricted, now may be a good time to set it back to something a bit more secure).  Now to install new packages, all you have to do is issue another simple command:
<pre>choco install packagename</pre>
The package name will vary, you can check out all the packages <a href="https://chocolatey.org/packages?sortOrder=package-download-count&amp;page=1&amp;prerelease=False" target="_blank">here</a>.  In my case, I want to install Vagrant and VirtualBox so I can start (trying) to play around with <a href="https://coreos.com/" target="_blank">CoreOS</a> and <a href="https://docker.com/" target="_blank">Docker</a>.  To install VirtualBox...you guessed it

<!--more-->
<pre>choco install virtualbox</pre>
You may receive administrative prompts during installations, quite normal as you would receive those if you were manually downloading the installers separately.  Chocolately will now start downloading the necessary files and install the specified package, in this case VirtualBox

<a href="http://www.virtxpert.com/wp-content/uploads/2014/09/choco-install-virtualbox.jpg"><img class="size-full wp-image-2614 aligncenter" src="http://www.virtxpert.com/wp-content/uploads/2014/09/choco-install-virtualbox.jpg" alt="choco-install-virtualbox" width="844" height="412" /></a>

As you can see here, I now have VirtualBox installed.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/09/virtualbox-installed.png"><img class="size-full wp-image-2616 aligncenter" src="http://www.virtxpert.com/wp-content/uploads/2014/09/virtualbox-installed.png" alt="virtualbox-installed" width="511" height="479" /></a>

&nbsp;

Now I want to install Vagrant, so again a simple
<pre>choco install vagrant</pre>
In this case, I also wanted to demonstrate installing multiple packages in a single line, so as you can see here by putting in an &amp;&amp; between commands it will install the first package, then the second.  For example
<pre>choco install vagrant &amp;&amp; choco install console2</pre>
The &amp;&amp; allows you to run multiple commands back to back, useful if, for example one package has to be installed before the other or you just know that you want multiple packages.  As you can see here I now have both Vagrant and Console installed.  Note that Vagrant was not added to my path, so to be able to run vagrant from any directory I manually added this in.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/09/choco-install-vagrant-console2.jpg"><img class="alignleft size-full wp-image-2620" src="http://www.virtxpert.com/wp-content/uploads/2014/09/choco-install-vagrant-console2.jpg" alt="choco-install-vagrant-console2" width="1475" height="719" /></a>

&nbsp;

So, now with really 3 simple commands, I am ready to use Vagrant to stand up a VM in VirtualBox.  Two more commands and I am good to go:

From the directory you would like to create your vagrantfile in
<pre>vagrant init hashicorp/preciese32</pre>
This will create your vagrant file, you can find a list of publicly available boxes ready for download at <a href="https://vagrantcloud.com/discover/featured" target="_blank">https://vagrantcloud.com/discover/featured</a> .Next,
<pre>vagrant up</pre>
In a few minutes, you'll have a new VM in VirtualBox!  You now have the foundation in place to start using Vagrant.

<a href="http://www.virtxpert.com/wp-content/uploads/2014/09/vagrant-up-ubuntu.jpg"><img class="size-full wp-image-2626 aligncenter" src="http://www.virtxpert.com/wp-content/uploads/2014/09/vagrant-up-ubuntu.jpg" alt="vagrant-up-ubuntu" width="847" height="323" /></a>

<a href="http://www.virtxpert.com/wp-content/uploads/2014/09/vagrant-up-virtualbox-vm.jpg"><img class="size-full wp-image-2623 aligncenter" src="http://www.virtxpert.com/wp-content/uploads/2014/09/vagrant-up-virtualbox-vm.jpg" alt="vagrant-up-virtualbox-vm" width="1174" height="546" /></a>

&nbsp;