---
ID: 4063
post_title: 'Quick How To &#8211; Using Ghost Inspector to monitor your blog'
author: Jonathan Frappier
post_date: 2015-11-08 20:21:49
post_excerpt: ""
layout: post
permalink: >
  http://www.virtxpert.com/quick-how-to-using-ghost-inspector-to-monitor-your-blog/
published: true
dsq_thread_id:
  - "4301839574"
---
Ghost Inspector is a tool for generating and continuously monitoring web sites and web applications, since it is free for up to 100 tests, I thought I would give it a try to ensure certain elements of my blog are working as expected. You can sign up for your free account at <a href="http://ghostinspector.com" target="_blank">ghostinspector.com</a>

The first step is to install the recorder and create a new suite of tests. I have installed the Chrome extension and created a suite called www.virtxpert.com

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/ghostinspector.png"><img class="aligncenter size-full wp-image-4064" src="http://www.virtxpert.com/wp-content/uploads/2015/11/ghostinspector.png" alt="ghostinspector" width="1177" height="480" /></a>

Once your inspector is installed, click on the ghost icon, log in and you can being recording your test. Since I currently run ads on my site, I want to ensure that the ads are displaying correctly. To do this, you use what is called an assertion. Start the recording and open your the web page you wish to test, i this case this blog. Click on the now green ghost icon, select Make Assertions, and click on the image you want to ensure is appearing.

Once complete, Ghost inspector will run through the test you just recorded. As you can see here the images for my various banner ads were found when the page was loaded.

<a href="http://www.virtxpert.com/wp-content/uploads/2015/11/ghostinspector-check-web-graphics.png"><img class="aligncenter size-full wp-image-4065" src="http://www.virtxpert.com/wp-content/uploads/2015/11/ghostinspector-check-web-graphics.png" alt="ghostinspector-check-web-graphics" width="1157" height="664" /></a>

In addition to the test, a video is taken and screenshot of the site you are testing. Another great feature of Ghost Inspector is the ability to schedule these tests, rather than manually running them. Click on Settings &gt;&gt; Schedule and select an option that fits your needs, I have opted for daily. You can create up to 100 of these tests in the free tier to ensure specific components of your website are working properly.

In addition to scheduling, you can also trigger tests via API to execute an entire test suite, very handy for web applications as part of the deployment process.

You can also enable notifications, either at the individual test level, suite level, or organization level. To set this at the organization level, click on your avatar on the top right side of the page, then click notifications. As you can see here you can set multiple email addresses, and even enable webhooks. With webbooks enabled you could theoretically receive updates of failed tests in something like Slack - very handy!

&nbsp;