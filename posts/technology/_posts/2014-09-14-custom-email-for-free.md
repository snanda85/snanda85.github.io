---
layout: post
title: How to get a Custom Email for Free
subtitle: Operate email with custom domain by leveraging existing personal gmail account
tags:
- email
- custom domain
---
So you've bought a personal domain for blogging (or are going to buy a new one).  
Wouldn't you like to operate a custom email id myname@mydomain.com? It definitely looks more professional (and cooler) than mydomain@gmail.com

There are various companies who provide business email hosting like [Google Apps][] or [Office 365][], but they are not free. There are other companies who provide cheap email hosting as well, but they might lack some important features like IMAP, Mobile Sync etc.

So, why not use the most reliable email hosting provider for free? **GMail**. Yes, for free.

<!--more-->
## Pre-requisites
1. Buy a domain from a registrar who provides free email forwarding like [GoDaddy][], [BigRock][] or [NameCheap][].
2. Create a GMail account if you don't already have one.

##Configure incoming mail
This step will make the gmail account to recieve the emails sent to your custom email address.
I am taking an example of Godaddy. The steps might be a little different for other domain providers, but the general idea is same.

1. Sign in to GoDaddy account &rarr; Webspace login &rarr; SetUp
    {% include post/image.html src="free-email-7.png" alt="Setup Email forwarding for the domain" %}
    In the popup dialog, select your domain name and click Submit
2. Click "My Account" &rarr; Email &rarr; Launch
3. This will bring you to the Email settings. Click on 'Create Forward'
    {% include post/image.html src="free-email-4.png" alt="Go to Email forwarding setup" %}
4. Enter your custom address in "Forward this email address", and gmail id in "To these email addresses"
    {% include post/image.html src="free-email-5.png" alt="Configure the email forwarding" %}
5. Click "Create", and wait for a few minutes for the setup to complete
6. Ask a friend to send you a test mail and confirm that you are able to recieve the email in your gmail inbox

**Note**: While testing the email delivery, please use a different email address to send out the test mail. Mails sent from the recipient account (i.e. your gmail account) will most likely fail.

For reference, Here are the instructions for [Namecheap setup][nc-ins] and [BigRock setup][br-ins]

##Configure outgoing mail
Now lets configure the gmail account to send out emails from the custom email address.

1. Sign in to Gmail using your personal account
2. Click the gear icon in the upper right and click Settings.
3. Go to the "Accounts and Import" tab.
4. Under "Send mail as", click on "Add another email address you own"
    {% include post/image.html src="free-email-1.png" alt="Gmail Settings" %}
5. In the newly opened popup window
    - Enter your name and custom email address
    - Deselect "Treat as an alias", and click "Next step".  
    {% include post/image.html src="free-email-2.png" alt="Adding a new email address" %}
6. Next step is to configure the outgoing smtp server
    - In the "SMTP Server" field, enter "smtp.gmail.com"
    - Enter your gmail account credentials in Username/Password fields
    - In case you have enabled 2-step verification, you would need to generate an [application specific password][app-pwd]  
    {% include post/image.html src="free-email-3.png" alt="Configure the mail server" %}
7. After this you will get a verification code on your email. Enter that code in the verification window and you are done.

Now, while sending out a mail you can select your custom address as your from address.  
    {% include post/image.html src="free-email-6.png" alt="Send mail" %}

[godaddy]: http://www.godaddy.com
[bigrock]: http://www.bigrock.com
[namecheap]: http://www.namecheap.com
[google apps]: http://www.google.com/intx/en_in/enterprise/apps/business/
[office 365]: https://godaddy.com/business/office-365.aspx
[nc-ins]: http://www.namecheap.com/support/knowledgebase/article.aspx/308/76/how-can-i-setup-free-email-forwarding-for-my-domain
[br-ins]: http://manage.bigrock.in/kb/servlet/KBServlet/faq445.html
[app-pwd]: https://support.google.com/accounts/answer/185833?hl=en
