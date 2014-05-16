---
layout: post
title: "Simple Random Sampling Without Replacement"
author: [yihui, yulijia]
categories: [Animation, Sampling Survey]
tags: [Simple Random Sampling, replacement, Bootstrapping]
reviewer: []
animation: true
---
{% include JB/setup %}

[Simple Random Sampling](http://en.wikipedia.org/wiki/Simple_random_sample)is easy to understand.
It is the purest form of probability sampling. Each member of the population has an equal and known
chance of being selected. When there are very large populations, it is often difficult or
impossible to identify every member of the population, so the pool of available subjects becomes
biased.

In most cases, we conduct the sampling in a "**without**-replacement" manner, i.e. we don't put
back the sample points once we pick them out. Correspondingly there is another way "sampling
**with** replacement": every time before we do the sampling, we put all the individuals back again;
although this is rare in practical sampling work, it's also extremely important and closely related
to the idea of [bootstrap](2013-05-08-bootstrapping-the-iid-data.Rmd).


The function `sample.simple()` in the [**animation** package](http://yihui.name/animation) shows
you the simple random sampling without replacement. The whole sample frame is denoted by a matrix
(nrow * ncol) in the plane just for convenience, and the points being sampled are marked out (by
red circles by default). Each member of the population has an equal and known chance of being
selected. Each frame is a completed simple random sampling without replacement process.


{% highlight r %}
library(animation)
sample.simple(nrow = 10, ncol = 12, size = 10)
{% endhighlight %}


<div class="scianimator">
<div id="simple_random_sample" style="display: inline-block;">
</div>
</div>
<script type="text/javascript">
  (function($) {
    $(document).ready(function() {
      var imgs = Array(50);
      for (i=0; ; i++) {
        if (i == imgs.length) break;
        imgs[i] = "/figures/2013-05-08-sampling-without-replacement/simple-random-sample" + (i + 1) + ".png";
      }
      $("#simple_random_sample").scianimator({
          "images": imgs,
          "delay": 200,
          "controls": ["first", "previous", "play", "next", "last", "loop", "speed"],
      });
      $("#simple_random_sample").scianimator("play");
    });
  })(jQuery);
</script>

