---
ID: 1062
post_title: >
  How to enable a server port on the Cisco
  UCS Fabric Interconnect
author: Jonathan Frappier
post_date: 2013-06-11 12:53:00
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/how-to-enable-a-server-port-on-the-cisco-ucs-fabric-interconnect/
published: true
dsq_thread_id:
  - "1390354924"
---
<div id="main-content">

Just in case you were wondering, these are the steps necessary to enable a port on a Fabric Interconnect when adding a new UCS chassis (or I guess a rackmount server as well).
<ol>
	<li>Log into Cisco UCS Manager</li>
	<li>Expand Fabric Internconnect A/B (Subordinate) &gt;&gt; Fixed Modules &gt;&gt; Ethernet Ports</li>
	<li>Click on the port you wish to enable and click Reconfigure</li>
	<li>Click Configure as server port, click yes<a href="http://www.virtxpert.com/wp-content/uploads/2013/06/configureasserverport.png"><img class="aligncenter  wp-image-1063" alt="configureasserverport" src="http://www.virtxpert.com/wp-content/uploads/2013/06/configureasserverport.png" width="271" height="378" /></a></li>
	<li>You may receive an alert that the interface is down, followed by a recovery message.</li>
	<li>Click the Show Interface link</li>
	<li>Enter a label to identify the port on the chassis that is connected.</li>
	<li>Repeat for Fabric Interconnect A/B (Primary)\</li>
</ol>
You should now see the port connected.

<a href="http://www.virtxpert.com/wp-content/uploads/2013/06/portup.png"><img class="aligncenter size-full wp-image-1064" alt="portup" src="http://www.virtxpert.com/wp-content/uploads/2013/06/portup.png" width="253" height="442" /></a>

</div>