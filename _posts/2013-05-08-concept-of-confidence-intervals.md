---
layout: post
title: "The concept of confidence intervals"
author: [yulijia]
categories: [Animation, Mathematical Statistics]
tags: [Confidence Intervals]
reviewer: [yihui]
animation: true
---
{% include JB/setup %}

A [confidence interval](http://en.wikipedia.org/wiki/Confidence_interval) gives an estimated range
of values which is likely to include an unknown population parameter, the estimated range being
calculated from a given set of sample data.

The interval covers the true parameter with a probability $$1-\alpha$$ or the true parameter lies
in the interval with a probability $$1-\alpha$$? The answer is the latter.

Confidence intervals consist of a range of values (interval) that act as good estimates of the
unknown population parameter. However, in infrequent cases, none of these values may cover the
value of the parameter. The level of confidence of the confidence interval would indicate the
probability that the confidence range captures this true population parameter given a distribution
of samples. It does not describe any single sample.

Function `Rosling.bubbles()` in the [**animation** package](http://yihui.name/animation) shows the
concept of the confidence interval which depends on the observations: if the samples change, the
interval changes too. At last we can see that the coverage rate will be approximate to the
confidence level.


{% highlight r %}
library(animation)
ani.options(nmax = 100, interval = 0.15)
par(mar = c(3, 3, 1, 0.5), mgp = c(1.5, 0.5, 0), tcl = -0.3)
conf.int()
{% endhighlight %}


<div class="scianimator">
<div id="systematic_sampling" style="display: inline-block;">
</div>
</div>
<script type="text/javascript">
  (function($) {
    $(document).ready(function() {
      var imgs = Array(100);
      for (i=0; ; i++) {
        if (i == imgs.length) break;
        imgs[i] = "/figures/2013-05-08-concept-of-confidence-intervals/systematic-sampling" + (i + 1) + ".png";
      }
      $("#systematic_sampling").scianimator({
          "images": imgs,
          "delay": 500,
          "controls": ["first", "previous", "play", "next", "last", "loop", "speed"],
      });
      $("#systematic_sampling").scianimator("play");
    });
  })(jQuery);
</script>

