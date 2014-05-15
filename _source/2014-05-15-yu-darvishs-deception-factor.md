---
layout: post
title: "Yu Darvish's deception factor"
author: [cpsievert]
categories: [WebGL, Animation, Baseball]
tags: [MLB, PITCHfx, pitchRx, animation, rgl]
---
{% include JB/setup %}


On April 2nd, 2013 Yu Darvish [flirted with pitching
perfection](http://sports.yahoo.com/news/yu-darvish-loses-perfect-game-030913556--mlb.html). To
demonstrate his ability to deceive batters with a consistent delivery over different pitch types,
[redditor DShep created this
gif](http://www.reddit.com/r/baseball/comments/1d2z6d/all_of_darvishs_primary_pitches_at_once/),
which layers video of five different pitches thrown by Darvish on April 24th:

<div align="center">
  <img class="decoded" src="http://i.minus.com/i3SXAH4AAxtWS.gif" alt="http://i.minus.com/i3SXAH4AAxtWS.gif">
</div>

Cool, huh? Well, I will show you how to 'recreate' a similar 'gif' with publicly available PITCHf/x
data using the [pitchRx](http://cran.r-project.org/web/packages/pitchRx/)
[R](http://cran.r-project.org) package. First, we collect all the pitches thrown by Darvish to
Albert Pujols on April 24th:


```r
library(animation)
library(pitchRx)
dat <- scrape(start = "2013-04-24", end = "2013-04-24")
atbats <- subset(dat$atbat, pitcher_name == "Yu Darvish" & batter_name == "Albert Pujols")
pitches <- plyr::join(atbats, dat$pitch, by = c("num", "url"), type = "inner")
```


Lets animate these `pitches` using `animateFX`. Note that we take a different perspective from
above by imagining the pitches coming closer as time progresses.





```r
animateFX(pitches)
```

<div align = "center">
 <embed width="504" height="504" name="plugin" src="figure/ani.swf" type="application/x-shockwave-flash"> 
</div>


One thing to notice here is the different release points by Darvish (especially for his slider).
Furthermore, Darvish didn't even throw a curveball to Pujols. If you look closer at the original
gif, you can actually see a different batter (than Pujols) in the batter's box (look for a white
bat). Darvish's delivery looks very similar on videotape, but his arm angle (and thus) release
point might be slightly different for different pitch types according to the PITCHf/x data. Let's
take a closer look at Darvish's release point during this start.


```r
atbats <- subset(dat$atbat, pitcher_name == "Yu Darvish")
Darvish <- plyr::join(atbats, dat$pitch, by = c("num", "url"), type = "inner")
qplot(data = Darvish, x = as.numeric(x0), y = as.numeric(z0), color = pitch_type) + 
    coord_equal()
```

<img src="figure/release.png" title="plot of chunk release" alt="plot of chunk release" style="display: block; margin: auto;" />


As you can see, Darvish has quite different release points according to pitch type. For example,
his slider tends to be more 'side-arm' compared to his four-seam fastball. Now, whether that
difference is distinguishable to the human-eye is another question...

EDIT: Thanks to a recommendation by [@Sky_Kalman](https://twitter.com/Sky_Kalkman), normalizing
release points should make it easier to make visual comparison of flight paths across the pitch
types. Here is one way to go about that:


```r
pitches$x0 <- mean(as.numeric(pitches$x0))
pitches$z0 <- mean(as.numeric(pitches$z0))
saveHTML(animateFX(pitches))
```

```
## HTML file created at: /tmp/RtmptnxAR9/index.html
## You may use ani.options(outdir = getwd()) or saveHTML(..., outdir = getwd()) to generate files under the current working directory.
```



Lastly, just for fun, let's take an interactive look at Darvish's pitches to Pujols. If your
browser has [WebGL enabled](http://get.webgl.org/), go ahead and play with the object below!


```r
library(rgl)
interactiveFX(pitches)
```


<iframe src="http://cpsievert.github.io/pitchRx/YuDarvish/" width="800" height="600"></iframe>

I think it would be awesome to have a similar tool in
[pitchRx](http://cran.r-project.org/web/packages/pitchRx/) for creating 'gifs' with actual video.
If anybody has ideas on how we can connect PITCHf/x data with actual video, please contact me or
leave a comment!
