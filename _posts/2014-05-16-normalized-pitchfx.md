---
layout: post
title: "Normalizing PITCHfx"
author: [Magnus Metz]
categories: [baseball, PITCHfx, pitchRx, animation]
tags: [MLB, animation]
animation: true
---
{% include JB/setup %}

In this article the idea of forcing release points to a central point in the animation is realized
- to ease the visual comparison of flight paths across pitch types. The idea was implemented by
just using average release points; but that can be deceptive, since it the alters the entire path
of each pitch.

The (current) proposal is what we will call 'normalized' (or regressed towards the mean) PITCHf/x
animations. The idea is to get an idea of a 'typical' flight path for each pitch type. It is
assumed that averaging over the relevant PITCHf/x parameters is the best way to go about this!
Anyway, this is a starting point. Note that the same `Darvish` data frame from my most recent
[post](http://magnusmetz.github.io/2014/05/yu-darvishs-deception-factor/) is used.


{% highlight r %}
library(knitr)
library(pitchRx)
library(animation)
opts_knit$set(animation.fun = hook_r2swf)
dat <- scrape(start = "2013-04-24", end = "2013-04-24")
atbats <- subset(dat$atbat, pitcher_name == "Yu Darvish")
Darvish <- plyr::join(atbats, dat$pitch, by = c("num", "url"), type = "inner")
{% endhighlight %}




{% highlight r %}
library(plyr)
library(reshape2)
idx <- c("x0", "y0", "z0", "vx0", "vy0", "vz0", "ax", "ay", "az")
for (i in idx) Darvish[, i] <- as.numeric(Darvish[, i])
agDarvish <- ddply(Darvish, c("pitch_type", "stand"), summarize, x0 = mean(x0), 
  y0 = 55, z0 = mean(z0), vx0 = mean(vx0), vy0 = mean(vy0), vz0 = mean(vz0), 
  ax = mean(ax), ay = mean(ay), az = mean(az))
agDarvish$b_height <- "6-1"  #estimate average batter height (for strikezones)
animateFX(agDarvish, layer = facet_wrap(~stand))
{% endhighlight %}


<div class="scianimator">
<div id="ani1" style="display: inline-block;">
</div>
</div>
<script type="text/javascript">
  (function($) {
    $(document).ready(function() {
      var imgs = Array(64);
      for (i=0; ; i++) {
        if (i == imgs.length) break;
        imgs[i] = "/figures/2014-05-16-normalized-pitchfx/ani1" + (i + 1) + ".png";
      }
      $("#ani1").scianimator({
          "images": imgs,
          "delay": 50,
          "controls": ["first", "previous", "play", "next", "last", "loop", "speed"],
      });
      $("#ani1").scianimator("play");
    });
  })(jQuery);
</script>

