---
id: 2389
title: Hosting a cyber-security workshop for a software development team
date: 2022-12-19T11:21:36-05:00
author: Alan Verdugo
guid: http://www.kippel.net/blog/?p=2389
permalink: /blog/security-workshop
categories:
  - Review
tags:
  - english

---

I was asked to run a security workshop for my team and, since this was my first time with a workshop aimed at security, I must confess that at first I had no idea of what I should do to make it both educational and entertaining.

First, I was tempted to just talk about our security tools, and do demos on how to use them, but that would have been boring for everybody. Most of our security tools are already fully automated, so there was not much I could show other than some scripts being executed. Besides, this was supposed to be a *workshop*, so the interactive aspect is probably the most important part.

Overall, this was a great experience. I learned many things and received good feedback, so in this post I will explain how I did it, what topics were covered and some thoughts about security and workshops in general.

## Choosing the tools

I started researching about how to plan a cyber-security workshops, and quickly found many interesting projects, including [Google's Gruyere project](https://google-gruyere.appspot.com/) and [DVWA](https://github.com/digininja/DVWA) (or "Damn Vulnerable Web Application").

I eventually chose a combination of two open source projects: [CTFd](https://ctfd.io/) and the [OWASP Juice Shop](https://owasp.org/www-project-juice-shop/). Together, they allowed me to put together exactly what I needed: An interactive and engaging way to teach the team about the importance of cyber-security.

### OWASP Juice Shop

The OWASP Juice Shop is a vulnerable-by-design fictitious e-commerce site. Since it is an OWASP Flagship project, it includes vulnerabilities from the [OWASP Top 10](https://owasp.org/www-project-top-ten/), among many others. The application is supposed to be run by each participant of the workshop. Thankfully, there is a container image available, which made this very easy for everybody.

<p align="center"> 
    <img src="https://raw.githubusercontent.com/alanverdugo/alanverdugo.github.io/master/_posts/security_workshop/juice_shop.png">
</p>

This project has [really good documentation](https://pwning.owasp-juice.shop/). It even includes advice on [hosting a CTF competition](https://pwning.owasp-juice.shop/part1/ctf.html), which was extremely useful.

What I really loved about the Juice Shop is that it also includes challenges that can be solved without any technical knowledge. It even includes social engineering challenges. This was really important for me, because I wanted the team to understand that sometimes it is trivially easy to cause damage to production systems. I also wanted the non-technical members of the team to know that they also had a chance at winning the competition. I really wanted *everybody* to participate because security should be a main concern for every single member of the team.

### CFTd

CTFd is a "cyber-security training platform". Basically, a server from where you control all aspects of the training sessions. It needs to be centralized, so I created an AWS EC2 instance and executed CTFd with Docker Compose. Then I shared the URL with the team and asked them to create their accounts.

It is in the CTFd web interface were participants register, read the challenges and submit the "flags" they have found in order to get points.

<p align="center"> 
    <img src="https://raw.githubusercontent.com/alanverdugo/alanverdugo.github.io/master/_posts/security_workshop/challenges.png">
</p>

CTFd has a [managed option](https://ctfd.io/pricing/) in case you don't have time to set it up on your own. There is also a [live demo](https://demo.ctfd.io/), so you can get familiar and see if it satisfies your requirements.

## Capturing The Flags

Competitions make everything more interesting, and I really wanted to add some excitement to the workshop since I was unsure about the team's interest in cyber-security. We are primarily a software development team, and security should be a major concern, but I know that many developers still have the mentality of "If the code runs, it is good enough", and I wanted to convince them to "think like hackers" in order to prevent security problems in our applications.

To encourage participation, when the CTF exercise started I told everybody that the 3 participants with more points would be awarded "Bluepoints"- 200 to the winner, 100 to the second place and 50 to the third place. These Bluepoints then could be exchanged for many different products in the online store of our employee rewards program.

In the competition, the participants go to the CTFd web interface and read one of the challenges, then they solve it using their own instance of the Juice Shop. Once they find the solution, they will receive a "flag" which is just a string of characters. Then, they will go back to the CTFd interface and input the flag, which will award them the respective points for that challenge.

The CTF competition lasted for 10 days. Regardless of their daily duties, I wanted to give everybody time to participate in the competition, so I tried to extend it as much as possible.

The following is the final scoreboard of the competition showing the 3 winners. As you can see, they started slowly but quickly picked up the pace.

<p align="center"> 
    <img src="https://raw.githubusercontent.com/alanverdugo/alanverdugo.github.io/master/_posts/security_workshop/scoreboard.png">
</p>

The following are some competition statistics, produced automatically by CTFd:

<p align="center"> 
    <img src="https://raw.githubusercontent.com/alanverdugo/alanverdugo.github.io/master/_posts/security_workshop/statistics.png">
</p>

<p align="center"> 
    <img src="https://raw.githubusercontent.com/alanverdugo/alanverdugo.github.io/master/_posts/security_workshop/statistics_2.png">
</p>

When the competition ended, I asked the winners to share how they solved some of their challenges, so we all could learn from them. This also encouraged discussion and ideas about different approaches.

Here's the rundown of the all topics we talked about during the workshop:

- Reasoning behind the workshop.
- Data breaches case studies.
- OWASP and OWASP top 10.
- Whitesource/Mend.
- Capture The Flag competition.
- The importance of strong passwords.
- Brute force attacks.
- Rainbow tables.
- General Q&A

## Conclusion

I really liked how CTFd and the OWASP Juice Shop projects made it easier to prepare the whole workshop. They are mature projects and the best I could find amongst the many alternatives that have the same goals. I was just a little confused at first about how they were supposed to work together and how to configure them. This is one of the reasons why I wrote this post.

Since the team is quite young, I allowed them to see the Hints for each challenge. In a future workshop, and depending on the experience of the participants, maybe I would make the challenges harder to solve, or enable the "pay for hints" feature, which would encourage a more strategic approach ("Should I pay 200 points for a hint that may or may not help me get 300 points?").

I noticed that even when they were competing individually, some people joined and started discussing and bouncing ideas about how to solve the harder challenges, which was great. So, for a future workshop I may enable the Teams feature in CTFd. However, I am afraid the most senior members would form stronger teams, discouraging the younger members to even attempt to compete.

In general, my objective was for team to learn these important points:

- Hacking is not something that only happens in movies. It could happen any day, to anybody, and history has shown that it could be disastrous if you are not prepared.
- Some attacks are very easy. You don't have to be an expert penetration tester to find and solve security problems in your application. There are tools that can help you with this.
- Security is a team sport. It does not matter if you consider yourself to be "non-technical". Everybody should be aware of how important this is, and have the right mindset to prevent and solve these problems.
