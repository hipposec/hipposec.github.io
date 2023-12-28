---
layout: default
title: "Preparing for that first security job - Protect"
date: 2019-01-28 07:30:04 -0500
categories: uncategorized
---

In the introduction we covered how the basic principles of many security jobs address the Protect, Detect and Respond concepts. This post guides you in becoming more educated on the Protect portion. The goal of the series is not to provide answers but rather to point a new security practitioner in a direction and ask questions. Finding the answers to these questions will hopefully build knowledge and the skill of self learning.

Protection is simply identifying risks and then knowing what changes to make (commonly called security controls) to reduce that risk . I’ll break this down into vulnerability scanning, penetration testing and security controls.

**Vulnerability Scanning**

For vulnerability scanning, I highly recommend downloading a trial or home version of a vulnerability scanning tool and trying it out on a network you are authorized to scan such as your home network. One example is Nessus Home by Tenable which is free and commonly found in enterprises (with a license). Learn about the following topics:

* How do you specify scan targets, and how does this account for changes in the environment such as a system getting a new IP address from DHCP?
* How do you schedule a scan, and what factors might you need to consider when scheduling a scan in a corporate environment? (Hint: think of what else is going on in the environment at different times of the day)
* Examine the results and ask how you would determine which are the highest priority (consider the discussion of Risk in the Intro post)
* What are the limitations of your scan? For example, was some of the scan blocked by a firewall? Was the scan able to assess all software on the system or just those that provide a network service?
* What information did the scan use to identify the vulnerability, and what level of confidence does that give you in the finding? These tools are not error-proof.
* Lastly, now that you’ve got a finding what needs to happen to address it?

**Penetration Testing**

Penetration testing is a huge topic you can spend a career learning. It’s important to note that a key difference between vulnerability scanning and penetration testing is while vulnerability scanning is performed by software in an automated fashion, penetration testing is an in-depth approach by a human with creativity applied. Although a penetration test may utilize vulnerability scans as a source to provide value it should do more than simply verifying the results of the scan. At the conclusion of a penetration test you should walk away with a fairly solid understanding of what the environment is and what it does.

Some great places to start on penetration testing is OWASP and the Metasploit Unleashed tutorials. I also enjoyed the OSCP certification which I have written about previously. A key factor in recommending the OSCP is that the test is performance based so it is not focused on memorization and multiple choice questions.

Some questions to think about during a penetration test are:

* Who is your target? In other words, what does the target do and how do they work? Who are the key employees? How might you leverage this knowledge in an attack? Google is your friend here.
* What specifically is in the environment, and how can you interact with it? (Hint: nmap.org)
* What’s the purpose of the systems you’re attacking, and how might that change your approach? For example, companies often put less effort into securing their dev systems compared to production, yet the compromise of a dev environment can lead to the compromise of a production environment through issues such as shared credentials.
* Another thing to consider is how vulnerabilities may be chained together to produce a larger result. For example, I once tested an environment that was utilizing a top level domain which was available for public use. Meaning, the environment was using “bar.com” even though anyone could create system “foo” and register it as “foo.bar.com”. I also found a password reset tool which when tested gave a very detailed error message complaining that it could not send the password reset email to the user because “companymail.bar.com” did not exist. So, I created my own mail system and registered it as “companymail.bar.com”, captured the password reset email and which allowed me to take over the administrative account for the web application. A vulnerability scanning tool may have picked up on these two issues individually but would not have painted the whole picture of how these could be leveraged.

**Security Controls**

You’re likely already aware of many best practices in the security field such as malware protection, encryption, firewalls and IPS systems. In a security job you’re going to be asked to know how all these tools in your belt work and how to apply them to reduce risk. And just as importantly, you’re going to need to know the weaknesses in these tools so you can identify what risk remains. I encourage you to get some experience with the following:

* Firewalls – both host and network based firewalls. For example, configure a iptables firewall on a Linux system or the Windows firewall. Setup pfSense on your home network
* IDS – Snort is a free example
* AntiVirus – If you don’t have one already, look for demo or open source versions to experiment with. I haven’t used it personally, but Immunet is an open source product by Cisco which has similarities to their enterprise offering
* OSSEC is an open source HIDS which can also do file integrity monitoring
* Setup a webserver and then protect it with a certificate from LetsEncrypt
* Disk encryption such as bitlocker if your version of Windows supports it

For each of these, ask:

* What kind of attack is the control preventing and in what situations is it successful? For example, a certificate from LetsEncrypt allows you to protect a connection from an attacker sniffing network traffic. But it relies on your end user accessing the site over HTTPS / port 443 and not HTTP / port 80 and refusing to connect if the certificate cannot be verified.
* What risk is left over after the control is applied? For example, the LetsEncrypt certificate only protects data as it is transmitted over the network. It does nothing to secure the data once it is written to disk. For another example, disk encryption such as BitLocker does not protect the data if the system is running and remotely compromised.
* What are ways of bypassing the control, and what is required of the attacker to accomplish that? For example, a firewall may prevent a remote attacker from connecting directly to a system. However, if the attacker can trick a user into executing code the connection can be initiated from the remote system to the attacker. Also, unless specifically configured otherwise IDS and IPS systems are blind to detecting threats that occur over encrypted connections.
* How reliant is the control on the cooperation of an end user, and why might they attempt to bypass it? For example, a user with sufficient privileges might disable or remove AntiVirus if they believed it was impeding their work. They are likely unable to make changes to a network based firewall, but that firewall doesn’t do much good if they take their laptop to Starbucks and use their wifi.

The most important part of these exercises are to learn the tools in your tool belt and how to successfully apply them. However, you will often find there is a balance to be struck between the extreme of implementing controls in a rigid fashion to create tight security versus allowing the organization to remain productive and innovative. Finding out what slips through this gray area is the purpose of Detection, which is covered in next week’s post.


