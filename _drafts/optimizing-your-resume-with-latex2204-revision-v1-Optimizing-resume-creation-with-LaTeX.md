---
id: 2209
title: Optimizing resume creation with LaTeX
date: 2018-03-20T00:17:39-05:00
author: Alan Verdugo
layout: revision
guid: http://www.kippel.net/blog/?p=2209
permalink: /?p=2209
---
<p style="text-align: justify;">
      For a long time I&#8217;ve had a love/hate relationship with my own resume.
</p>

<p style="text-align: justify;">
      Like most people, I started by writing a Microsoft Word document with any experience and knowledge I could remember. Having no design experience whatsoever, the result was an five-page abomination, every single row of it was a bullet point, listing a tool I knew or a job I had.
</p>

<p style="text-align: justify;">
      I was brave and fool enough to send this&#8230; &#8220;thing&#8221; to a recruiter and she said, to put it mildly, that it was too hard to read. Years later, I had another interview with this same recruiter and she still remembered me thanks to the fact that my resume was so ugly. This time I sent a newer resume and she compared both, saying that, at least, I was getting better at writing resumes.
</p>

<p style="text-align: justify;">
      That experience created in me a slight obsession with creating a better resume each time I had to update it. In turn, my obsession with learning things prompted me to update it regularly.
</p>

<p style="text-align: justify;">
      I started searching for Microsoft Word templates that I liked, modifying them and creating my own template exactly like I wanted it. This worked fine for a time, but I still had the feeling I could do better.
</p>

<p style="text-align: justify;">
      Once I started learning proper practices of version control systems, I realized that I could be using all this new knowledge to improve new versions of the most important document in my career. I also realized that most people do not do this, but it seems to be due to version control systems not entering popular culture yet.
</p>

<p style="text-align: justify;">
      So, where could I begin? Microsoft Word documents do have some primitive idea of keeping version tracking and comments, but that was not enough for me, specially because I was using <a href="https://www.libreoffice.org/" target="_blank" rel="noopener">LibreOffice</a> to create Word documents.
</p>

<h5 style="text-align: center;">
  Enter (and exit) JSON
</h5>

<p style="text-align: justify;">
      Around this time, I started working heavily with <a href="https://json.org/" target="_blank" rel="noopener">JSON</a> and I figured that its shapeless nature could translate well to a resume format.
</p>

<p style="text-align: justify;">
      As it happens with many software-related ideas, I quickly found out that other people had the same idea and there is already an open source project trying to make it a reality. In this case, it was the <a href="https://jsonresume.org/" target="_blank" rel="noopener">JSON Resume project</a>. While this project is very promising, it still does not deliver some important features. For example, the official schema does not provide a section to list certifications, you either list them as &#8220;education&#8221; or as &#8220;awards&#8221;, and I do not like either option. The fact that new versions of the official schema appear rarely, convinced me that this project could deliver what I wanted in some years, but not right now.
</p>

<p style="text-align: justify;">
      Another problem was that, in addition to JSON, I also wanted to have, at least, PDF and HTML versions of the same document. I wanted a write-once-import-to-many flow. While the JSON Resume tool does offer some conversion capabilities, the general results are just not very satisfactory. I wanted much more from what this could offer.
</p>

<h5 style="text-align: center;">
  Enter LaTeX
</h5>

<p style="text-align: justify;">
      With <a href="https://latex-project.org/" target="_blank" rel="noopener">LaTeX</a>, you can create any kind of document. It is specially useful to write complex mathematical formulas and, for that reason alone, it is very popular in the academia world. In fact, at first I got the idea that you could only write mathematical equations with LaTeX. But, thankfully, I was <em>very</em> wrong.
</p>

<p style="text-align: justify;">
      Some people have created LaTeX documents that I can only describe as works of art. The amount of freedom it provides is, at least to my knowledge, simply unparalleled.
</p>

<p style="text-align: justify;">
      The LaTeX syntax is not as easy to understand as JSON, but it is not too difficult. I would say it is as hard to master as Microsoft Word, which is obviously not much. The limitless potential behind LaTeX makes it worth it to spend a few hours getting the basics.
</p>

<p style="text-align: justify;">
      LaTeX has a long story, much longer to any of the alternatives I have mentioned so far. It was first released on 1985, so you could say it is pretty mature by now. Its typesetting system, the TeX project, was started in 1978 by Donald Knut (yes, <em>that</em> <a href="https://en.wikipedia.org/wiki/Donald_Knuth" target="_blank" rel="noopener">Donald Knuth</a>).
</p>

<p style="text-align: justify;">
      The best news was that there are also <a href="https://www.overleaf.com/gallery/tagged/cv#.WrCiuOZG1hE" target="_blank" rel="noopener">many LaTeX templates</a> that I could use to start . Not only I ended up with a resume exactly how I wanted it, but I learned a new skill, which now I can include in the resume itself. I also put my version control skills to good use.
</p>

<p style="text-align: justify;">
      My resume in now at my Github repository, where I can store it indefinitely and is also available to any slightly-technical recruiter. It only took me a few hours from researching about LaTeX until I had a complete document, so this is something that anybody could accomplish quickly and easily. Besides, there is a loyal and committed LaTeX community who has produced many guides, tutorials, and even WYSIWYG editors.
</p>

<p style="text-align: justify;">
      In addition to improving the document further (and having several styles), I want to make a more complete flow of the process. I imagine that in the very near future I will be pushing its new versions to <a href="https://github.com/alanverdugo" target="_blank" rel="noopener">my Github repository</a>, a <a href="https://jenkins.io/" target="_blank" rel="noopener">Jenkins</a> job will pick up the new changes, process them and automatically publish my resume in <a href="http://kippel.net/CV.pdf" target="_blank" rel="noopener">my personal page</a>. But I will talk about that in a future post.
</p>