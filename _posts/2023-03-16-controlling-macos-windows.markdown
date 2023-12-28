---
layout: post
title: "Controlling MacOS from Windows"
date: 2023-03-16 15:44:48 -0500
categories: uncategorized
---
While I like using my iPhone (most of the time) I tend to prefer Linux or Windows as my desktop. Since I only use iMessage, this means I lose the ability to send an interesting article or photo over iMessage. It also means I can’t access apps such as Apple Maps or Apple News that I prefer on my phone. 

I’ve just recently discovered that MacOS has a built in VNC server that you can then access from Windows or Linux with a VNC client such as UltraVNC. This doesn’t remove the expense of owning the mac, but gives me a little more flexibility. Here’s how to set that up: 

In the MacOS you need to enable the server under Sharing / Remote Management. On this screen be sure to click Computer Options and set a password for connecting, otherwise UltraVNC will not connect at all. The password is annoyingly limited to only 8 characters but don’t worry – you’ll also have to authenticate as a user. 

In Windows, go download and install UltraVNC. I did not have to change any settings from default, all I did is provide my Mac’s IP address and connect over port 5900. 

The resolution isn’t the best, but it works. RealVNC seems to be a much sharper solution but I did not want my mac accessible from the cloud or to pay a subscription fee.  
