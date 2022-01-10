---
id: 2067
title: Analyzing movie rating data from an IMDB.com dataset using Python, Pandas and Matplotlib
date: 2017-11-29T09:26:14-05:00
author: Alan Verdugo
guid: http://www.kippel.net/blog/?p=2067
permalink: /blog/movie-data
#permalink: /?p=2067
categories:
  - Uncategorized
tags:
  - data science
  - english
  - IT
  - open source
  - programming
  - Technical writing
---
<p style="text-align: justify;">
      Since the dawn of cinema, the quality and enjoyment produced by motion pictures has been a complicated and controversial subject. An entire sub-industry has been created to review, criticize, recommend, analyze, categorize and rate movies. This, added to the subjective nature of each individual likes and dislikes has resulted in mixed experiences and expectations for the public. Some movies that are regarded as timeless classics by some people are seen as boring or even as bad movies by other people. The passing of time and the recent heavy use of special effects and CGI in movies also affect how the movies will be regarded in a few years, when those special effects look outdated.
</p>

<p style="text-align: justify;">
      However, we may find a general trend of increased satisfaction or dissatisfaction if we analyze a large number of movie ratings.
</p>

    The code I wrote for this analysis is available in <a href="https://github.com/alanverdugo/movies_analysis" target="_blank" rel="noopener">my GitHub repository</a>.

<h2 style="text-align: justify;">
  <a id="user-content-research-question" class="anchor" href="https://github.com/alanverdugo/movies_analysis#research-question" aria-hidden="true"></a>Research question
</h2>

<p style="text-align: justify;">
      Since many critics refer to their favorite period as the best era that cinema has to offer (or alternatively, that the movie quality is in decline), we will attempt to answer the following question:
</p>

<p style="text-align: center;">
  <strong>Has the perceived quality of movies increased or decreased over time?</strong>
</p>

<p style="text-align: justify;">
      For any answer we may find, we will demonstrate and provide a reason behind it in the form of data and its visualizations.
</p>

<h2 style="text-align: justify;">
  <a id="user-content-findings" class="anchor" href="https://github.com/alanverdugo/movies_analysis#findings" aria-hidden="true"></a>Findings
</h2>

<p style="text-align: justify;">
      Using an <a href="http://www.imdb.com/" rel="nofollow">IMDB.com</a> dataset, I analyzed 45,844 movies and 26,024,290 ratings for said movies. The oldest movie in the dataset was launched in 1874 and the newest in 2017.
</p>

<p style="text-align: justify;">
      I grouped the movies by launch year and calculated the average rating for the movies launched in every year. Doing this, I wanted to get an idea of the overall quality of the movies trough time.
</p>

<p style="text-align: justify;">
      While the technical aspect of motion pictures have obviously advanced thanks to new technology, it was not clear if this also improved the overall quality of the movie. In the next image I present a chart of the relation between launch year and average rating for the movies launched in each year.
</p><figure id="attachment_2068" aria-describedby="caption-attachment-2068" style="width: 1916px" class="wp-caption aligncenter">

[<img class="size-full wp-image-2068" src="https://raw.githubusercontent.com/alanverdugo/alanverdugo.github.io/master/wp-content/uploads/2017/11/movie_average_per_year.png" alt="Fig. 1 - Movie average rating per year." width="1916" height="916" />](https://raw.githubusercontent.com/alanverdugo/alanverdugo.github.io/master/wp-content/uploads/2017/11/movie_average_per_year.png)<figcaption id="caption-attachment-2068" class="wp-caption-text">Fig. 1 &#8211; Movie average rating per year.</figcaption></figure> 

<p style="text-align: justify;">
      Some interesting facts I got from this analysis:
</p>

<ul style="text-align: justify;">
  <li>
    The initial period (from 1874 to around 1915) is chaotic and experimental. A film could be under a minute long. There was little to no cinematic technique, the film was usually black and white and it was without sound.
  </li>
  <li>
    In the 1920s, begins a process of normalization. Movies are more popular and attainable. The public seem to have learned what to expect from directors and actors by this time. The primary steps in the commercialization of sound cinema were taken in the mid-to late 1920s, this could have helped to this normalization.
  </li>
  <li>
    2014 was a relatively disastrous year for cinema. The average rating for this year is 2.95. (The lowest since 1917, which is still part of the “experimental period”). The causes for this are beyond this analysis, but I will remind the reader that in 2014 we got movies like <em>Transformers: Age of extinction</em> and <em>Left behind</em> which <a href="https://www.rottentomatoes.com/m/left_behind_2014" target="_blank" rel="noopener">currently has a 1% score</a> in <a href="https://www.rottentomatoes.com/" rel="nofollow">rottentomatoes.com</a>
  </li>
  <li>
    In an scale from 0 to 5, The average tends to be slightly above 3. There is no noticeable increment or decrement from this average in the last century. So, to answer the research question, we cannot said that the quality of cinema has increased nor decreased substantially.
  </li>
</ul>

<h2 style="text-align: justify;">
  <a id="user-content-references" class="anchor" href="https://github.com/alanverdugo/movies_analysis#references" aria-hidden="true"></a>References
</h2>

<li style="text-align: justify;">
  History of film. (2017, November 26). In Wikipedia, The Free Encyclopedia. Retrieved 04:03, November 29, 2017, from <a href="https://en.wikipedia.org/w/index.php?title=History_of_film&oldid=812220038" rel="nofollow">https://en.wikipedia.org/w/index.php?title=History_of_film&oldid=812220038</a>
</li>
<li style="text-align: justify;">
  Sound film. (2017, November 28). In Wikipedia, The Free Encyclopedia. Retrieved 04:04, November 29, 2017, from <a href="https://en.wikipedia.org/w/index.php?title=Sound_film&oldid=812587250" rel="nofollow">https://en.wikipedia.org/w/index.php?title=Sound_film&oldid=812587250</a>
</li>