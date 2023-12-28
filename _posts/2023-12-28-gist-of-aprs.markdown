---
layout: post
title: "GHOR - Gist of APRS"
date: 2023-12-28 16:23:46 -0500
categories: uncategorized
---
This short summary of APRS is part of a series explained here [Gist of Ham Radio (GHOR)](https://hipposec.github.io/uncategorized/2023/12/28/ghor-gist-ham-radio.html) .

APRS is a digital transmission of packets over your radio. Once broadcasted, these packets can be picked up by repeaters (digipeaters) which will rebroadcast them so that they cover a longer distance. Your ultimate goal is to have your packet picked up by an iGate which will post them to the internet. From there they could be turned into SMS messages, message bots for information, or let someone know your location.

At the moment I'm just experimenting with transmission of packets including via the ISS but it's a goal to setup a digipeater or at least an iGate. 

What's in the packets?

There are two types of APRS packets. Beacons, which include location and sometimes weather info are broadcasted to no one in particular, and then there are messages which work similar to texting. You can go to https://aprs.fi to see beacons from other users. 

One very handy feature of APRS is the ability to send a cellphone text message by sending @phonenumber <message> to SMSGTE (check the SMSGTE website for more info). Note that this is using the messaging ability of APRS and not beacons. Some radios such as the new Anytone D878UVII Plus only do beacons. 

How are they transmitted?

In the US, APRS packets are usually transmitted on 144.390 Mhz using FM. That means you can transmit APRS as long as you have a Technician license. 

What do I need?

I'm still learning APRS, but there seems to be a few ways to get on the air. I'll do more detailed explanations of each as time permits as separate documents. 

The first is to just buy an APRS radio. I purchased a AnyTone D878UVII Plus which lets me transmit a beacon, and this generally works. I say generally because I'm far enough away from a repeater / iGate that I have to use my base station with 8db gain to get anywhere. I used this exact setup to digipeat an APRS packet off the International Space Station.

Another method I've been messing around with is the APRS Droid app on an android tablet, the APRS cable for a Baofeng and my UV5R. The gist of how this works is your android device will create the packet and play the packet as audio. You plug your device into the Baofeng via the APRS cable and enable VOX (meaning the radio will transmit when it "hears" audio). 

Neither of these quite satisfied me so I've ordered a Mobilink TNC. As mentioned, the AnyTone lacks messaging and the Baofeng just isn't very reliable. 

What if I just want to listen?

You can checkout APRS activity in your area with the RTL-SDR and GQRX (SDR software for linux). Tune to 144.390 Mhz, set the mode to Narrow FM, then go to Tools, AFSK1200 Decoder. This will open a new window which will show the decoded packets as they happen. Note that it's not too uncommon for a packet to come through but not be decoded correctly.

Activity wise, I live in a suburban county of almost a million people. I probably hear a packet every 2-3 minutes.
