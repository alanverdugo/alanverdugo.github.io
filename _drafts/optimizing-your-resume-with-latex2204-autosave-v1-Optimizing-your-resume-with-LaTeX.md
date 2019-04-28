---
id: 2219
title: Optimizing your resume with LaTeX
date: 2018-03-25T00:00:42-05:00
author: Alan Verdugo
layout: revision
guid: http://www.kippel.net/blog/?p=2219
permalink: /?p=2219
---
<p style="text-align: justify;">
      For a long time I&#8217;ve had a love-hate relationship with my own resume.
</p>

<p style="text-align: justify;">
      Like most people, I started by writing a Microsoft Word document, including any experience and knowledge I could remember. Having no graphic design experience whatsoever, the result was an five-page abomination, every single row of it was a bullet point, listing a tool I knew or a job I had.
</p>

<p style="text-align: justify;">
      I was brave and/or fool enough to send this&#8230; &#8220;thing&#8221; to a recruiter and she said, to put it mildly, that it was too hard to read. Years later, I had another interview with this same recruiter and she still remembered me thanks to the fact that my resume was so atrocious. This time I sent her a newer resume and she compared both, saying that, at least, I was getting better at writing resumes.
</p>

<p style="text-align: justify;">
      That experience created in me a slight obsession with creating a better resume each time I had to update it. In turn, my obsession with learning prompted me to update it regularly.
</p>

<p style="text-align: justify;">
      I started searching for elegant Microsoft Word templates, modifying them and creating my own template exactly like I wanted. This worked fine for a time, but I still had the feeling that I could do better.
</p>

<p style="text-align: justify;">
      Once I started learning proper practices of version control systems, I realized that I could be using all this new knowledge to improve new versions of the most important document in my career. I also realized that most people do not do this, but it seems to be due to version control systems not entering popular culture yet.
</p>

<p style="text-align: justify;">
      So, where could I begin? Microsoft Word documents do have some primitive idea of keeping track of versions and comments, but that was not enough for me, specially because I was using <a href="https://www.libreoffice.org/" target="_blank" rel="noopener">LibreOffice</a> to create Word documents.
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
      Another problem was that, in addition to JSON, I also wanted to have, at least, PDF and HTML versions of the same document. I wanted a write-once-import-to-many flow. While the JSON Resume tool does offer some conversion capabilities, the general results are just not very satisfactory. I wanted much more from what this project could offer at the time.
</p>

<h5 style="text-align: center;">
  Enter LaTeX
</h5>

<p style="text-align: justify;">
      With <a href="https://latex-project.org/" target="_blank" rel="noopener">LaTeX</a>, you can create any kind of document. It is specially useful to write complex mathematical formulas and, for that reason alone, it is very popular in academia. In fact, at first I got the idea that you could <em>only</em> write mathematical equations with LaTeX. But, thankfully, I was <em>very</em> wrong.
</p>

<p style="text-align: justify;">
      Some people have created LaTeX documents that I can only describe as <a href="https://www.tug.org/texshowcase/" target="_blank" rel="noopener">works of art</a>. The amount of freedom LaTeX provides is, at least to my knowledge, simply unparalleled. It allows to create stunningly beautiful documents. Just imagine trying to create something like the following in Microsoft Word:
</p><figure id="attachment_2210" aria-describedby="caption-attachment-2210" style="width: 648px" class="wp-caption aligncenter">

[<img class="size-full wp-image-2210" src="http://li106-124.members.linode.com/blog/wp-content/uploads/2018/03/latex01.png" alt="D. Taraborelli (2008). The Beauty of LATEX. Some rights reserved. cc-by-sa" width="648" height="449" />](http://li106-124.members.linode.com/blog/wp-content/uploads/2018/03/latex01.png)<figcaption id="caption-attachment-2210" class="wp-caption-text"><a href="http://www.nitens.org/taraborelli/latex" target="_blank" rel="noopener"><em>D. Taraborelli (2008). The Beauty of LATEX. Some rights reserved. cc-by-sa</em></a></figcaption></figure> 

&nbsp;<figure id="attachment_2215" aria-describedby="caption-attachment-2215" style="width: 640px" class="wp-caption aligncenter">

[<img class="size-full wp-image-2215" src="http://li106-124.members.linode.com/blog/wp-content/uploads/2018/03/gene.png" alt="Colored Lettrines by Raphink." width="640" height="287" />](http://li106-124.members.linode.com/blog/wp-content/uploads/2018/03/gene.png)<figcaption id="caption-attachment-2215" class="wp-caption-text">_<a href="https://github.com/raphink/coloredlettrine" target="_blank" rel="noopener">Colored Lettrines by Raphink.</a>_</figcaption></figure> <figure id="attachment_2211" aria-describedby="caption-attachment-2211" style="width: 972px" class="wp-caption aligncenter">[<img class="size-full wp-image-2211" src="http://li106-124.members.linode.com/blog/wp-content/uploads/2018/03/latex02.png" alt="Steve Seiden's theoretical computer science cheat sheet." width="972" height="828" />](http://li106-124.members.linode.com/blog/wp-content/uploads/2018/03/latex02.png)<figcaption id="caption-attachment-2211" class="wp-caption-text"><a href="https://www.tug.org/texshowcase/cheat-20131114.tar.gz" target="_blank" rel="noopener"><em>Steve Seiden&#8217;s theoretical computer science cheat sheet.</em></a></figcaption></figure> <figure id="attachment_2212" aria-describedby="caption-attachment-2212" style="width: 982px" class="wp-caption aligncenter">[<img class="size-full wp-image-2212" src="http://li106-124.members.linode.com/blog/wp-content/uploads/2018/03/latex03.png" alt="LaTeX facsimile of a Bible de Genève, 1564." width="982" height="1507" />](http://li106-124.members.linode.com/blog/wp-content/uploads/2018/03/latex03.png)<figcaption id="caption-attachment-2212" class="wp-caption-text"><a href="https://github.com/raphink/geneve_1564" target="_blank" rel="noopener"><em>LaTeX facsimile of a Bible de Genève, 1564.</em></a></figcaption></figure> 

&nbsp;

<p style="text-align: justify;">
      LaTeX has a long story, much longer to any of the alternatives I have mentioned so far. It was first released on 1985, so you could say it is pretty mature by now. Its typesetting system, the TeX project, was started in 1978 by Donald Knuth (yes, <em>that</em> <a href="https://en.wikipedia.org/wiki/Donald_Knuth" target="_blank" rel="noopener">Donald Knuth</a>).
</p>

<p style="text-align: justify;">
      The LaTeX syntax is not as easy to understand as JSON, but it is not too difficult. The limitless potential behind LaTeX makes it worth it to spend a few hours getting the basics. That, in addition to the organization that a version control system delivers, meant that not only I could design my resume, but now I could easily design it, program it, compare it, automate it, store it, and share it.
</p>

<p style="text-align: justify;">
      The best news was that there are also <a href="https://www.overleaf.com/gallery/tagged/cv#.WrCiuOZG1hE" target="_blank" rel="noopener">many LaTeX templates</a> that I could use to start. So, not only I ended up with a resume exactly how I wanted it, but I learned a new skill, which now I can include in the resume itself. I also put my version control skills to good use. I used the <a href="https://www.overleaf.com/latex/templates/awesome-source-cv/wrdjtkkytqcw#.WrM7BdYh1hG" target="_blank" rel="noopener">YAAC: Another Awesome CV</a> template by Christophe Roger. It is elegant, simple, it has a lot of potential and its code is very well organized. I noticed that it also lacked a certification section but I was able to add it easily by studying his code.
</p>

<p style="text-align: justify;">
      My new resume in now at <a href="https://github.com/alanverdugo/resume" target="_blank" rel="noopener">my GitHub repository</a>, where I can store it indefinitely and is also available to recruiters. It only took me a few hours from researching about LaTeX until I had a complete document, so this is something that anybody could accomplish quickly and easily. Besides, there is a loyal, helpful and committed LaTeX community which, through the years, has produced many guides, tutorials, and even WYSIWYG editors, so the learning curve is not as hard as it may seem.
</p>

<p style="text-align: justify;">
      In addition to improving the document further (and having several styles), I want to make a more complete flow of the process. I imagine that in the very near future I will be pushing its new versions to my GitHub repository, a <a href="https://jenkins.io/" target="_blank" rel="noopener">Jenkins</a> job will pick up the new changes, process them and automatically publish my resume in <a href="http://kippel.net/CV.pdf" target="_blank" rel="noopener">my personal page</a>. I will talk about that in a future post. For now, feel free to take a look at the code, offer some feedback, fork it, create a pull request, send it to your friendly neighborhood recruiter, or do whatever you want with it.
</p>