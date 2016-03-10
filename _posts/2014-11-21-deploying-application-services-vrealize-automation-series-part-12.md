---
ID: 3109
post_title: 'Deploying Application Services &#8211; vRealize Automation Series Part 12'
author: Jonathan Frappier
post_date: 2014-11-21 08:30:56
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/deploying-application-services-vrealize-automation-series-part-12/
published: true
dsq_thread_id:
  - "3248563751"
---
<p>[display-posts category="vRA Home Lab" display-posts posts_per_page="15"]</p>
<p>One of my goals in the #vDM30in30 challenge was to expand my comfort level with vRealize Automation / vCloud Automation Center and Application Services / Application Director.  To that end, it's time to deploy the AppS appliance.  In vRealize Automation 6.1, Application Services (formerly Application Director) became a "component" of vRa.  I guess what the marketing department meant by "component" was that it is a completely separate virtual appliance with its own management UI and integration with vRealize Automation :)</p>
<p>In 6.0, like the vCloud Automation Center appliance, the initial OVF import was important.  While there are documented ways to manage the network settings that "should" allow you to make changes, I found that the changes were not always persistent so again I am careful here and probably carrying with me some bad memories.  Log into the vSphere Web Client, if you are running your VMs on the VMware Workstation NAT'd network, do so from your DC.</p>
<ul>
<li>Click on vCenter &gt;&gt; Hosts and Clusters</li>
<li>Right click on your cluster and select Deploy OVF Template, if prompted click allow</li>
<li>Browse for the location to your Application Services OVF and click Next</li>
<li>Click Next, Accept, and Next</li>
<li>Name your appliance, I'll be keeping with my convention and use vxprt-apps01, and select the datacenter or folder you want to deploy to</li>
<li>Select the datastore, then ensure you have selected Thin Provision</li>
<li>Connect to the appropriate port, change the IP allocation pull down to Static and fill in the DNS, Gateway and Netmask fields;  click Next</li>
<li>Enter the IP address for the appliance and click Finish</li>
<li>While the appliance is being deploy, open DNS manager and create an A record in both the forward and reverse lookup zones.</li>
<li>If, like me you are limited to lab resources, change the amount of memory for the virtual machine to 3 or 4GB.  I changed mine to 3GB and it seems to be working fine.</li>
<li>Once the deployment finishes, power on the virtual machine and open the VMRC; you will see a prompt to enter the serial number for Application Services:</li>
</ul>
<p>[caption id="attachment_3120" align="aligncenter" width="1005"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/vra-apps-boot-serial-number.png"><img class="size-full wp-image-3120" src="http://www.virtxpert.com/wp-content/uploads/2014/11/vra-apps-boot-serial-number.png" alt="vRealize Automation / vCloud Automation Center Application Services Serial Number via Console" width="1005" height="537" /></a> vRealize Automation / vCloud Automation Center Application Services Serial Number via Console[/caption]</p>
<ul>
<li>Enter your serial number and press the enter key on your keyboard</li>
<li>Enter the new OS root password when prompted (you can ignore the errors about weak passwords...not that mine is weak ... :)</li>
<li>Enter the OS darwin_user account password</li>
<li>The appliance will configure its initial configuration process - now would be a good time to also update your host file if necessary on your workstation.  Services can take awhile to start since I dropped the memory of the system</li>
<li>You will be asked if you want to use this instance for a migration from 6.0.1, in our case the answer is N</li>
<li>Next, provide your vRealize Automation / vCloud Automation Center Server URL; in my case https://vxprt-vcac01.vxprt.local</li>
</ul>
<p>[caption id="attachment_3125" align="aligncenter" width="1003"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/vra-apps-boot-vcac-registration-url.png"><img class="size-full wp-image-3125" src="http://www.virtxpert.com/wp-content/uploads/2014/11/vra-apps-boot-vcac-registration-url.png" alt="vRealize Automation / vCloud Autoamtion Center Application Services registration" width="1003" height="334" /></a> vRealize Automation / vCloud Autoamtion Center Application Services registration[/caption]</p>
<ul>
<li>Enter administrator@vsphere.local when prompted for the administrator username</li>
<li>After a few moments you should get a prompt saying Registration is successful</li>
<li>You will now be asked if you want to setup Out-Of-Box sample content; I am selecting Yes</li>
<li>Next, provide the Tenant Name - in my case vsphere.local as I am using the default tenant for my lab</li>
<li>Here, we need to switch back to the vRealize Automation web console for a moment as we need to give a user the appropriate roles to import content.</li>
<li>Log in as tenantadmin, click on Administration &gt;&gt; Users; search for one of your Business Group admins, in my case either Rick or Luke, type in their name in the search box and click on the user when it appears</li>
<li>Give the user the top 4 roles Application Architect, Catalog Administrator, Cloud Administrator, and Publisher/Deployer (probably don't need all, but can't decipher what specifically it needs from the documentation)</li>
</ul>
<p>[caption id="attachment_3127" align="aligncenter" width="1041"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/vra-application-permissions.png"><img class="size-full wp-image-3127" src="http://www.virtxpert.com/wp-content/uploads/2014/11/vra-application-permissions.png" alt="Assing Application Services permissions in vRealize Automation / vCloud Automation Center" width="1041" height="289" /></a> Assing Application Services permissions in vRealize Automation / vCloud Automation Center[/caption]</p>
<ul>
<li>Click Update; the user luke now has all Application Services related roles</li>
<li>Switch back to the VMRC; enter luke as the username and then the password password</li>
<li>Enter the business group that should have access to the sample content, in my case StarWars</li>
</ul>
<p>[caption id="attachment_3128" align="aligncenter" width="1003"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/vra-apps-import-out-of-box-content.png"><img class="size-full wp-image-3128" src="http://www.virtxpert.com/wp-content/uploads/2014/11/vra-apps-import-out-of-box-content.png" alt="VMware Application Services importing out of box content for business group" width="1003" height="252" /></a> VMware Application Services importing out of box content for business group[/caption]</p>
<ul>
<li>Once complete you should see that you can also import out of box content for other tenants again by running /home/darwin/tools/import_oob_content.sh</li>
<li>Press any key to continue</li>
<li>Enter the new password for the Application Services admin account (I know a lot of accounts huh)</li>
<li>Setup will finish boot until you see the typical VMware appliance console</li>
<li>Open a web browser and navigate to https://vxprt-apps01.vxprt.local:8443/darwin/org/vsphere.local</li>
<li>You can log in as any tenant user that you configured; for example try luke</li>
</ul>
<p>[caption id="attachment_3130" align="aligncenter" width="1032"]<a href="http://www.virtxpert.com/wp-content/uploads/2014/11/apps-login.png"><img class="size-full wp-image-3130" src="http://www.virtxpert.com/wp-content/uploads/2014/11/apps-login.png" alt="VMware vRealize Automation / vCloud Automation Center Application Sevices web console" width="1032" height="683" /></a> VMware vRealize Automation / vCloud Automation Center Application Sevices web console[/caption]</p>
<p>That is the basic deployment of VMware vRealize Automation / vCloud Automation Center Application Services - up next we have a bit more configuration to do to make the Application Services Available as a catalog item in the vRealize Automation / vCloud Automaton Center catalog.</p>
<p>&nbsp;</p>