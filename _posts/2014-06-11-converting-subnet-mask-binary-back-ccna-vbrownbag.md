---
ID: 2274
post_title: 'Converting Subnet Mask to binary and back #CCNA #vBrownBag'
author: Jonathan Frappier
post_date: 2014-06-11 21:47:24
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/converting-subnet-mask-binary-back-ccna-vbrownbag/
published: true
dsq_thread_id:
  - "2757098090"
---
A question came up on the professionalvmware.com CCNA R&amp;S #vBrownBag about converting your subnet mask to binary, something common in the Cisco CCNA exam.  Here is a nifty little cheat sheet you can use if you don't have access to a subnet calculator either in the exam or locked in a data center with no internet access.

A subnet mask is made up of 8 bits.  If you take 255 as an example, the associated binary value would be 11111111.  The easiest way to visualize or think about this is that each place has a value, going from left to right the values are:

128 | 64 | 32 | 16 | 8 | 4 | 2 | 1

Basically start at 128 and divide by 2 going left to right (or right to left start at 1 and double).  Now I mentioned before that 11111111 = 255 because

128 + 64 + 32 + 16 + 8 + 4 + 2 + 1 = 255.

Easy with 255, but what about another value, say 255.255.240.0?  Well the first two octets would be 11111111.11111111, to get the binary value of 240, start adding numbers from left to right so

128+64+32+16 = 240.  To get the binary value place "1" in the place holder for each of those numbers and "0" for the remaining so 11110000

Another example is 255.255.254.0 would be

128+64+32+16+8+4+2 = 254 so the binary version would be 11111110

To revert binary back to a numerical value, simple take the value that corresponds to that spot and add it together, for example if you have 1100000000 take the first to places from the table and add them together so 128+64 = 192.