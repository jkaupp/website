---
title: 52Vis - Homeless
slug: content//post/2016-04-12-52vis-homeless
---

I've a confession to make.  I'm a terrible blogger.  I do so out of need and interest, and I've a lot of the latter but little of the former.

>"The game has changed." <cite>Clu</cite>  

(Yes, Tron Returns. Get over it.)

Bob Rudis, @hrbrmstr, a useR, visualization practitioner, data-driven security expert, blogger has constructed a wonderful set of information visualization challenges for the next year.  (There goes my free time).  I was a little late to the party and missed the first week due to massive family sickness, but I'm going to try to follow along and participate for the coming weeks.

This week's task is outlined on [hbrmstr's blog](https://rud.is/b/2016/04/06/52vis-week-2-2016-week-14-honing-in-on-the-homeless/).   In short its looking at US Department of Housing data on the homeless population in the USA and producing a truthful, insightful and effective visualization of the data.  This is an emotionally charged data set and I kept thinking about it all week.  Not only from the perspective of what questions I wanted to answer with my visualization, but from the perspective of someone who's been fortunate enough to have a home, a family and a great deal of opportunity and what that _means_ to me.

Some may say that data is just numbers, and that it's hard to connect to it.   I don't think it is.  Data always represents something, and in this case it represents real people in a terrible situation.  I believe that keeping that in mind connects you to the data, keeps you honest and motivates you.  

> "that's all I have to say about that" <cite>Forrest Gump</cite>

I explored the data, producing scatterplot matrices and looking for interesting relationships.  Then I realized that I wanted to see what was being done to help the homeless people.  Most US government funding is made public, so I took a walk over to the Department of Housing, found the Community of Care Program grant awards by state and integrated that into the analysis.  (I don't know if this is cheating, but I wanted to see the funding and its effects on the homeless population).  This is still VASTLY incomplete and only sheds some light on a small sliver of the entire story (support and funding don't fix the problem, but it can help).  This line of analysis is very nuanced and very deep.  This little bit of work is a grain of sand in the Sahara.

I'm a fan of Alberto Cairo and his work.  His books are fantastic, great reads and are highly recommended.  In "The Functional Art" he used an image from Epoca magazine that is a scatterplot with each point representing summary values for a year on a separate x and y scale.  These can be connected illustrating how these relationships change over the years.  I don't know what it's officially called, but I call it a temporal scatterplot.  I thought this would be a fantastic fit for my intended visualization.    

I thought this was best represented at two levels, National and State.  This provides the "Big Picture" as well as the capturing the smaller stories that differ between the states.  I believe if you only present one of these, it's terribly misleading as the aggregate always smooths out the individual bumps and assumes homogeneity where none exists.

First up, the National "Big Picture". The homeless population and funding data were aggregated by year and charted homeless population vs coc funding and with a spline connecting each point. (Thanks to @hrbrmstr for the ggalt package and the tip on geom_xspline2)

![National]({{ site.url }}/assets/National_level_hud_coc.svg)

This shows overall that funding has only been increasing over the years and the homeless population has been declining.  However, what is going on 2010 with the increase in the homeless population?  This is where further research and additional analysis can shed some light on a situation.  My initial cursory research reveals that this was the year ending the Iraq war, the 'flash crash', and the bottoming of the jobs market post recession.  That's a lot of causes, should someone with more expertise want to keep going.

Next up, the State-level results.  The homeless population and funding data were aggregated by year and state, normalized to population and displayed per 100,000 people.  They are plotted similarly to the National level, with the addition of small multiples for each state.  The multiples are arranged according to the funding they received.

![State]({{ site.url }}/assets/state_level_hud_coc.svg)

This illustrates a vastly different picture than the National level.  It shows wild swings in both funding and homeless population and directly challenges the Big Picture view of throwing money at a problem.  Look at the the first three panels, look at Rhode Island, Vermont and Alaska.  Something really odd is happening that warrants a closer look.  Ultimately, these differences and odd relationships lend support to my initial statement that this is far more complex and requires a great deal more thought, investigation and expertise than I can provide.  It also directly challenges one unstated assumption of my own, that the funding and homeless population are variables that are in-phase, when most likely they are lagged in an cyclical cause-effect loop.

I also thought that both might be better served as interactive documents, so I added some yaml and roxygen comments to use rmarkdown::render() (which calls knitr::spin) with the shiny runtime to produce a simple interactive html document direct from the R code.   The ggplot code to produce the static images is there too, you can either change the include options to show either static or interactive but be sure to uncomment the actual call to the plot object.

You can view the interactive version on my *[shinyapps.io account](https://jkaupp.shinyapps.io/52vis_Homeless/)*

If you're interested in seeing what I did, simply go to my github (link in sidebar) and check out the code.  I've included png and svg versions, and all of the data.

All in all, while I enjoyed the challenge, it gave me far more to think about than simply visualizing information.
