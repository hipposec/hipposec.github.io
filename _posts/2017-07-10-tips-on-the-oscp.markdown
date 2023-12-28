---
layout: post
title: "Tips on the OSCP"
date: 2017-07-10 07:23:40 -0500
categories: uncategorized
---

I recently passed the OSCP and wanted to share some stuff I learned to help others.

For perspective, my background:

* 8 years of a wide range of Infosec experience mostly from the “blue team” point of view
* For 2 years of that experience, my duties were split between security and being a network admin. This meant managing the network but also a few linux based servers that provided DHCP/DNS/NTP/Radius
* 18 years as a linux end-user
* Exposure to scripting / programming in C, C#, ASP, Java, Bash, Perl and Python. I am not remotely a developer though. Most of the deeper exposure was through college work quite a while back. For anything serious I need a bit of googling to jog my memory, but I am comfortable following source code and making slight modifications when needed.
* I have a CEH and previously read “The Basics of Hacking and Penetration Testing: Ethical Hacking and Penetration Testing Made Easy”. So I was familiar with a lot of the concepts even if I didn’t have much hands on experience.

**Course and Lab**

There’s already a lot out there about what makes up the course and exam, so I won’t go too deep into it. In all I paid for 120 days of lab time, but had a couple stretches where I simply could not make time for it. If my calendar had been more open the recommended 60 days would have been plenty. I took the exam after getting root/admin rights on 32 systems which included gh0st, humble, sufferance and pain. The exam took me a little over 22 hours and the report less than 4.

I did not bother with the exercises in the PDF or writing a report about the lab as I felt they were not worth the extra 5 points.

**Tips**

* Lab time is pricey, so be honest with yourself about how much time you have to work on it (see above). After the first few, most machines took me 2-4 hours to compromise (gh0st, humble, sufferance and pain took 6-8). So at that pace 30 machines takes from 60-120 hours. When coming up with a plan, also consider if you’re the kind of person who can walk away in the middle of a puzzle. I’m not, so that resulted in many late nights and tired mornings.
* Note taking and enumeration are critical, so figure out what works for you. My approach was to use OneNote with a page for each system. I started each page with a template and walked through enumeration by filling out each section. The last part of the page would be a list of potential vulnerabilities followed by my initial exploit notes and privilege escalation notes. On a separate page I kept track of useful commands I was going to use often, such has how to generate a msfvenom payload or how to add a windows admin account via command line.
* Work out a routine for the lab / exam that includes breaks. What worked great for me was to wear a digital watch that beeps at the top of the hour. Most of the time I’d stop what was working on when it beeped and then use it to set a 10 minute timer. I’d use that time to eat a snack and/or walk around my house a little bit.
* The course material does not provide everything you need. Get used to doing your own research on services to see what is out there. Unfortunately you’ll occasionally find what appears to be an exact walk through of the box you’re on, so try to resist reading those. Two great pages to bookmark are:
	* http://www.fuzzysecurity.com/tutorials/16.html
	* https://blog.g0tmi1k.com/2011/08/basic-linux-privilege-escalation/
* Don’t be afraid to use the forums for help, but at the same time try each system without looking first. Also, realize that boxes may have been changed since a poster worked on it, or they could be completely clueless. Don’t let forum information give you tunnel vision.
* When you get stuck ask yourself what you’ve assumed, especially if you discovered something that may have caused you to end your enumeration prematurely.
* Don’t worry about taking hints or using metasploit at first- you’re learning and the confidence will come. But when you use metasploit ask yourself if you honestly know what it did and keep researching until you can say yes. Then take that info and see if you can do it manually.
* When deciding if you’re ready for the exam, note that it’s not just the number of systems you’ve done but how quickly and confidently you’re getting through them. I decided to schedule my exam when I had conquered 10 systems in a week while working a full time job. Another idea is to try out a mock practice exam where you choose 3-5 systems and just see how long it takes you to do them consecutively. If you still feel confident after that, you’re probably ready.
* This course will challenge you to think differently and have perseverance. If there wasn’t a bit of creativity required then pentesting would be left completely to automated tools. Don’t be afraid to try stuff that “shouldn’t work”.
* My biggest criticism of the course was how crowded the lab is. It is highly recommended that you revert every system to it’s original settings before attempting an attack and several times I had a machine reverted in the middle of my attack (another reason to take good notes!). Also, some machines required exploiting services that were unusable if another student was doing the same thing you were. This seemed to get worse as summer started so you may have a better experience at other times of the year.
