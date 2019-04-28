---
id: 2026
title: Getting out of the maze with A star
date: 2017-09-10T23:02:07-05:00
author: Alan Verdugo
layout: revision
guid: http://www.kippel.net/blog/?p=2026
permalink: /?p=2026
---
<p style="text-align: justify;">
      A local IT company (who shall remain unnamed in this post and shall be thankful for that) was offering free tickets to this year&#8217;s <a href="http://www.campus-party.org/" target="_blank" rel="noopener">Campus Party event</a> in Mexico. To get the tickets, you needed to complete a programming challenge. Since I&#8217;ve never attended any Campus Party* and I enjoyed solving the programming challenge for <a href="http://www.kippel.net/blog/?p=2017" target="_blank" rel="noopener">the Wizeline event</a>, I took some time to solve this one.
</p>

<p style="text-align: justify;">
      Basically, the challenge was to find the optimal way out of a squared, bi-dimensional maze. Using an API, you registered for the challenge, requested a maze of size <em>n</em> by <em>n</em>, then you were supposed to find the optimal path to get out of it (using a program, of course) and then you had to submit your path as a list of (x,y) positions, starting at (0,0) and finishing at a position where a goal (designated by &#8220;x&#8221;) was placed. An example of a small 8&#215;8 maze would be something like this:
</p>

<pre class="theme:solarized-dark font:ubuntu-mono font-size-enable:false toolbar:2 striped:false marking:false nums:false nums-toggle:false lang:default highlight:0 decode:true">11110000
00010000
00110000
00100000
00111000
00001000
00001000
0000111x</pre>

<p style="text-align: justify;">
      The zeroes are obstacles or walls, the ones are clear paths. So the solution in the previous example is obvious: (0,0), (0,1), (0,2), (0,3), (1,3), (2,3), (2,2), (3,2), (4,2), (4,3), (4,4), (5,4), (6,4), (7,4), (7,5), (7,6), (7,7).
</p>

    Here is another example:

<pre class="theme:solarized-dark font:ubuntu-mono font-size-enable:false toolbar:2 striped:false marking:false nums:false nums-toggle:false lang:default highlight:0 decode:true">1110111
0010101
1010101
1010101
1010011
1010110
1111x00</pre>

<p style="text-align: justify;">
      Which is still obvious. However, when I began to request mazes of bigger sizes I noticed the full complexity of the problem: There were many bifurcations and dead-ends. Of course, mazes are supposed to be confusing, that is the whole point of their existence. And not only that, I had to submit the shortest path from start to finish. That meant I could not use a brute-force method to find the goal by walking every possible path in the maze until I found it. The best part was that I had to solve a 1000&#215;1000 maze to claim the prize.
</p>

<p style="text-align: justify;">
      A 1000&#215;1000 maze might not sound very big, but once you think about all the possible configurations in that space, you realize it is not an easy task. Thankfully, getting out of mazes is a very old problem, pioneered by Cretan kings who wanted to hide away their funny-looking stepsons. For that reason, a lot of smart people have spent a lot of time trying to find the best solution to such a problem, better known as the &#8220;shortest path problem&#8221;. Among those people was <a href="https://en.wikipedia.org/wiki/Edsger_W._Dijkstra" target="_blank" rel="noopener">Edsger W. Dijkstra</a>, a dutch mathematician and a computer scientist who rarely used a computer. Dijkstra is one of the elder gods of computer science and now spends his afterlife looking disapprovingly at students who use GOTO statements.
</p>

<p style="text-align: justify;">
      In 1959, Mr. Dijkstra successfully designed an <a href="https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm" target="_blank" rel="noopener">eponymous algorithm</a> to find the shortest path between two points in any structure where there could be obstacles, varying distances, bifurcations, and dead-ends. This algorithm (or a <a href="https://en.wikipedia.org/wiki/Category:Routing_algorithms" target="_blank" rel="noopener">similar algorithm</a>, at least) is what mapping software uses to recommend trajectories (I believe Google maps uses <a href="https://en.wikipedia.org/wiki/Contraction_hierarchies" target="_blank" rel="noopener">Contraction hierarchies</a> since they need and can pre-compute routes in order to improve execution times).
</p>

<p style="text-align: justify;">
      One of these variations of Dijkstra&#8217;s algorithm is the <a href="https://en.wikipedia.org/wiki/A*_search_algorithm" target="_blank" rel="noopener">A* algorithm</a> (pronounced &#8220;A Star&#8221;). It was created in 1968 by Peter Hart, Nils Nilsson and Bertram Raphael, all of them Stanford scientists. A*, in turn, has many variations.
</p>

<p style="text-align: justify;">
      So, I used an implementation of the A* algorithm to successfully find the shortest path in the 1000&#215;1000 maze. I sent my solution and even when the API itself confirmed it was the optimal path to exit the maze, I never got the prize, not even a reply saying &#8220;Somebody solved it before you&#8221; or &#8220;We ran out of prizes&#8221;. I found that very unprofessional and irritating since the rules specifically said to send an email to a certain person notifying about the solution.
</p>

<p style="text-align: justify;">
      Since the Campus Party is now over and I am still a little salty about being ignored, I uploaded <a href="https://github.com/alanverdugo/tools/blob/master/maze_runner.py" target="_blank" rel="noopener">my solution to my Github repository</a>. It is a very quick and dirty solution, but it works, so don&#8217;t laugh too much (or better yet, improve it and create a pull request). Thankfully, I learned many interesting things and had fun doing this programming exercise so it was not a complete waste of time.
</p>

&nbsp;

* _The total number of actual parties I&#8217;ve attended tends to zero._