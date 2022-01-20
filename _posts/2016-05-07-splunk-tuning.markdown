---
layout: default
title: "Splunk tuning"
date: 2016-05-07 07:18:42 -0500
categories: uncategorized
---

I recently found myself with too much log data and not enough Splunk license to handle it all. After spending a few days digging through the logs with grep, cut, sort and uniq I was able to cut the log size down to a quarter of what it originally was. Here’s how:

First I should mention to accomplish most of this I changed my systems to not log to the Splunk application directly, but rather to the rsyslog demon. Splunk then monitors the directories / files produced from there. While this may not be the best option performance wise, it has the benefit that I can retain some logs as plain text and not have them be analyzed by Splunk.

**Look for logs that give little value**

The biggest change I made was going through our firewall logs for udp traffic connections. Since udp doesn’t use sessions, every packet was being recorded. I reduced the logs by more than half by dropping firewall logs showing our DNS caching servers were making DNS queries. I accomplished this by having a rsyslog rule that outputs messages from our firewall containing “dns” to a different directory.

Other udp services you may want to look for and consider dropping are syslog and consul if they are present in your environment.

An option that involves a little more risk (if your focus is security) is to drop logs that involve your monitoring solution. These can generate high volume of authentication and firewall logs. The same decision can be made with vulnerability scanners.

**Truncate Windows logs**

If you’ve ever looked at Windows logs, you’ll notice that they contain a lot of worthless text that explain what the log message means. Over hundreds of thousands of events this really adds up.

Adding these lines to props.conf removes some of that chatter. Credit goes to Andreas Lund commenting on this post: http://blogs.splunk.com/2013/10/14/windows-event-logs-in-splunk-6/

>>SEDCMD-event1=s/This event is generated(.*[\r\n]*)*/_truncated_/
>SEDCMD-event2=s/Token Elevation Type indicates(.*[\r\n]*)*/_truncated_/

**Short hostnames**

This doesn’t have the big pay out the other methods do, but if you can log only the hostname of the systems sending logs instead of the FQDN it does add up. In our case this freed up another 500MB / day of license.

With a little work you can make changes that produce significant savings in the cost of running a Splunk instance (a product I’m extremely happy with by the way). If you have any tips on how to further reduce log volume, please comment.
