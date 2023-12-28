---
layout: post
title: "Preparing for that first security job - Respond"
date: 2019-02-11 07:38:22 -0500
categories: uncategorized
---

The last post discussed detecting an incident, now we’ll get into responding to one. Each scenario is a little different and hopefully your organization has response procedures so this will be more of a high level post than the others.

As part of the Detect post I mentioned the importance of keeping up with the news. As you do this, be on the lookout for analyses of attacks after the fact. Learn what you can about what real attacks look like, how they could have been stopped and what organizations do right or wrong in response. 

The main parts of dealing with an incident are containment, eradication and recovery. But before any of those can take place, be sure that in your detection phase you’ve adequately confirmed an incident has occurred. Legitimate activity or simple mistakes can sometimes appear to be a security incident until you unravel the whole story.

**Containment**

As quickly as possible our goal is to keep an attack from causing further damage. Ask yourself:

* How did the attack gain a foothold in the environment? Examples could be unpatched systems, compromise credentials, or social engineering
* After a foothold was established, what methods are being used to propagate within the environment?
* Going back to the previous post, what logs or indicators would be useful in identifying systems that have been affected?
* Are you able to determine the attacker’s goal?
* Is there anything you could warn users about?
* Based on this information, how do you stop the attacker from continuing? Some examples could include locking accounts, adjusting firewall rules or disconnecting systems from the network.
* Once you’ve contained the threat, it’s time to remove it and bring things back to normal.

**Eradication and Recovery** 

The lines between eradication and recovery can sometimes be blurry so I’ll address them together. The steps in this process are fueled by the information you learned in the Detection and Containment phases. The goal is to remove the threat, prevent it from happening again and restore the systems back to production readiness. Typical steps in this process include:

* Re-installing operating systems and applications or restoring them from backup
* Having users reset passwords
* Patching systems to close vulnerabilities
* Introducing new controls such as additional firewalls, employee training or changing access permissions on an account

After a major incident all parties involved should have a “lessons learned” meeting to identify areas of improvement in preventing, detecting and responding to incidents.

Next week I will post the last and final portion of this series which covers advise on interviewing.
