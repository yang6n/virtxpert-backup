---
ID: 1497
post_title: 'How to &#8220;Erase&#8221; a virtual tape in EMC Networker'
author: Jonathan Frappier
post_date: 2013-11-07 09:20:38
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/erase-virtual-tape-emc-networker/
published: true
dsq_thread_id:
  - "1944802839"
---
So maybe its just been a while since I used BackupExec, but pretty sure I "erased" tapes in the application.  Well, in Networker you "label" a tape to erase it.  Since I am not a full time Networker Engineer/Administrator this wasn't immediately obvious so if you are running into the same thing, here is how to erase a tape.  In this scenario I am backing up to a Virtual Tape Library (VTL) but should be similar for physical tapes.

To erase the tape, do the following:
<ul>
	<li>Log into Network Management Console (NMC)</li>
	<li>Click on the Networker server node then double click Networker in the main display pane</li>
	<li>A new window will launch</li>
	<li>Expand libraries and select your tape library</li>
	<li>Click on any of the column headers to sort, Pool or Last Accessed Time</li>
	<li>Find a tape marked as recyclable (generally the Last Access time for these tapes should be more than your retention policy).</li>
	<li>Right click the tape and select Label</li>
	<li>Change the target media pool to the appropriate pool</li>
	<li>Uncheck prompt to overwrite label and click OK</li>
	<li>You can select multiple tapes at once to re-label in bulk</li>
</ul>
Pretty easy once you know, and knowing is half the battle!