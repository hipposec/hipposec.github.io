---
layout: post
title: "Using a custom domain with free gmail"
date: 2023-06-10 15:46:08 -0500
categories: uncategorized
---
One of the things I’ve done in the last few years is move my primary email address over to a custom domain. The purpose for this change is to make my email address more portable, meaning if I ever have an issue with my hosting provider I can pick up and move without needing to change addresses. This was particularly a concern as I read more and more stories of providers arbitrarily blocking users for terms of service violations with no real chance of appeal.  

I like for email and my office-type products (word processing, cloud storage, etc.) to be with a single company so that essentially narrowed my choices to Microsoft, Google or a custom iCloud domain. I used Microsoft and it was great, but I decided to try out using Gmail so I could avoid the additional monthly costs.  

Google pushes people to Workspace but as long as you just want to send/receive email this can be done from a free Gmail account. 

The easiest part to setup is the ability to receive email at the custom domain. I went into Google Domains and configured email forwarding to my already established Gmail account. As far as I know, there’s nothing special about using Google domains for this and email forwarding from other providers will work. 

https://support.google.com/domains/answer/3251241?hl=en

The more complicated part is setting up the ability to send inside Gmail, but the instructions Google provides worked perfectly.  

https://support.google.com/mail/answer/22370?hl=en

When you get to configuring server settings, use the Gmail SMTP settings. Note that for authentication you need to use your @gmail.com address and not the custom domain. Hopefully you’re using Google’s MFA to protect your account so you’ll have to generate an application password. 

https://support.google.com/mail/answer/7126229?hl=en#zippy=%2Cstep-change-smtp-other-settings-in-your-email-client

The final part is creating a DNS record letting everyone know the gmail servers are authorized to send email for your domain. You do this by going to your DNS provider and creating a record with the type “SPF” and this value: 

“v=spf1 include:_spf.google.com ~all” 

A few tips on this setup: 

– When setting a custom domain, consider carefully before using a less common TLD (.com, .org, etc.). I have had some issue with websites (usually banks) that use data validation for email addresses claiming my domain wasn’t valid because of this. 

– This works for sending / receiving email but for any other function within Google I believe you have to continue using your gmail address. 

– When setting up your email forwarding, consider also creating a catch-all address that will forward to you any email sent to your domain regardless of the username (so *@yourdomain.com). You can now use any name@yourdomain.com to sign up for websites and then use this to filter their emails without revealing your primary address.  
