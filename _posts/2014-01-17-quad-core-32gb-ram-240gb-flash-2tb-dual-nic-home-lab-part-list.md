---
ID: 1849
post_title: >
  Quad-Core, 32GB RAM, 240GB Flash, 2TB,
  Dual-NIC Home Lab Part List
author: Jonathan Frappier
post_date: 2014-01-17 22:44:12
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/quad-core-32gb-ram-240gb-flash-2tb-dual-nic-home-lab-part-list/
published: true
dsq_thread_id:
  - "2137322348"
---
<strong>Updated 2/1/14:  </strong>Looking to put the home lab back together, and rather than using multiple hosts, going for a single beefy box where I can do some virtual inception (aka nested ESXi).  My goal was to build this under $1000, but couldn't quite pull that off though I came pretty close with a $1194 price tag (before tax and shipping).

The part list and brief explanation for the choices, assume price was a factor in all selections since my goal was to make this as inexpensive as possible:

<a href="http://www.newegg.com/Product/Product.aspx?Item=N82E16819113328" target="_blank">CPU:  AMD Trinity X4 Quad Core @ 3.4GHz</a>:  The Trinity family supports <a href="http://support.amd.com/en-us/kb-articles/Pages/GPU120AMDRVICPUsHyperVWin8.aspx" target="_blank">AMD-V with RVI</a> and 64-Bit support.  This should allow me to do ESXi on bare metal and next at least 2 other ESXi VMs inside as well as boot VMs inside the VMs!  Also went with an <a href="http://www.newegg.com/Product/Product.aspx?Item=N82E16835106213" target="_blank">aftermarket fan</a> to try and make it a bit more quiet.

<a href="http://www.newegg.com/Product/Product.aspx?Item=N82E16820231569" target="_blank">Memory:  G.Skill 32GB Ripjaw Kit (4x 8GB)</a>:  The G.Skill kits had near flawless ratings on NewEgg, and I have always had good luck with them.  There wasn't much of a price difference anyway I sliced 4x 8GB memory modules so I went for the single kit with the best ratings.

<a href="http://www.newegg.com/Product/Product.aspx?Item=N82E16813128659" target="_blank">Motherboard:  GIGABYTE GA-F2A88XM-D3H</a>:  The Gigabyte motherboard, first and foremost is compatible with the <a href="http://www.gigabyte.us/support-downloads/cpu-support-popup.aspx?pid=4716" target="_blank">X4 750K CPU</a>, offers support for up to 64GB of memory (<em>Apologies, thought I saw a 16x1 module, but as Hoss pointed out, those are all ECC</em>  - <del><a href="http://www.crucial.com/store/listmodule/DDR3/~240-pin%20DIMM~~0~~16384~/list.html" target="_blank">16GB modules are at Crucial for $200 a piece</a></del>), has 8x 6Gbs SATA ports and built in RAID 0/1/5/10/JBOD support.  The NIC appears to use a <a href="http://www.tinkertry.com/install-esxi-5-5-with-realtek-8111-or-8168-nic/" target="_blank">Realtek 8111 chipset, which "should" work on 5.5 thanks to a little help from Paul Braren</a>.  I couldn't actually find a specific mention of the chipset version on the Gigabyte website, but it links to a download for the 8111 driver so...fingers crossed.  In any case I've added a 2nd 2-port NIC.

<a href="http://www.newegg.com/Product/Product.aspx?Item=N82E16820233404" target="_blank">Flash/SSD:  Corsair Neutron GTX 120GB</a>:  I've had good luck with these drives in laptops, and the stress test that techreport.com did shows them surviving the <a href="http://techreport.com/review/25681/the-ssd-endurance-experiment-testing-data-retention-at-300tb">22TB, 100TB, 200TB and 300TB stress test</a> as well as being <a href="http://techreport.com/review/24841/introducing-the-ssd-endurance-experiment/5" target="_blank">near the top in performance</a>, coming in 2nd only to the Samsung Pro's which had pretty horrible reliability marks in comparison.  The SSD's will be used to front vSphere Flash Read Cache or similar technology (Proximal Data, Pernix etc).

<a href="http://www.newegg.com/Product/Product.aspx?Item=N82E16822178339" target="_blank">HDD:  Seagate 500GB Hybrid</a>:  Because space, price and 4 drives doing RAID0 on the MB gets me 2TB usable, though I'll likely do 2x 2-drive RAID0 at 1TB each for 2 datastores.  On the baremetal ESXi host I will run FreeNAS presenting via NFS (or iSCSI if you prefer) to all the hosts to simulate shared storage.  These 2.5" drives also require about half the power draw of the 1TB 3.5" drives.

<a href="http://www.newegg.com/Product/Product.aspx?Item=N82E16833328022">NIC:  SYBA Dual Port NIC</a>:  Another Realtek 8111 chipset and with questions on the onboard NIC version still out there, having multiple physical NIC's can't be bad anyways with ESXi, especially if you opt to use multiple versions of these boxes for your lab instead nesting.  Ryan Birk has an article <a href="http://www.ryanbirk.com/need-a-cheap-vmware-esxi-dual-port-lab-nic/" target="_blank">here</a>, and all the comments seem to suggest this works on 5.5.

<a href="http://www.newegg.com/Product/Product.aspx?Item=N82E16817152041" target="_blank">Power Supply:  600W RAIDMAX</a>:  Probably a bit overkill with the lower power drives, even though the CPU is the 100W variety.  This has 6 SATA power connectors to support the 2 SSDs and 4 SSHD Hybrids.  This happens to be on sale right now, putting it in the ballpark of lower powered PS's, if the sale ends I'll shop around for a different PSU.

<a href="http://www.newegg.com/Product/Product.aspx?Item=N82E16811139027">Case:  Corsair Graphite 230T</a>:  I've swapped the case on the original build based on the poor quality of the <a title="Thermaltake Chaser A21 Case Review" href="http://www.virtxpert.com/thermaltake-chaser-a21-case-review/">Thermaltake Chaser A21</a>.  The Corsair 230T allows you to mount 4x 3.5" and 4x 2.5" drives at the same time, something I could not do with the Chaser without additional drive bays.  Since this build uses all 2.5" drives you'll still need a couple the ICY 2.5" drive bays, or you may opt to use all of them and give yourself the ability to have 12x 2.5" drives fit in this case (though you'll need a different motherboard or add on SATA controller).

<a href="http://www.newegg.com/Product/Product.aspx?Item=17-994-141" target="_blank">Dual 2.5" Drive Mount for 3.5" bay</a>:  With the 230T case you can mount 4x 2.5" drives, however in our build we have a total 6 so you will need at least one of these mounting kits.

<strong>Summary</strong>

For around $1200, you can have a quad core, 32GB RAM setup which should be capable of building a nice nested ESXi lab.  I will be looking into 6-core versions this weekend

Non-linked part list:  For those who just want PN's I've listed them below- component: MFG PN / Newegg PN (QTY)
<div>Processor: AD750KWOHJBOX / N82<wbr />E16819113328 (1)</div>
<div>Memory: F3-1600C9Q-32GXM / N82<wbr />E16820231569 (1)</div>
<div>Motherboard: GA-F2A88XM-D3H / <wbr />N82E16813128659 (1)</div>
<div>SSD: Neutron Series GTX 120GB / N82E16820233404 (2)</div>
<div>HDD: ST500LM000 / N82E16822178<wbr />339 (4)</div>
<div>NIC: SY-PEX24028 / N82E1683332<wbr />8022 (1)</div>
<div>Case: Corsiar 230T / N82E16811139027 (1)</div>
<div>PSU: RX-600AF / N82E1681715204<wbr />1 (1)</div>
<div>Fan: CLP0605 / N82E16835106213 (1)</div>
&nbsp;