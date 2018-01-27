---
title: 'Goofus and Gallant: Charts'
slug: content//post/2015-10-01-goofus-and-gallant-charts
---

For the past couple of years I've been delving into the world of information visualization.  Part due to intense interest, part due to job responsibilities.  I've read a lot, taken a lot of courses, and have been working to polish my skills along the way.  Having a design focused background (engineering) coupled with a broad foundation of data analysis and statistics (PhD), and my own modest skills in graphics and typography has helped quite a bit.

To make a long story short, part of my role is helping engineering programs cope with the large amounts of curriculum, assessment, survey and student data.  At the heart of that is presenting information in effective ways, following best-practises, to organize, distill and design visualizations that maximize data utility while maintaining the truth contained within.   Some of this work is driven by meeting accreditation and quality concerns, but the crux is providing instructors, administrators and programs with needed insight to develop data-informed continuous improvement practises.

The other day I was provided a sample report that had some visualizations of curriculum mapping data.  These samples were created for a workshop provided by the accreditor, and are intended to show programs what sort of reporting is required.  I'm all for samples that illustrate the implicit requirements of an evaluator.  What I didn't really like is the fact that the samples were presenting the information in a way that disregards effective practise, and doesn't provide an accurate or meaningful representation of the data.  The charts don't lie, they just make it difficult to see the underlying components of the data.  They also serve a singular purpose, rather than providing a broad view that can be used for a variety of purposes.

Here's Goofus' charts:

![Goofus' Chart]({{ site.url }}/assets/goofus.png)

Some background:  The 2 letter codes on the x-axis represent specific outcomes.  The I-D-A, represents the level at which the outcome is developed (I = introduced, D = developed, A = advanced).  On the second chart, the semester is given by numbers 1-8, with a full 4 year program being comprised of 8 semesters.

1) Goofus' presentation makes it difficult to see the counts for each level within the outcome,  you can see relative distributions, but nothing quantitative.  There isn’t really a part-to-whole relationship to convey, so presenting the bars in this fashion serves little purpose.  

2) Goofus repeats his offense from the first chart: relative sizing, difficult to see exact numbers.   Additionally, his chart aggregates the IDA for all attributes.  Why is he doing this?  Just to see how much the program focuses on in a particular area?  The aggregation hides the detailed information for each outcome.

3) Goofus! Pie charts can be difficult to read, especially with multiple categories being compared.  People  have difficulty comparing relative sizes based on angle.  Goofus also has to be careful with the data mappings, as pie charts are maligned due to the frequent errors in percentages. Also, they don't really describe the data in a relevant fashion (what does representing it as a percentage actually provide you?).  

I think Goofus organized the charts incorrectly.  They appear as: Meso-Micro-Macro, which is unintuitive.  There's also text/readability issues, but those can be fixed with careful font selection and emphasis.

So I decided play the part of Gallant and improve them (or at least what I consider to be improvements).

![Gallant's Chart]({{ site.url }}/assets/gallant.png)

First, I changed the order from Macro-Meso-Micro, which gives the user a sense of drill-down in view.  Second I changed the font to a serif, because I find those easier to read. (Gill Sans being an exception due to purposeful design).  Lastly, rather than present these as stark bars (which they are), I applied a Tuftian principle and overlaid a white grid.  This allows for easier comparison and clear depiction of the units.

1) Gallant throws away the pie and uses a waffle chart (or a square pie chart) to present the data as counts rather than percentages.  This allows the reader to see the proportion still, and also have some links back to absolute counts of the data.  

2) Gallant's separates the curriculum levels out, allowing for quick comparison between outcomes and levels (without drawing and arithmetic)  The discretization allows the interested to see exactly how many courses contributed to the development of the outcome.   

3) Gallant uses Tufte's small multiples: The multiples are arranged by semester on the horizontal and IDA on the vertical. Each multiple plots the number of courses in that semester for each outcome.  This allows a more detailed overview of a program to se what attributes were more intensely developed over the program, when they were developed, and how many courses developed them.

I believe that Gallant's presentation of the data gives the reader more utility and increases the value of a single graphic.  It also provides a sense of connectedness, with each graph being a related view to the other.  

The moral of this post is:  "Learn from those that came before you".   Simply charting the data without thinking of it's intended use first, not showing the parts to the whole and ignoring best practise will make you a Goofus.

So be a Gallant.  

Oh.  These charts were created in R, using ggplot2 and arranged with gridExtra. You can see the code on my [github repo](https://github.com/jkaupp/curricualized)
