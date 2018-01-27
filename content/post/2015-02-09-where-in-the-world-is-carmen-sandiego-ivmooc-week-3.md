---
title: 'Where in the world is Carmen Sandiego?: #IVMOOC Week 3'
date: '2015-02-09'
slug: content//post/2015-02-09-where-in-the-world-is-carmen-sandiego-ivmooc-week-3
---
Getting through this week was a bit tough, not due to content or complexity, but due to life, work and winter.  Being the only well parent is a lot of work.  Couple that with deadlines, grant writing and research sessions made for very little free time.  I made it though!

After watching the videos and hands-on clips for the week, I felt tackling this assignment was pretty easily.  I chose to visualize the amount of NSF funding for Engineering Education research. My search off of the scholarly database yielded 2000 results, with multiple awards per state.  Aggregating in the very manual way outlined in the hands on video was far too inefficient and tedious.  So I turned to R and some of the wonderful packages that have been created (gdata, ggmaps, ggplot2, plyr).  I did use SCI2 to geocode the data, since I used my query limits with google maps when playing around with ggmaps.

After that it was pretty easy.  I aggregated at the state level, as the SCI2 geocoder gave me some errors when encoding the zip codes, or the city level.  Pulled up a map of the continental USA, and plotted the amount of funding indicating amounts with both size and color.  The code I used is below:

{{< highlight r >}}
library(plyr)
library(gdata)
library(ggmap)
library(ggplot2)

setwd("~/MOOCs/IVMOOC";)
data <- read.csv("NSF Master LandL.csv";)

data.state <-ddply(data, .(state, Latitude, Longitude), summarize, expected_total_amount = sum(expected_total_amount))
usa <- get_map(location = 'united states', zoom = 4, color="color", maptype='road')
g <- guide_legend("Amount of Funding (USD)")

ggmap(usa) +
  geom_point(aes(x=Longitude, y=Latitude, show_guide = TRUE, size=expected_total_amount, color=expected_total_amount), data = data.state) +
  scale_colour_gradient(low="#e7e1ef", high="#dd1c77") +
  guides(colour = g, size = g) +
  theme(legend.position = "bottom") +
  ggtitle("Geocoding of NSF Funding of Engineering Education Research") +
  xlab("Longitude") +
  ylab("Latitude")
{{< endhighlight >}}


I wanted to explore at both the state level and at the city level, but ran into those limits, and the amount of time I could spend on this.  Maybe in the future, I'll delve into this a bit more and expand the code to geocode by the zip in R, and then plot those on the US map.    My visualization:

![Geospatial Assignment](/img/geospatial-assignment.png)

All in all, a fun week.  The bits I found most useful:  a nice overview of colors and their use in geospatial maps and the hands-on sessions.
Next up, week 4 and the midterm!
