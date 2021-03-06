---
layout: post
title: "First attempts with pitchRx and animint"
author: Magnus Metz
categories: [PITCHfx, interactive graphics]
tags: [pitchRx, animint]
---
{% include JB/setup %}


Thanks to Carsen Sievert's
[article](http://cpsievert.github.io/2014/03/fun-with-pitchrx-and-animint/) I was able to make some
first experiences with the [animint](https://github.com/tdhock/animint) package, which allows one
to create linked, interactive (even animated) web graphics using ggplot2 code.

This short post demonstrates linked plots using data from the
[pitchRx](http://cran.r-project.org/web/packages/pitchRx/) package. The pitchRx package provides
Major League Baseball Advanced Media's Gamedata. In addition with PITCHf/x 3D animations of the
baseball flightpaths can be created. If you click on the bars in the bar chart below, the
corresponding start versus end speed scatterplot should change to reflect the current selection.
According to Sievert the package fills a void where other similar (and also great) packages like
[rCharts](http://rcharts.io/) and [ggvis](http://ggvis.rstudio.com/) currently fall short. I
hopefully can spend more time with the package in the future and apply it to different data.


{% highlight r %}
library(pitchRx)
library(animint)
data(pitches, package = "pitchRx")
pitches$type <- interaction(pitches$pitch_type, pitches$pitcher_name)
counts <- ddply(pitches, c("pitch_type", "pitcher_name", "type"),
                summarise, count = length(px))
viz <- list(bars = ggplot() +
              geom_bar(aes(x = factor(pitch_type), y = count,
                           fill = pitcher_name, clickSelects = type),
                      position = "dodge", stat = "identity", data = counts),
            scatter = ggplot() +
              geom_point(aes(start_speed, end_speed, fill = pitcher_name, showSelected = type),
                         alpha = 0.65, data = pitches))
gg2animint(viz)
{% endhighlight %}

<iframe src="http://magnusmetz.github.io/figures/2014-05-15-first-attempts-with-animint/animint/"
style="background: #FFFFFF;" width="1200" height="500"> </iframe>

## References

- This article was reproduced from [cpsievert](http://cpsievert.github.io/2014/03/fun-with-pitchrx-and-animint/)
