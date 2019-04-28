---
id: 2375
title: The angry employee dilemma
date: 2018-11-05T00:36:24-05:00
author: Alan Verdugo
layout: revision
guid: http://www.kippel.net/blog/?p=2375
permalink: /?p=2375
---
Recently, I read a rant on Linkedin. It was about why employees are supposed to give at least a two week notice when they want to resign, but at the same time, companies can fire employees at the drop of a hat and is common to ask them to leave the premises that same day. Until then, I didn&#8217;t even thought about this disparity, and it does seem unfair to employees. Most of the comments agreed that the company _should_ tell the employee that his position would be terminated soon. Another option would be that, if the company is not satisfied with the employee&#8217;s performance, it should counsel and explain the situation to the employee so they can improve and prevent said termination.

However, the comment that made me really interested in this discussion was from a manager. He claimed that this situation is normal and that companies are doing the right thing by firing employees and removing them from the company as soon as possible. His reasoning was that some employees &#8220;take it badly&#8221; and retaliate to the company by deleting crucial code or damaging the company&#8217;s IT infrastructure in some way, maybe even to the point of not being able to recover from it.

There are many flaws with this logic.

For now, I will ignore the fact that terminating and employee should be the very last resort for a company, let&#8217;s just assume the decision was made because there is no other option and that the employee, for some reason, definitively has to go and there is no way around it.

&nbsp;

An employee should not &#8220;take it badly&#8221;.

I know that nobody will be happy to be fired. People can and will take those news badly, but if one of my employees gets so angry that he tried to harm the company (or even worse, other employees) in some way, it either means I was not communicating properly that his or her termination was very probable, that the project was being cancelled or that there was another risk to the position. In short, a termination should not be a surprise to anybody, specially to the person being terminated.

This creates all sort of ramifications and different problems. After all, if I know that the project was probably being cancelled (for example) and I tell my employees, they will start looking for jobs and may leave the team without resources. This is actually very good for them and for you as a manager. It shows you care about their careers and their personal lives by being honest and respecting them. It just doesn&#8217;t make any sense to wait until the last second to share the bad news. If there are risks, the risks should be faced as soon as possible.

If the employee is being fired for just being a bad employee, we actually have the same situation. The employee should have been warned that he or she should improve or otherwise he or she would be terminated. How lenient the company should be with these warnings is a matter of another post, but the bottom line is the same: The employee should not be surprised that he or she is being terminated. They should either see it coming or should have not being fired at all because they did improve and their termination is no longer necessary. An unexpected violent reaction is only possible when the cause is equally unexpected.

The soft skills of the manager are obviously paramount here. They could be the only difference of a tragic conversation or a turn around in the employee behavior. This, again, is a matter of another post.

&nbsp;

Nobody should be able to bring the company to its knees.

This is the main point I want to cover: The technical side of firing somebody, specially in the IT industry.

Let&#8217;s assume again that the termination is imminent, but let&#8217;s also assume that the employee did &#8220;take it badly&#8221; and just wants to get revenge for this unfairness. Again, if the management team is doing things right, _this should never happen_. But I like having a plan B, and a plan Z, so just humor me and assume this is happening.

The original Linkedin comment said &#8220;[the angry terminated employee] could delete all the production code so you need to revoke their access before they do any harm&#8221;.

This is so wrong in so many levels. First of all, why would anybody be able to delete all of the production code? This only means there are no off-site backups of said code. A professional development team should never worry about somebody destroying their work, even if it the attack is coming from one of their own. Worrying about somebody deleting the only copy of the production code would be like using the old excuse &#8220;The dog ate my homework&#8221;. So what? You don&#8217;t have another copy of your homework? Can&#8217;t you just print it again right now? This is completely unacceptable and it was just disaster waiting to happen anyway.

Any development team should use a version control system (VCS) and every single member of the team should have a full copy of the code. Most modern version control system allow this very easily and Git, the most used VCS does this by default. I know this may sound extremely obvious for some readers, but you would not believe how many times I have seen &#8220;professional&#8221; and &#8220;world class&#8221; development teams not using any sort of code repository. You would specially not believe me if I said their names, so I just won&#8217;t name them, but more than one time I&#8217;ve said to myself: &#8220;If I delete this directory, I would be destroying their whole project&#8221;. I wish I was joking. Let&#8217;s just said you don&#8217;t want to be part of those teams, or being part of a team that does things like they do.

The DevOps methodologies also help to recover from disastrous scenarios. By treating the IT infrastructure as code, we can replicate and rebuild said infrastructure even if it goes down in the worst possible way.

So again, even if the big bad angry terminated employee manages to &#8220;delete the production code&#8221;, this should not be a major problem, just build it again from one of your many backups and you are up and running again.

Now, let&#8217;s take a moment to see this from a security perspective. Let&#8217;s say you have failed in doing all this and the employee is indeed able to cause serious problems to you and to the company. This is a huge red flag because, if an employee has the capabilities to do cause irreparable damage, it means a malicious hacker can also do it. When I wrote &#8220;Nobody should be able to bring the company to its knees&#8221;, I meant &#8220;NOBODY should be able to bring the company to its knees&#8221;.

Think about it, maybe all your employees are very happy and there is no need for terminations, but still, a hacker could get in and delete all your code because you didn&#8217;t have any backups or any way to recover from such an scenario. The worst part is that all this could happen without you noticing. It could happen on a Sunday at 4:00am! At least, if an angry employee was the attacker, you could be prepare for it before the termination, but you never know when a hacker could get inside your network. By failing to protect the company from internal attacks you are also failing to protect the company from external attacks. Again: This is completely unacceptable and it was just disaster waiting to happen anyway.