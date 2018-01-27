---
title: 'I''ll take "Famous Titles" for $400 Alex.  #IVMOOC Week 4'
slug: content//blog/2015-02-12-ill-take-famous-titles-for-400-alex-ivmooc-week-4
---
Two posts in week, and two weeks of #IVMOOC down!
Topical analysis this week, and keeping in theme, here's what I'm doing.  Alongside setting up data architecture, moving research along, planning future moves, and comparing and contrasting frameworks (including engineering thinking, skills, accreditation, assessment and professional behaviour), I'm eating lunch, listening to Hidetake Takayama, writing this post and trying to figure out what to make for dinner.
Pretty much the same as everyone else!

Anyways.  I liked this week, but I got sidetracked with digging into visualizing data from twitter.  In the midst of watching one of the videos, I wanted to see how the #antivaxprof shenanigans were heating up or calming down.  I fired up R, figured out how to use the twitter API through ROAuth and TwitteR, and got to business. This is data from Feb 4th to 11th that contained #antivaxprof. I wanted to see graphically how tweets were being used, as in when tweets were originating and how they were progressing.  Below is the quick and dirty plot of that. Red dots are original tweets, greens are retweets of the same tweet.  Each plotted to the retweet count of the original.

![Twitter Viz]({{ site.url }}/assets/twitter-stuff.png)

Then I wanted to see how this was capturing the attention of the twittersphere, simply by looking at the frequency of tweets per day, and overlaying that with the total retweet count of all those tweets in a day.  (I guess the #IVMOOC workflow is sinking in.)  Enter plyr, and here is the quick and dirty of that.  I see this graph as showing that the public interest of the story declined in both activity and reach over time.  Thing about controversies and social media.  Short bursts of attention that die down, or at least settle only to those most affected.  I'm certain that this data is a little biased though, since twitter is just one small slice of the social media globe.

![Twitter Viz 2]({{ site.url }}/assets/twitter-2.png)

Then I went back to actually doing what I was supposed to be doing for #IVMOOC.  I searched the NSF grants database for "Engineering Education", and work on extracting and visualizing the word co-occurrence network in the titles.   Had to use a bit of scripting to get things the way I wanted it.

{% highlight python %}
resizeLinear(references,2,40)
resizeLinear(weight,.5,5)
colorize(references,gray,black)
g.edges.color = "34,94,168"
for n in g.nodes:
    n.x = n.xpos*40
    n.y = n.ypos*40
    n.strokecolor = n.color
    if (n.references > 20):
        n.labelvisible = true
{% endhighlight %}

A bit of time and some cleaning up in Affinity Designer, and I submitted this:

![IVMOOC Assignment 4]({{ site.url }}/assets/assignment-4.png)

I can see a lot of potential uses for this in my own work and research.  Fantastic week.  Next up: the midterm.  

*(Cue ominous music)*
