---
layout: post
title: "Hit or Miss Monte Carlo Integration"
author: [yulijia]
categories: [Animation, Computational Statistics]
tags: [hit-or-miss, Monte Carlo]
reviewer: [yihui]
animation: ture
---
{% include JB/setup %}

## Introduction

I first heard the [Montre Carlo Method](http://en.wikipedia.org/wiki/Monte_Carlo_method) is on a
story of the nuclear weapon project. The Montre Carlo Method was invented in the late 1940s by
Stanislaw Ulam, they were used at Los Alamos for early work relating to the development of the
hydrogen bomb, and became popularized in the fields of physics, physical chemistry, and operations
research.

The Montre Carlo Method used for drawing a sample at random from the empirical distribution. The
oldest well-known example is that of the [Buffon's needle](2013-04-16-buffons-needle.Rmd), where
supposing a needle of the same length as the width between cracks we have: $$P=\frac{2L}{D\pi}$$
implying $$\hat{\pi}=2\frac{L}{D}P$$, the $$\frac{L}{D}$$ is a constant.

## What is a Monte Carlo Method?

In physics and statistics many of the problems Monte Carlo is used on is under the form of the
estimate of an integral unkown in closed form: $$\hat{\theta}=\int_0^1 f(u)du$$, which can be seen
as the evalutaion of $$Ef(u)$$, where $$u \sim U(0,1)$$.

The **hit-or-miss** Monte Carlo method generates random points in a bounded graph and counts the
number of 'hits' or points that are in the region whose area we want to evaluate,
$$\hat{\theta}=\frac{\#hits}{\#total}$$. As shown in the [Buffon's
needle](2013-04-16-buffons-needle.Rmd), the $$\pi$$ can be calculated by the sumilation.

Here, I show one of the simulation of $$\pi$$ by function `MC.hitormiss()`in the [**animation**
package](http://yihui.name/animation). This function can generate uniform random numbers and
compute the proportion of points under the curve. Consider a circle inscribed in a unit square.
Given that the circle and the square have a ratio of areas that is $$P=\pi/4$$, the value of
$$\pi$$ can be approximated using a Monte Carlo method. We only need to counts the number of 'hits'
or points that are in the circle, the $$\pi=4P$$.


{% highlight r %}
library(animation)
ani.options(nmax = 200)
f = function(x) sqrt(1 - x^2)
P = MC.hitormiss(f, from = 0, to = 1)$est
{% endhighlight %}


<div class="scianimator">
<div id="hit_or_miss_montre_carlo" style="display: inline-block;">
</div>
</div>
<script type="text/javascript">
  (function($) {
    $(document).ready(function() {
      var imgs = Array(200);
      for (i=0; ; i++) {
        if (i == imgs.length) break;
        imgs[i] = "/figures/2013-04-30-hit-or-miss-monte-carlo-integration/hit-or-miss-montre-carlo" + (i + 1) + ".png";
      }
      $("#hit_or_miss_montre_carlo").scianimator({
          "images": imgs,
          "delay": 100,
          "controls": ["first", "previous", "play", "next", "last", "loop", "speed"],
      });
      $("#hit_or_miss_montre_carlo").scianimator("play");
    });
  })(jQuery);
</script>


{% highlight r %}
Pi = P * 4
Pi
{% endhighlight %}



{% highlight text %}
## [1] 3.064
{% endhighlight %}


## Note

This function is for demonstration purpose only; the integral might be very inaccurate when n is
small.

`ani.options('nmax')` specifies the maximum number of trials.

## Reference
1.Monte
Carlo,[http://www-stat.stanford.edu/~susan/courses/s208/node14.html](http://www-stat.stanford.edu/~susan/courses/s208/node14.html)
