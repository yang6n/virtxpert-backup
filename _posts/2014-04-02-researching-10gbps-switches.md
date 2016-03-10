---
ID: 2121
post_title: Researching 10Gbps switches
author: Jonathan Frappier
post_date: 2014-04-02 10:24:50
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/researching-10gbps-switches/
published: true
dsq_thread_id:
  - "2580879732"
---
Recently I've had to research 10Gbps switches, not being an everyday network person I'd typically just ask Cisco and be done with it, after all as the saying goes no one ever gets fired for buying Cisco but wanted to look into what other vendors have for options.  The purpose of the blog post is not to suggest this is the end all be all, but provide some basic research to others and to open conversation as to anything I might be missing, or considerations I need to look at that I've not (again I'm not a full time network person).

This particular use case is for a small data center to support new servers using 10Gbps Ethernet for shared storage and networking.

<strong>Assumptions</strong>:
<ul>
	<li>Each physical server will have no more than two 10Gbps interfaces</li>
	<li>Future growth will likely not exceed 20 total physical servers for a total of 40 required ports.</li>
	<li>The 10Gbps switch will handle L2 10Gbps traffic</li>
	<li>Outbound VM network traffic will be routed to an existing core switch and firewall</li>
	<li>Provide enough ports for future physical host considerations</li>
	<li>Existing equipment with only 1Gbps links will stay connected to existing switches</li>
</ul>
To support redundancy I would like to have at least two physical switches to connect one each of the two 10Gbps server ports.  The expected physical layout would be similar to the image below:
<p style="text-align: center;"><a href="http://www.virtxpert.com/wp-content/uploads/2014/04/10Gbps-with-existing-network.jpg"><img class="aligncenter  wp-image-2123" alt="10Gbps with existing network" src="http://www.virtxpert.com/wp-content/uploads/2014/04/10Gbps-with-existing-network.jpg" width="576" height="432" /></a></p>
<p style="text-align: left;">Raw technical specifications were just about equal across the board, most of the switches to support the size of the deployment needed all had roughly the same throughput, PPS and MAC table support.  Cost was also fairly equal (note cost was pulled from public reseller sites, you should check with your reseller or VAR on pricing).  Here is what I looked at (crowd sourced list via Twitter; thank you Michael Davis, Rob Nelson, Ed Swindelles, Robert Novak):</p>

<ol>
	<li> Number of ports (and type)</li>
	<li>Available port speed</li>
	<li>Number of uplinks (and type)</li>
	<li>Available uplink speed</li>
	<li>Throughput</li>
	<li>Packets per second</li>
	<li>Latency</li>
	<li>CPU/Memory</li>
	<li>Buffers</li>
	<li>Port licensing</li>
	<li>Cable compatibility</li>
	<li>Warranty</li>
	<li>First year cost</li>
	<li>SFP cost</li>
	<li>Maintenance cost</li>
</ol>
A few things to note that aren’t listed here; all switches support LAG groups, the number of groups and group members vary generally between 16 and 32 ports per LAG group.  The SuperMicro switch supported 8 per LAG.

Thanks to <a href="http://twitter.com/bvdlatisit">@bvdlatisit</a> for suggesting the 3524 (and thus 3548 - I'll check those out and update this post shortly)
<table width="1606" border="0" cellspacing="0" cellpadding="0"><colgroup> <col width="88" /> <col width="162" /> <col width="44" /> <col width="96" /> <col width="66" /> <col width="72" /> <col width="90" /> <col width="56" /> <col width="82" /> <col width="92" /> <col width="80" /> <col width="66" /> <col width="56" /> <col width="84" /> <col width="76" /> <col width="66" /> <col width="80" /> <col width="106" /> <col width="144" /> </colgroup>
<tbody>
<tr>
<td width="88" height="21">Manufacturer</td>
<td width="162">Model</td>
<td width="44">Size</td>
<td width="96">Redundant PS</td>
<td width="66"># of Ports</td>
<td width="72">Port Type</td>
<td width="90">Port Speed</td>
<td width="56">Uplinks</td>
<td width="82">Uplink Type</td>
<td width="92">Uplink Speed</td>
<td width="80">Throughput</td>
<td width="66">PPS</td>
<td width="56">Latency</td>
<td width="84">Buffers</td>
<td width="76">MAC Table</td>
<td width="66">Warranty</td>
<td width="80">Switch Cost</td>
<td width="106">Twinax 5M Cost</td>
<td width="144">Product Link</td>
</tr>
<tr>
<td height="20">Cisco</td>
<td>3064X</td>
<td>1U</td>
<td>Yes</td>
<td>48</td>
<td>SFP+</td>
<td>Up to 10Gbps</td>
<td>4</td>
<td>QSFP+</td>
<td>4x10+40Gbps</td>
<td>1.28Tbps</td>
<td>950 mpps</td>
<td>?</td>
<td>9 MB shared</td>
<td>128000</td>
<td>1 Year</td>
<td>18500</td>
<td>280</td>
<td>http://goo.gl/7dUrQG</td>
</tr>
<tr>
<td height="20">Cisco</td>
<td>3064T</td>
<td>1U</td>
<td>Yes</td>
<td>48</td>
<td>RJ-45</td>
<td>Up to 10Gbps</td>
<td>4</td>
<td>QSFP+</td>
<td>4x10+40Gbps</td>
<td>1.28Tbps</td>
<td>950 mpps</td>
<td>1.41 us</td>
<td>9 MB shared</td>
<td>128000</td>
<td>1 Year</td>
<td>18000</td>
<td>280</td>
<td>http://goo.gl/7dUrQG</td>
</tr>
<tr>
<td height="20">Arista</td>
<td>7124SX</td>
<td>1U</td>
<td>Yes</td>
<td>24</td>
<td>SFP+</td>
<td>Up to 10Gbps</td>
<td>0</td>
<td>--</td>
<td>--</td>
<td>480Gbps</td>
<td>360 mpps</td>
<td>500 ns</td>
<td>?</td>
<td>?</td>
<td>1 Year</td>
<td>16500</td>
<td>135</td>
<td>http://goo.gl/B34DE7</td>
</tr>
<tr>
<td height="20">Arista</td>
<td>7050S-64</td>
<td>1U</td>
<td>Yes</td>
<td>52</td>
<td>SFP+</td>
<td>Up to 10Gbps</td>
<td>4</td>
<td>QSFP+</td>
<td>4x10+40Gbps</td>
<td>1.28Tbps</td>
<td>960 mpps</td>
<td>1.2 us</td>
<td>9 MB shared</td>
<td>128000</td>
<td>1 Year</td>
<td>26000</td>
<td>135</td>
<td>http://goo.gl/Pu9U8C</td>
</tr>
<tr>
<td height="20">Juniper</td>
<td>QFX3500-48SQ-ACRB</td>
<td>1U</td>
<td>Yes</td>
<td>48</td>
<td>SFP+ / SFP</td>
<td>Up to 10Gbps</td>
<td>4</td>
<td>QSFP+</td>
<td>4x10+40Gbps</td>
<td>1.28Tbps</td>
<td>960 mpps</td>
<td>&lt; 1 us</td>
<td>9 MB shared</td>
<td>120000</td>
<td>1 Year</td>
<td>25000</td>
<td>170</td>
<td>http://goo.gl/pqH4Bc</td>
</tr>
<tr>
<td height="20">Extreme</td>
<td>X670V-48x - VIM4-40G4X</td>
<td>1U</td>
<td>Yes</td>
<td>48</td>
<td>SFP+</td>
<td>Up to 10Gbps</td>
<td>4</td>
<td>QSFP+</td>
<td>4x10+40Gbps</td>
<td>1.28Tbps</td>
<td>952 mpps</td>
<td>&lt; 1 us</td>
<td>9 MB shared</td>
<td>128000</td>
<td>1 Year</td>
<td>21000</td>
<td>?</td>
<td>http://goo.gl/0oSlEn</td>
</tr>
<tr>
<td height="20">Extreme</td>
<td>X670V-48x</td>
<td>1U</td>
<td>Yes</td>
<td>48</td>
<td>SFP+</td>
<td>Up to 10Gbps</td>
<td>0</td>
<td>--</td>
<td>--</td>
<td>960Gbps</td>
<td>714 mpps</td>
<td>&lt; 1 us</td>
<td>9 MB shared</td>
<td>128000</td>
<td>1 Year</td>
<td>18000</td>
<td>?</td>
<td>http://goo.gl/0oSlEn</td>
</tr>
<tr>
<td height="20">Supermicro</td>
<td>X3348SR</td>
<td>1U</td>
<td>Yes</td>
<td>48</td>
<td>SFP+</td>
<td>Up to 10Gbps</td>
<td>4</td>
<td>QSFP+</td>
<td>4x10+40Gbps</td>
<td>1.28Tbps</td>
<td>?</td>
<td>?</td>
<td>?</td>
<td>?</td>
<td>1 Year</td>
<td>13365</td>
<td>156</td>
<td>http://goo.gl/bbme0B</td>
</tr>
<tr>
<td height="20">Dell</td>
<td>N4064</td>
<td>1U</td>
<td>Yes</td>
<td>48</td>
<td>SFP+</td>
<td>Up to 10Gbps</td>
<td>4</td>
<td>QSFP+</td>
<td>4x10+40Gbps</td>
<td>1.28Tbps</td>
<td>952 mpps</td>
<td>?</td>
<td>9 MB shared</td>
<td>?</td>
<td>Lifetime</td>
<td>16825</td>
<td>156</td>
<td>http://goo.gl/XcEFuw</td>
</tr>
<tr>
<td height="20">HP</td>
<td>5900AF</td>
<td>1U</td>
<td>Yes</td>
<td>52</td>
<td>SFP+</td>
<td>Up to 10Gbps</td>
<td>4</td>
<td>QSFP+</td>
<td>4x10+40Gbps</td>
<td>1.28Tbps</td>
<td>952 mpps</td>
<td>&lt; 1.5 us</td>
<td>9 MB shared</td>
<td>128000</td>
<td>1 Year</td>
<td>24200</td>
<td>?</td>
<td>http://goo.gl/ptXgWQ</td>
</tr>
</tbody>
</table>
<strong>Summary</strong>

At this point, I seem to have circled back to Cisco, specifically the 3064X which was also suggested by a re-seller I spoke to about pricing.  While the SuperMicro was the least expensive, not being a network person I'm not comfortable taking on the support of it directly (if some vendor slapped their logo on it and supported it directly that's fine) and while Arista seems to be the new hotness, I also don't have an unlimited budget so comparing features and price, Cisco seems to be it.  If you've deployed 10Gbps switches, what do you think of this information?  What did I miss? And what have your experiences been?

<strong>Definitions</strong>:

SFP+:   Enhanced Small Form-Factor Pluggable

QSFP+:  Quad SFP

ns:   nanosecond (http://goo.gl/M9LxEM)

us:  microsecond (http://goo.gl/M9LxEM)