---
layout: post
title: "Using Amazon Dash button to trigger scripts"
date: 2017-04-16 07:21:27 -0500
categories: uncategorized
---

A handy weekend project is to hack Amazon Dash buttons together with your own server to trigger scripts. Although there are several ways to do this, my path is possible because I run a linux box to provide DHCP and DNS services to my LAN. Another option would be to monitor for ARP packets.

**Background**

The Amazon Dash button is a $5 device from Amazon (usually offset with a $5 credit) that allows you to push a button and order a specific product. When the button is pressed the device wakes up, connects to Wifi, and reaches out to Amazon to complete the order.

**Setup**

As I mentioned before, this assumes you run your own linux system with dhcpd and rsyslog. The same concept would likely work on other *nix systems or pfsense. And I’m assuming if you’re doing that you can also write your own script, make it executable, etc.

* First, setup your Dash button by holding down the button until the light flashes blue.
* Open the Amazon App on your phone and go to Your Account, and Manage Devices under the “Dash Buttons & Devices” section
* Follow the process to setup the new button and when it comes time to choose a product close the setup wizard.
At this point pressing the button should cause your button to join Wifi but not successfully order a product since you haven’t completed the setup. Press the button and check your dhcpd logs (in Ubuntu that would be /var/log/syslog) and look for the most recent line similar to:

>> dhcpd: DHCPACK on 192.168.1.150 to 50:f5:da:d3:45:24 via eth0

The important thing to get from this line is the MAC address of the dash button. We need to use the MAC to create a DHCP reservation which in Ubuntu is in /etc/dhcp/dhcpd.conf

>> host gainbutton { hardware ethernet 50:f5:da:d3:45:24; fixed-address 192.168.1.18; }

Note that in my example I have changed the IP address for the reservation to be different than what was initially assigned. The new address will be used from here forward.

We now have a trigger mechanism because pushing the dash button will cause a known unique entry to appear in the system logs. Using rsyslog configuration we can cause that unique log entry to trigger our script. To have the MAC address and the new IP address  trigger myscript.sh put the following line in /etc/rsyslog.conf

>> :msg, regex, "DHCPACK on 192.168.1.18 to 50:f5:da:d3:45:24" ^/home/hipposec/bin/myscript.sh

Now restart rsyslogd and and test pressing your button to see if it runs the script.

The last thing you’ll want to do is block the button in your firewall so that it can’t reach Amazon. If you do not do this you will receive a notification from Amazon every time you press it letting you know that it is not set up completely.

Note: After the button has been pressed you must wait 10 seconds or so for the wireless connection to terminate before pressing it again.

**Use case ideas**

I’d love to hear more ideas for using these since I have one more unused button, but here’s how I’m using them now:

* A button by the bed that triggers all of my Hue lights to come on to full brightness
* A button on my dog’s food container that just logs a date and time when pressed. A separate script monitors this log and emails me if I haven’t fed her by a certain time in the morning / afternoon, but also lets me check to make sure I don’t feed her twice (which is more likely).

Final note: Several others on the internet have had the idea to use Dash buttons in this way, it is not my original idea. There are multiple ways this could be accomplished.
