---
ID: 2170
post_title: 'CapEx versus OpEx &#8211; its not a decision point, its a result of business requirements'
author: Jonathan Frappier
post_date: 2014-04-24 10:12:30
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/capex-versus-opex-its-not-a-decision-point-its-a-result-of-business-requirements/
published: true
dsq_thread_id:
  - "2635735519"
---
At the <a href="http://techfieldday.com/event/sddc14/" target="_blank">SDDC Symposium</a>, there was a discussion around <a href="http://www.investopedia.com/terms/c/capitalexpenditure.asp" target="_blank">CapEx</a> vs <a href="http://www.investopedia.com/terms/o/operating_expense.asp" target="_blank">OpEx</a> (video below).  You can click the previous links to learn more about each but, in short, CapEx or Capital Expenditures are large, one time purchases, such as buying a SAN or NAS for example where as OpEx or Operational Expense is ongoing cost which in the technology field most closely aligns to ongoing cost such as monthy payments for Amazon AWS instances or S3 storage.

I expected a bit more discussion around actual CapEx and OpEx, however (at least early on) was mostly around technology and whether vendors can lock you in or how to be more agile.

From my perspective, CapEx and OpEx isn't a technology decision alone, it's a joint decision between the short/long term business goals, the finance group and how they prefer to manage cash flow and budget and what technology groups need in order to support those short and long term business goals.  I don't feel that one is any better than the other, but it should be a marriage between business, finance and technology.  If short term business goals call for a more flexible end user computing solution, and additional business requirements call for lower operational cost then its the job of the technology group to find a solution.  If a longer term business goal is, as Colin McNamara used in one of his examples, a more mature development solution that allows you to abstract your code/product from any particular solution then the finance and technology groups need to work together to allow for the OpEx model.  Let's assume for a moment that this conversation goes horribly wrong for you and you are instructed as a technologist to go CapEx, and are given the budget to build out multiple physical data centers, does that really change your development model?  I don't think so, build your code so it can be deployed and don't tie  yourself to the hardware where its deployed.

At the end of the day, CapEx vs OpEx is not a decision, its the result of business requirements that involve many people.  I've worked for organizations where finance felt very strongly for a CapEx model, however, when needed we discussed business requirements that required solutions in more of an OpEx model and that worked because business, finance and technology worked together to identify the needs of the business and the solution to properly support those needs.  Justin Warren made a similar point around 18:29 which I've often said - business doesn't care about technology, it doesn't care about what server vendor you use they want their business to operate, be available, perform well and provide disaster recovery options while supporting customer and local/state/federal requirements.  If I can run my business application stack on AWS or on my local VMware stack, the business doesn't care.  It's up to the technology group to take these requirements and build the right solution.

To my fellow technology folk, let's make CapEx vs OpEx a thing of the past and focus on the needs of the business(es) we support.  Technology needs to understand how the business and finance operate, and we need to educate business and finance on various solutions and make the right decision for the business.

<strong>SDDC14 CapEx/OpEx Battleground</strong>

<iframe src="//www.youtube.com/embed/5_Lk4Cer-C4" width="560" height="315" frameborder="0" allowfullscreen="allowfullscreen"></iframe>