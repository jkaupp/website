---
title: 'My business is with R tonight, with maps and color. #IVMOOC Week 5'
slug: content//post/2015-02-22-my-business-is-with-r-tonight-with-maps-and-color-ivmooc-week-5
---
So the midterm has me a bit disheartened.  Not because of difficulty, but because of the miscommunication between the admin and the students.  In Canvas the midterm description was set to Feb 16th 8pm EST deadline.  After putting my son to bed, and while making dinner, I logged into Canvas and rushed to do the midterm.  Flying through it, I ended up with a 21.  Then I see the next day on twitter that it's due on the 19th, yet this wasn't reflected on Canvas.  Had I known this, I would have set aside a better time to actually write the midterm, un-hurried and would have done much better. I had some misclicks, skipped questions not addressed and some bonehead mistakes (For all of the graphic work and video editing I've done why in the blue hell would I put saturation down as Qualitative? Derp.)

Also, upon seeing the correct answers, there some dubious incorrect answers.  Word Cloud vs Tag Cloud?  Cartograms vs Cartogram?  These small errors don't mean much, but they show some issues with the automatic grading system.  I hope they get corrected in future versions.  My mark can stand as it is, it wasn't my best effort and is more reflective of poor time management, but this can be really discouraging for people and just make them walk away from the course.

And that's all I have to say about that.

Week 5.  For this week, I pretty much read the book chapter rather than watch videos, and the hands on videos didn't really do more than what was covered in the chapters and sci2 wiki.  I wasn't terribly happy with the sci2 output, so I went to R.  After thinking for a bit, I abandoned most of my attempts to collect all the data through R, because I remembered the 'tree' command in unix.  So after a download of homebrew, brewing up tree and looking at the manual, I had my workflow:

1. Generate directory hierarchy using tree
2. Export it to xml
3. Translate the xml to JSON
4. load the JSON into R
5. Refine the data
6. Add secondary variable to encode the data (file counts)
7. [Treemapify](https://github.com/wilkox/treemapify) the data and plot
8. Clean up the plot in Affinity Designer

Below is my R code:

{% highlight r %}
library(plyr)
library(magrittr)
library(treemap)
library(treemapify)
library(ggplot2)

# This originally started out by mapping the directory heirarchy using R, but then I remembered
# Tree from unix (I'll get to that later).
# I used this bit of code, plus excel to get the file counts for each directory
# If I had a better knowledge of regular expressions, I would subset the n.files data frame
# by a Directory structure to the depth I would like (1)

path<-"~/OwnCloud/Graduate Studies Research"
dirs <- list.dirs(path)

num.files <- function(x) {
 out <- length(list.files(x))
 out
}

n.files <- ldply(dirs,num.files)

# Prior to this step, I collected the information about the directory structure
# using the unix Tree command to output the director structure, depth 2 to xml.
# tree -dhX -L 1 -o test.xml --du ~/OwnCloud/Graduate*
# I then converted the XML to JSON using an online converter, because I couldn't
# get the XML and JSONIO librarys to work correctly

data.temp <- fromJSON("~/json.txt") %>%
 data.frame()

# Trimming the data frame and putting the columns into the correct data formats

data3<-data3[, c(1:3)]
data3$file.count <- c(55,23,271,32,47,68,313,2120,171,44,63,86)
names(data3) <- c("root", "subdir", "size", "count")
data3$size <- as.numeric(data3$size)
data3$subdir <- factor(data3$subdir)
data3$count <- cut(data3$count,c(0, 50, 100, 150, 300, 2200),labels=c("0-50", "50-100", "100-150", "150-300", "300+"))

# Using treemapify to transform the data into a structure that ggplot2 can use.
# Then used ggplotify to plot it, because a layered grammar of graphics is awesome.

treemapify(data3,
 area="size",
 fill="count",
 label="subdir") %>%
ggplotify %>%
 + guides(fill=guide_legend("# of Files")) %>%
 + ggtitle(bquote(atop(.("Treemap Visualization"), atop(italic(.("Graduate Studies Directory, Depth = 1")), ""))))
 {% endhighlight %}

And here is the resulting visualization:

![IVMOOC Assignment 5]({{ site.url }}/assets/assignment-5.png)
