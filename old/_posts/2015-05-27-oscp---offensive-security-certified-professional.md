---
layout: post
title: "OSCP - Offensive Security Certified Professional"
tagline: "Try harder you must!"
category: certification
tags: [oscp, pwk, certification, pentesting, offensive, security]
---

I know there is already a whole truck load of OSCP reviews out there. But if you're anything like me, these
won't be enough. You want more. You want to soak in everything you can before diving into the labs and come out as
a pretty decent penetration tester. This is why I decided to sum up my experiences with the [_Penetration Testing with Kali Linux_](https://www.offensive-security.com/information-security-training/penetration-testing-with-kali-linux/)
course and the accompanying OSCP exam by Offensive Security. I even created this blog to share my thoughts.

This was definitely one of the most challenging things I have done in my career.
So let's dive right into it!

<!--more-->

### Intro

Ever since seeing my first buffer overflow, I've been excited with the (in)security of software and systems. A [_fellow student_](https://www.smrrd.de/) told me about penetration testing
and the PWK course (formerly known as PWB). I was impressed with his ability to pop shells over the network and decided I wanted to do that as well. I had played around with
several CTF-type challenges and a little bit of Reverse Engineering before but I wanted to formalize my education and see what I really knew. I quickly found out that there was a lot more to be learned. The PWK course offers a 
lot of opportunities to continue research on your own in order to get the most out of it. If there would be one thing I would tell soon-to-be OSCPs, it would be to do it for the
learning experience, not for the mere piece of paper. In the remainder of this post I want to share my experience from start to certification, including some tips I would have found useful before
starting the course. I hope you will, too! Additionally, over the next weeks, I will share a couple of techniques and scripts which I researched during my OSCP experience on this blog.

### Certification Process

Although there is a live training version of the PWK course, most students will want to register for the online version. You can register on [_Offensive Security's Registration Page_](https://www.offensive-security.com/preregistration.php?cid=21).
During registration, you can choose between 30, 60 or 90 days of VPN lab access. A lot of people wonder which is the right amount for them. However, you can't really go wrong since you can extend your time in the lab
as often as you like. With the amount of time I was going to be able to spend in the labs and my previous knowledge (see next section) I went for 60 days and extended for another 30 days this year
since I didn't get to take my exam after my first time in the lab. It all depends on how much time you are able to invest.

I initially registered so I could have my exam just before starting my final thesis for university. Since the course also collided with my final exams my stress levels were pretty
high during that time. In the end, I didn't get my exam done in time and postponed it to this year after getting settled in a new job. But that's the thing with the course, you can always
step back, learn more, try harder and come back to finish what you started.

After registration (with a corporate email address or proof of identity in case you try a free mail address) you receive course documentation in form of a pretty elaborate 
study guide and several hours worth of video material. Additionally, you receive your VPN connection package which allows you to connect to the student lab. Everything is pretty
clearly explained so with a standard Kali Linux installation including OpenVPN, you should have no trouble getting started. For more information on the registration and curriculum,
visit the [_official PWK offering_](https://www.offensive-security.com/information-security-training/penetration-testing-with-kali-linux/).

### Am I really ready for this?

A "[...] solid understanding of TCP/IP, networking and reasonable Linux skills." is what Offensive Security describes as the prerequisites to the course. This may or may not be sufficient
for you. While it's definitely true, the definition of "solid skills" may vary. From my standpoint, reasonable Linux skills are absolutely mandatory to get the most out of the course.
This means you should be able to do all sorts of daily tasks from the command line. This includes creating directories, editing files, grepping for stuff in files, searching for files (basically
everything around files), etc. This section includes several additional skills which I found useful, or would have found useful if I've had them beforehand:

#### Working on a command line

I mentioned it already but I want to extend my earlier point. Not only should you be able to control a Linux system, but Windows plays a big role in penetration testing as well. 
A key skill in which I certainly had (and still have) a lot of room for improvement is the Windows Command Line.
Especially with the incorporation of PowerShell, you have a powerful tool at your hand for penetration testing on Windows platforms. It offers capabilities from file transfer to 
managing Active Directory. I strongly recommend you check out [_nishang_](https://code.google.com/p/nishang/) which is a collection of PowerShell scripts for penetration testing, including
backdoors, keyloggers and other post-exploitation tools. For your start with PowerShell you can consult the official [_Microsoft TechNet Script Center_](https://technet.microsoft.com/en-us/scriptcenter/powershell.aspx).
Another great resource for PowerShell snippets (and a whole lot more useful information) is found in the [_Red Team Field Manual_](http://www.amazon.com/Rtfm-Red-Team-Field-Manual/dp/1494295504/). A book every aspiring 
pentester should have on his shelf.

Think of PowerShell as bash ported to Windows!

#### Reading, Writing and Debugging Code
During the PWK course, you will often encounter scripts, exploits and tools that are written by someone else. Because it is plain dangerous to run foreign code
on your system without knowing what it does (especially when it comes to exploits), a crucial skill is reading code. Preferably in multiple languages such as C, python, perl and ruby
to name some of the most popular ones. 

For writing your own code, I recommend that you learn to write simple scripts in your favorite language. I like Python a lot because there are modules for literally everything.
Other than that, bash is also helpful to get things done quickly. Get used to scripting everything you can because it will save you so much time!

Lastly, it won't hurt to get to know a little x86 assembly and debugging in general. Learn how to step through code and try to understand what it does. This will be crucial for exploit
development and for porting exploits to other platforms. I know that assembly and all the low-level stuff seems really scary. But at least for me, knowing my way around [_OllyDbg_](http://www.ollydbg.de/) from Reverse Engineering as a hobby helped
me to quickly grasp the Buffer Overflows in the PWK course. I recommend at least the first part of the amazing [_Exploit Writing Tutorial Series_](https://www.corelan.be/index.php/2009/07/19/exploit-writing-tutorial-part-1-stack-based-overflows/) by the corelan team.

You don't have to be an expert in any of the above since there is a lot covered in the course material. I just think you will get a lot more out of the course and your time in the lab if you 
sharpen your knife a little bit.

#### Prepare your toolbox
I was lucky to have a licence for VMWare Workstation since a proper virtualization platform is incredibly useful for the PWK course. Of course you can use a free virtualization
software such as VirtualBox as well. I used the most current Kali VM on VMWare which may differ slightly from the officially recommended version. But since a pentester should be able
to adapt and not just blindly run exploits, it may even be a good exercise. However, I would suggest not updating your OS between the final lab days and your exam because you might
mess up some important configurations. After every session in the labs I took a snapshot and backed everything up to a NAS. 

#### Preparing a comfortable Documentation Workflow (Including backups, obviously)
Since your final deliverable for obtaining the OSCP certification is a full-blown penetration test report, you should start to keep notes right away. You don't necessarily need
to submit a report for the labs but it may provide you with some additional points for your exam. I used KeepNote to keep detailed notes on every machine in the lab as well as on additional
research, exercises, cheat sheets and the like:

![KeepNote](https://n3ko1.github.io/assets/keepnote1.png){: .img-responsive}

As useful as KeepNote is to organize your thoughts and to keep track of your exploits, I strongly recommend to prepare and write your lab report (Word or OpenOffice) in parallel.
I failed to finish my lab report in time because I couldn't quickly compile it from my notes. My note organization didn't match the recommended report structure and KeepNote gave me 
a hard time exporting the actual notes into something useful. Fortunately I had enough points during my exam but after putting all these hours in it was frustrating nontheless.

As a final thought: make sure to keep your notes constantly backed up. I used my personal NAS, but any cloud hosting provider (Dropbox etc.) will do. And as with any good backup, know
how to restore your files if something goes wrong.

### Study Material
The study material for the PWK course consists of a 365-pages PDF lab guide and several hours worth of videos. The lab guide is fantastic and touches on a variety of topics
ranging from finding your way around Kali Linux over bash scripting and network sniffing to exploit development and some seriously confusing tunnelling techniques. For most chapters, it leaves
exercises to the reader and challenges you to conduct further research on your own. If you're like me, you will be so intrigued by some of the techniques that this part will be the most fun.
As with anything they do, Offensive Security will challenge you to try harder. Don't just read through the guide, try to understand every little detail and work through every exercise. It will
definitely pay off in the long run.

The videos, which are intended to support the lab guide, are really good, as well. Personally, however, I don't like video tutorials that much since I am forced to follow a given speed and I don't
have the level of control I have when reading. But since the videos contain some additional information, you should go ahead and watch them, anyway.

Since I started when the course was still called Pentesting with Backtrack, I can confirm that Offensive Security does a good job on keeping the material up to date.
Some techniques may be somewhat outdated, but they are still the basis for a lot of common attacks today. There is no need to develop a ASLR- and DEP-bypassing exploit if you don't
understand the magic behind the actual buffer overflow vulnerability. So kudos to Offensive Security for keeping the material relevant while still sticking to the very basics.
The upgrade process itself was very smooth for me. I was eligible for a free upgrade, was sent detailed information on how to get my new course material and connect to the new PWK labs.
According from the official pricing page, you now have to pay a fee to upgrade from PWB. But I think if there is an update during your certification process, you will get it for free.

For more information on the content of the course, check out the official [_Course Syllabus_](https://www.offensive-security.com/documentation/penetration-testing-with-kali.pdf).

### Back to the Lab!
Just a couple of days after the exam and all the humbling frustration earned through Pain and Suffering I already started to miss the labs. That's how good they are.
The virtual lab environment is really the essence of this course. You are given access to an environment with around 50-60 machines of different flavors from Windows and Linux
clients with different patch levels to various server systems. You will encounter mail servers, web servers and even bots that do certain exploitable actions in the environment. 
Additionally you have a personal Windows machine to test your exploits and train your debugging skills. I recommend
to start your journey to the labs as soon as the first enumeration techniques are discussed in the lab guide. Try to understand the technique and find a target to apply your newly
learned skills to. Rinse and repeat. Then script everything you learned and continue. The real beauty of this course is that you are given a great sandbox and accompanying material
to really dive deep into the rabbit hole. Always go the extra mile to research a little more on the techniques you encounter. This will give you a great advantage when the exam comes around.

Some of the machines can be exploited really easily. But the learning curve is very steep and you should avoid to fully rely on Metasploit for your exploitation process. Try to understand
the more simple attacks completely or you will find yourself stuck on the harder machines. Metasploit is restricted during the exam so learn to ride without the training wheels. 
You are able to revert the machines and you should absolutely make use of this feature. Always
revert a machine before even looking at it. Services might have crashed from other students tampering with the system, additional services may appear and so on. Yes, you may piss off other 
students. But that's part of the game and part of why you should always document your findings immediately.

Make sure you do not only train individual techniques but to build a strong methodology. First enumerate, enumerate and enumerate just a little bit more. Document everything you see and find
interesting. Open ports, services, web pages, user names, OS versions, you name it. Be structured in your exploitation attempts. Document what you have tried, what worked and what didn't and why.
After successful exploitation, don't just move on to the next system. Without giving away anything: it may prove interesting to look at the owned systems a little more closer.
Again, a word on documentation. Compile your report in time. I recommend you update your full report every few machines to not be overwhelmed by the work load like I was.

A lot of people ask how much time you need to invest in the course to root every machine and to handle the exam. That is a tough question as it depends on multiple factors. Your previous
skills, methodology and even luck come into play. I took a lot of time to research the things I learned which held me off from exploiting every single system. However, I managed
to get to every subnet in the lab and owned some of the more tricky systems such as Pain and Suffering. All in all I had 90 days in the labs with a year-long break in between. On my last
30 days I invested around 4-5 hours a day. It is hard but I managed to fit it in between a full time job and other responsibilities. Thanks to my awesome girlfriend for supporting my dream!

One final piece of advice for your time in the labs. Try to get on the IRC channel early on. You won't get a lot of help from the admins if you expect plain answers. But there are a lot
of other students there and it's really good to have a partner in crime to discuss exploits and attack strategies with. You will notice that no aspiring OSCP will just give away anything. You can
discuss, ask questions, share thoughts. This makes your isolated life during the course easier. Thanks to [_Evangelos Mourikis_](https://vagmour.eu/) \([_@teh_h3ck_](https://twitter.com/teh_h3ck)\) for
helping me through the last weeks!

### Exam Preparation
In my case, I booked my exam a couple of weeks after my lab time ended. I planned to prepare extensively but since I had a lot of other stuff on my plate I guess I did a lousy job on that.
Primarily, my preparation consisted of organizing my notes and cheat sheets and preparing all scripts I gathered during lab time. I also tried to write my lab report which I failed to finish.
These are my tips on preparing for the exam, even if your time is limited.

#### Organize your thoughts. And everything else.
During your lab assignment you will gather a huge amount of information. This includes attack vectors, exploits and payloads for specific machines, general techniques, scripts, links and more.
You should take your time to organize everything in a manner that you can quickly access and grasp it during the exam. I created a folder structure on my Kali machine with something similar to this:

    .
    |-- enumeration
    |-- exploitation
		|-- exploits
			|-- ms08-067.c
    |-- post_exploitation
		|-- file_transfer
		|-- gathering
			...
		|-- privilege_escalation
			|-- privchecker.py

I think you get the idea. I tried to map my organization to the methodology I wanted to use for the challenges encountered during the exam. If you want to go the extra mile you
can pre-compile all privilege escalation exploits you used in the labs and organize them accordingly. This might save you a lot of time in the exam.

I kept all other information in my KeepNote notebook while creating a separate notebook for the exam. This way, the exam notebook would only contain information relevant to the final
report and I could look up previous attack strategies, cheat sheets and bookmarks in the other one. In fact, during the exam, it might be useful to think back to some of the techniques
you applied to the lab machines. Even if it's just a special flavor of a file transfer technique: it might save you time! As well as blood, sweat and tears of course.

#### Scripting as a way of life.
I mentioned it before and I'll stick to it. Script as much as possible. In fact, I did not realize this at first and ended up fiddling together existing scripts with my own thoughts which
wasn't pretty but got me through the exam. Just in case you don't know where to start scripting, here are a few examples:

**Enumeration**

You probably guessed it. There is a flood of brilliant tools for enumerating all kinds of things. But instead of running them manually one after another, you can streamline your process into
one handy tool. During the exam I used a slightly modified version of the [_Recon Scan Script by Mike Czumak_](http://www.securitysift.com/offsec-pwb-oscp/). He has a great blog post on the OSCP
including multiple really useful tips and scripts. After obtaining my certification I wanted to do things differently which is why I started a little project called _WrapMap_.

Basically, WrapMap offers a wrapper around nmap using the [_python-nmap library_](http://xael.org/norman/python/python-nmap/) in a slightly modified version. It runs asynchronous
nmap scans and executes custom modules based on the results. In the modules you can do everything you want to and return results to the main script which writes
a bunch of output files. The tool is intended to be used when nmap NSE scripts don't cut it and you want to incorporate other tools (sqlmap, nikto, ...) in your enumeration script.
The tool is open source and I would love to see some modules be contributed! You can find it here: [_WrapMap on GitHub_](https://github.com/n3ko1/WrapMap).

**File Transfer**

I really profited from scripting all different techniques around file transfers (i.e. not simple (T)FTP). For example, I wrote a script which automated the process of logging in to
a WordPress page, editing a template of your choice to include your PHP backdoor and uploading a binary file to Windows using the _debug.exe_ technique. Mastering and scripting these
techniques will save you time and trouble in situations where you need to get a file to a target. In fact, I will dedicate a separate blog post in the future to file transfer techniques.

**Privilege Escalation**

Privilege Escalation was one of my weak spots going into the exam. However, there are some really great resources on the topic which help you understand it and script
a lot of the steps. Check out the following links: [_Basic Linux Privilege Escalation_](http://blog.g0tmi1k.com/2011/08/basic-linux-privilege-escalation.html) and [_pentestmonkey_](http://pentestmonkey.net/category/tools/audit).
The latter is also a great resource for other cheat sheets and little helper scripts.

As you see, a lot of things have already been created. You should take that as a challenge to build your own tools on top to exactly do what you want them to do.
And in the process, you will notice that you suddenly understand things on a whole different level. And if you do build cool stuff, make sure to share it!

To sum it up, if you managed to penetrate the majority of systems in the lab you have a great starting point for the exam. On top of that, organization and automation are key
to success in my opinion. Make sure to align everything with a strong methodology and you should be good to go. And don't forget to get a good night of sleep!

### The Big Day!
I started my exam on a Friday at 10 AM. Offensive Security sent me my connection package just in time including a really exhaustive set of instructions.
They did a great job explaining everything in such detail that you know exactly what you are expected to do, what is allowed in terms of tool usage and how many
points are assigned to which challenge. So don't worry too much, all will be clear when the big day arrives.

They give you 23 hours and 45 minutes to complete the exam in which you have to achieve at least 70 out of 100 possible points to pass. After that you have an additional 24 hours 
to submit your exam report. You do not _have_ to submit a report on the student lab but it may give you some points if you are on the "passing edge". So I strongly recommend to _not_ follow my example.
I started out on one of the seemingly easy challenges worth 10 points. And was completely lost. After 3 hours of nothing I switched to a 30-point target and had it cleared until (an arguably late) lunch. After that
it took me until 3 AM on the next day to achieve the minimum score of 70 points. With immense relief and a mental state of complete lunacy I decided to quit. I slept soundly and wrote my report
the next day in another 6 hour session (103 pages). On Tuesday I received the often-dreamed-about confirmation of certification:

![OSCP](https://n3ko1.github.io/assets/cert.png){: .img-responsive}

I want to conclude this section with some lessons learned:

* Get enough rest before your exam
* Take frequent breaks, keep hydrated
* Don't be fooled by point values. I completed all challenges _except_ the ones worth 10 points.
* Stick to your methodology! There will be a time during your exam where you hammer your keyboard trying the same failing exploit again and again. Take a step back!
* Write and submit your lab report. Seriously, it will reduce your stress level when finishing the exam with minimum points and no safety net.
* Manage your time. Stick to a target but don't be afraid to move on if nothing seems to work.

### Conclusion
It's easy to say that this was the greatest certification I obtained in my career since it is my first. Whether or not the piece of paper enhances my CV, the learning
experience was absolutely amazing. It is true that you find all the information from the lab guide somewhere on the internet for free. But the main selling point is the 
virtual lab environment. It is set up perfectly to teach and intrigue you, to tease and infuriate you. You will find hidden features, even laugh out loud.
I can only recommend it to anyone who want to break into the wide field of penetration testing.

Thanks Offsec for this experience! I will be back and try even harder.

