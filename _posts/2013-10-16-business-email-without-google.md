---
id: 944
title: How To Setup Business Email Without Google Apps
date: 2013-10-16T16:35:38+00:00
author: Adrianna Tan
excerpt: How to set up business email without Google Apps. I like Fastmail and this is my workflow.
layout: single
guid: http://popagandhi.com/?p=944
permalink: /2013/10/business-email-without-google/
crisp_persona_post_view_count:
  - 1146
dsq_thread_id:
  - 1863108541
categories:
  - Tech
---
Google Apps seemed like a godsend to many businesses when they first came around. The free version was great, and I never had to upgrade. Eventually I came around to the same opinion that Marco Arment has [stated many times](http://www.marco.org/2011/04/05/let-us-pay-for-this-service-so-it-wont-go-down): I want to pay for a service I need, especially one that is so mission-critical like business email. Several times I&#8217;d had problems with Google Apps and just simply could not get any support because we were on the free service. I could have upgraded, but migrating my email to another provider was something I wanted to do anyway to wean myself off the big G.

When I had to set up email for a new business recently, I decided to try something new. I decided to go with Fastmail.fm after multiple recommendations from other geeks, and so far I&#8217;m pretty happy with it.

I didn&#8217;t find too many resources in the same place, so I decided to make one.

**1. Buy a domain.**

If you haven&#8217;t already bought one, or are thinking of transferring to a better domain registrar, I strongly recommend [Name.com](http://ref.name.com/aff_c?offer_id=3&aff_id=6677). I have been using them for a long time — never been happier. Everything is easy and straightforward, unlike GoDaddy. (Disclaimer: If you click on [Name.com](http://ref.name.com/aff_c?offer_id=3&aff_id=6677) from my site, I make a small percentage through my affiliate link.)

**2. Purchase an email plan. (Fastmail recommended)**

I like Fastmail for many reasons (read about some of them [here](http://www.marco.org/2011/04/05/let-us-pay-for-this-service-so-it-wont-go-down). Sign up for a business plan at [Fastmail.fm](https://www.fastmail.fm/signup/business.html). If you&#8217;re not sure what you need, just start with the basic plan. I&#8217;m just a one-person operation at the moment and I have a Standard plan. I&#8217;ll look into upgrading when I need to.

Fastmail will run you through account setup and passwords. You can create a master user and use that to make administrative changes to all accounts. Use a different password for the master account and your own standard account.

**3. Make some DNS changes.**

Log in to your [Name.com](http://ref.name.com/aff_c?offer_id=3&aff_id=6677) account. Click on the domain you just purchased, and click on DNS Records. If you&#8217;re using any other domain registrar, just locate for the DNS Manager or other tool that lets you make your own DNS changes. If you&#8217;re using an off-site DNS service, you probably won&#8217;t be needing this article but the same DNS values apply.

**4. Set up CNAMES**

This how-to won&#8217;t cover how to set up your domain to your web host and will focus only on email. In the DNS Manager/DNS editing area of your domain registrar/service, create two new CNAME records.

In [Name.com&#8217;s](http://ref.name.com/aff_c?offer_id=3&aff_id=6677) DNS manager, select CNAME from the TYPE dropdown and enter _mail_ into the blank space named &#8220;HOST&#8221;. Enter _wwww.fastmail.fm_ in the ANSWER field, and 300 in the TTL field. (Remember to come back to this after everything is setup and ready to go — once it works, come back here and change all the TTL values to 3600.)

Create a second CNAME record, repeating all the steps but with a new CNAME record of _wap_ instead of _mail_.

You&#8217;ll end up with:

CNAME mail.yourdomain.com www.fastmail.fm 300

CNAME wap.yourdomain.com www.fastmail.fm 300

NOte that you can replace mail/wap witho whatever you prefer, such as mail/mobile or email/m. For newbies, the whole idea of creating these CNAME records is so that you can go to mail.yourdomain.com or m.yourdomain.com or mobile.yourdomain.com and access the web interface.

**5. Set up MX records**

In the same DNS management screen, set up two MX records. It&#8217;s exactly the same as the above, but there is a new field for MX records: priority. In this case, the two values have a priority value of &#8220;10&#8221; and &#8220;20&#8221; each.

As below:

MX yourdomain.com in1-smtp.messagingengine.com 300 10

MX yourdomain.com in2-smtp.messagingengine.com 300 20

**6. Set up IMAP access**

The best part of Fastmail is its excellent IMAP feature. You can, of course, use the web interface at mail.yourdomain.com (or whichever CNAME record you just set up in step 4, but I prefer to use various email software to access my business email.

On my desktop, Mail.app or any other app.

On my iPhone, my new go-to Mail app for business is [Dispatch app](http://www.dispatchapp.net/). It supports all of the productivity tools that I use or like, such as Evernote, Clear, Things, Google Maps, Drafts, Skype, Fantastical, Reminders, Due (see full list [here](http://www.dispatchapp.net/faq.html)); it&#8217;s a different approach to email, and I like its action-driven focus. It&#8217;s still pretty young, but I like it very much already.

No matter what email client/software you use, the setup should be the same.

_Incoming mail server: mail.messagingengine.com

Port: 993

Username: yourname@yourdomain.com

Password: xx your password xx_

_Outgoing mail server: mail.messagingengine.com

Port: 465

Use SSL: Yes

Authentication: Plain

Username: yourname@yourdomain.com

Password: xx your password xx_

You can also set up your Fastmail account to [enable FTP and DAV access](https://www.fastmail.fm/help/remote_email_access_server_names_and_ports.html), but I haven&#8217;t had the need to.

You should be all set up now, just send a test email and make sure everything works! (For more info/support, go [here](https://www.fastmail.fm/help/remote_email_access_server_names_and_ports.html).) When it all works great, go back and change all of the TTL values from 300 to 1800 or 3600.

Did this work for you? Is there another email provider you have had a great experience with? Let me know in the comments.
