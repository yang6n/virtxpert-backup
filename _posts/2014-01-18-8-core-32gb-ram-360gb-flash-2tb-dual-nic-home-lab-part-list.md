---
ID: 1857
post_title: >
  8-Core, 32GB RAM, 360GB Flash, 3TB,
  Dual-NIC Home Lab Part List
author: Jonathan Frappier
post_date: 2014-01-18 11:39:29
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/8-core-32gb-ram-360gb-flash-2tb-dual-nic-home-lab-part-list/
published: true
dsq_thread_id:
  - "2139994607"
---
<strong>Updated 3/01/14</strong>:  This is an update to my <a title="Quad-Core, 32GB RAM, 240GB Flash, 2TB, Dual-NIC Home Lab Part List" href="http://www.virtxpert.com/quad-core-32gb-ram-240gb-flash-2tb-dual-nic-home-lab-part-list/" target="_blank">$1200 home lab quad-core build</a>.  This build uses the FX-8320 Vishera processors, which I "think" support RVI as its predecessor, the Zambezi did support it.  The AMD-RVI compatibility list hasn't been updated since 2012, but it's still cheaper than an 8-core Intel.  Assuming my assumption is correct, its only $85 more to do the same build with the FX-8320 and new motherboard.  I've also added a 3rd SSD to this build and swapped out the power supply, not bad for a home lab under $1500.

The part list and brief explanation for the choices, assume price was a factor in all selections since my goal was to make this as inexpensive as possible:

<a href="http://www.newegg.com/Product/Product.aspx?Item=N82E16819113285" target="_blank">CPU:  AMD FX-8320 Vishera</a>:  The FX family supports <a href="http://support.amd.com/en-us/kb-articles/Pages/GPU120AMDRVICPUsHyperVWin8.aspx" target="_blank">AMD-V with RVI</a> and 64-Bit support, however the document hasn't been updated since Vishera processors were released.  Even if it does not support RVI, I should allow me to do ESXi on bare metal and next at least 2 other ESXi VMs inside as well as boot 32-bit VMs inside the ESXi VMs!  RVI would be required to do 64-bit on the nested ESXi hosts.  Also went with an <a href="http://www.newegg.com/Product/Product.aspx?Item=N82E16835106213" target="_blank">aftermarket fan</a> to try and make it a bit more quiet.

<a href="http://www.newegg.com/Product/Product.aspx?Item=N82E16820231569" target="_blank">Memory:  G.Skill 32GB Ripjaw Kit (4x 8GB)</a>:  The G.Skill kits had near flawless ratings on NewEgg, and I have always had good luck with them.  There wasn't much of a price difference anyway I sliced 4x 8GB memory modules so I went for the single kit with the best ratings.

<a href="http://www.newegg.com/Product/Product.aspx?Item=N82E16813131873" target="_blank">Motherboard:  Asus M5A97</a>:  After the TA970 shipped DOA, I ended up swapping it out for an Asus M5A97.  The M5A97 only supports 32GB of RAM, but since I can't seem to find non-ECC 16GB DIMMS I was never going to get to 64GB of RAM that the TA970 supposedly supported anyways.  Th M5A97 supports 3 case fans and the CPU fan, so I could hook up all the fans that ship with the Corsair 230T (something I could not do on the TA970).  The M5A97 still didn't have on USB 3.0 jumpers on the board to connect the front panel USB 3.0 on the case, but I feel a bit better going in with an Asus board.  This board rocks the same Realtek chipset, I'll have notes shortly as I build this to see if I needed to add custom VIBs for it (The <a href="http://www.tinkertry.com/install-esxi-5-5-with-realtek-8111-or-8168-nic/" target="_blank">Realtek 8111 chipset, which "should" work on 5.5 thanks to a little help from Paul Braren</a>).

<a href="http://www.newegg.com/Product/Product.aspx?Item=N82E16814133461">Video:  PNY GeForce 8400</a>:  Cheapest PCI Express 16x 2.0 Card on NewEgg/Amazon and I just need basic video since the TA970 doesn't have it.

<a href="http://www.newegg.com/Product/Product.aspx?Item=N82E16820233404" target="_blank">Flash/SSD:  Corsair Neutron GTX 120GB</a>:  I've had good luck with these drives in laptops, and the stress test that techreport.com did shows them surviving the <a href="http://techreport.com/review/25681/the-ssd-endurance-experiment-testing-data-retention-at-300tb">22TB, 100TB, 200TB and 300TB stress test</a> as well as being <a href="http://techreport.com/review/24841/introducing-the-ssd-endurance-experiment/5" target="_blank">near the top in performance</a>, coming in 2nd only to the Samsung Pro's which had pretty horrible reliability marks in comparison.  The SSD's will be used to front vSphere Flash Read Cache or similar technology (Proximal Data, Pernix etc).

You've got some options on the HDDs.  I went with 4x <a href="http://www.newegg.com/Product/Product.aspx?Item=N82E16822178339" target="_blank">HDD:  Seagate 500GB Hybrid</a> drives doing RAID0 on the MB gets me 2TB usable and 240GB flash.   On the baremetal ESXi host I will run FreeNAS presenting via NFS (or iSCSI if you prefer) to all the hosts to simulate shared storage.  I could have also gone with 3x flash drives for a total of 360GB flash and 1TB 3.5" drives and had 3TB usable in a RAID0.

NIC:  HP NC7170:  This might be a bit of a sore spot for some folks, as these are mostly refurb by now but you can pick the NC7170 dual port NICs up for around 20-25 a piece on <a href="http://www.amazon.com/HP-NC7170-network-adapter-383738-B21/dp/B0009MWAI4" target="_blank">Amazon </a>and <a href="http://www.ebay.com/sch/i.html?_trksid=p2050601.m570.l1313.TR12.TRC2.A0.H0.Xnc7170&amp;_nkw=nc7170&amp;_sacat=0&amp;_from=R40" target="_blank">eBay</a>.  These NICs work out of the gate with ESXi 4.1 and higher (so if you are testing upgrades etc maybe).  If you aren't comfortable with this, you can still go with the <a href="http://www.newegg.com/Product/Product.aspx?Item=N82E16833328022" target="_blank">SYBA Dual</a><span style="text-decoration: underline;"><a href="http://www.newegg.com/Product/Product.aspx?Item=N82E16833328022" target="_blank"> port card</a> </span>and inject the VIB into the ISO (blog post coming soon)

<a href="http://www.newegg.com/Product/Product.aspx?Item=N82E16817182277" target="_blank">Power Supply:  Rosewill RD 600</a>:  Slight oversight on the last power supply, it only had 6 SATA connectors, that might be fine if you go a 3 SSD/3 Hybrid drive but for the same price we get 8 SATA connectors on the Rosewill RD600.

<a href="http://www.newegg.com/Product/Product.aspx?Item=N82E16811139027">Case:  Corsair Graphite 230T</a>:  I've swapped the case on the original build based on the poor quality of the <a title="Thermaltake Chaser A21 Case Review" href="http://www.virtxpert.com/thermaltake-chaser-a21-case-review/">Thermaltake Chaser A21</a>.  The Corsair 230T allows you to mount 4x 3.5" and 4x 2.5" drives at the same time, something I could not do with the Chaser without additional drive bays.  Since this build uses all 2.5" drives you'll still need a couple the ICY 2.5" drive bays, or you may opt to use all of them and give yourself the ability to have 12x 2.5" drives fit in this case (though you'll need a different motherboard or add on SATA controller).

<a href="http://www.newegg.com/Product/Product.aspx?Item=17-994-141" target="_blank">Dual 2.5" Drive Mount for 3.5" bay</a>:  The 230T case can mount 4 2.5" drives and has 4 3.5" bays.  If you went with a 3.5" 1TB Seagate hybrid drive or just a standard 3.5" drive you can skip these, mount the Corsair drives in the existing 2.5" bays and the 3.5" drives in the existing bays.  If you go with all 2.5" drives you will need at least 1 of these.  I bought 4 as I am hoping to eventually cram up to 12 drives into this build; the ICY drive cages will allow me to do that.

SATA Cables 6Gbps/SATA III capable:  The Seagate and Corsair drives did not ship with SATA cables, though the motherboard shipped with 2 so you will need at least 5.  In the 230T case will need a 12" cable.

<a href="http://www.newegg.com/Product/Product.aspx?Item=9SIA13311U9187" target="_blank"><span style="text-decoration: underline;">12x SATA cable pack</span></a>:  You'll end up looping the cables through the back of the case, so having a little extra length on the cables is nice.

<strong>Summary</strong>

For around $1400, you can have an 8-core, 32GB RAM setup which should be capable of building a nice nested ESXi lab.

<iframe src="http://astore.amazon.com/jonathanfrappierblog-20" width="88%" height="1000" frameborder="0" scrolling="no"></iframe>

For those who just want PN's I've listed them below- component: Component (QTY) | Model | NewEgg URL | Price
<div>
<table>
<tbody>
<tr>
<td valign="top" width="154">Component</td>
<td valign="top" width="167">Model</td>
<td valign="top" width="175">URL</td>
<td valign="top" width="95">Price</td>
</tr>
<tr>
<td valign="top" width="154">CPU</td>
<td valign="top" width="167">AMD FX-8320</td>
<td valign="top" width="175">http://goo.gl/VK7K4</td>
<td valign="top" width="95">$159.99</td>
</tr>
<tr>
<td valign="top" width="154">Motherboard</td>
<td valign="top" width="167">ASUS M5A97</td>
<td valign="top" width="175">http://goo.gl/YTJ0s</td>
<td valign="top" width="95">$94.79</td>
</tr>
<tr>
<td valign="top" width="154">Memory</td>
<td valign="top" width="167">G.Skill 32GB X Series</td>
<td valign="top" width="175">http://goo.gl/259fS</td>
<td valign="top" width="95">$299.99</td>
</tr>
<tr>
<td valign="top" width="154">SSD (x2)</td>
<td valign="top" width="167">Corsair GTX 120GB</td>
<td valign="top" width="175">http://goo.gl/PM1sge</td>
<td valign="top" width="95">$129.99</td>
</tr>
<tr>
<td valign="top" width="154">HDD (x4)</td>
<td valign="top" width="167">Seagate ST500LM000</td>
<td valign="top" width="175">http://goo.gl/jwAMR</td>
<td valign="top" width="95">$74.99</td>
</tr>
<tr>
<td valign="top" width="154">NIC (x2)</td>
<td valign="top" width="167">HP NC7170</td>
<td valign="top" width="175">http://goo.gl/yHFWWY</td>
<td valign="top" width="95">$30 to $40</td>
</tr>
<tr>
<td valign="top" width="154">Power Supply</td>
<td valign="top" width="167">Rosewill RD600</td>
<td valign="top" width="175">http://goo.gl/xJZRKA</td>
<td valign="top" width="95">$54.99</td>
</tr>
<tr>
<td valign="top" width="154">2.5” Mount Kits (x3)</td>
<td valign="top" width="167">ICY MB082SP</td>
<td valign="top" width="175">http://goo.gl/NQFsNR</td>
<td valign="top" width="95">$12.99</td>
</tr>
<tr>
<td valign="top" width="154">Case</td>
<td valign="top" width="167">Corsair 230T</td>
<td valign="top" width="175">http://goo.gl/bF1LDm</td>
<td valign="top" width="95">$79.99</td>
</tr>
<tr>
<td valign="top" width="154">USB Cables</td>
<td valign="top" width="167">12 pack</td>
<td valign="top" width="175">http://goo.gl/RsKMxt</td>
<td valign="top" width="95">$28.99</td>
</tr>
<tr>
<td valign="top" width="154">Onboard speaker</td>
<td valign="top" width="167">Generic</td>
<td valign="top" width="175">http://goo.gl/eicnvn</td>
<td valign="top" width="95">$6.00</td>
</tr>
<tr>
<td valign="top" width="154">Video card</td>
<td valign="top" width="167">PNY GeForce 8400</td>
<td valign="top" width="175">http://goo.gl/K1TBoU</td>
<td valign="top" width="95">$27.99</td>
</tr>
</tbody>
</table>
</div>
&nbsp;