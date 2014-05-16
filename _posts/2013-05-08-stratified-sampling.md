---
layout: post
title: "Stratified Sampling"
author: [yihui]
categories: [Animation, Sampling Survey]
tags: [Stratified Sampling]
reviewer: []
animation: true
---
{% include JB/setup %}

[Stratified Sampling](http://en.wikipedia.org/wiki/Stratified_sampling) is commonly used
probability method that is superior to random sampling because it reduces sampling error. A stratum
is a subset of the population that share at least one common characteristic. Examples of strata
might be males and females, or managers and non-managers.

The researcher first identifies the relevant strata and their actual representation in the
population. Random sampling is then used to select a sufficient number of subjects from each
stratum. "Sufficient" refers to a sample size large enough for us to be reasonably confident that
the stratum represents the population. Stratified sampling is often used when one or more of the
strata in the population have a low incidence relative to the other strata.

The function `sample.strat()` in the [**animation** package](http://yihui.name/animation) shows you
the stratified sampling. Each rectangle stands for a stratum, and the simple random sampling
without replacement is performed within each stratum. The points being sampled are marked out (by
red circles by default).


{% highlight r %}
library(animation)
sample.strat(col = c("bisque", "white"))
{% endhighlight %}


<div class="scianimator">
<div id="stratified_sample" style="display: inline-block;">
</div>
</div>
<script type="text/javascript">
  (function($) {
    $(document).ready(function() {
      var imgs = Array(50);
      for (i=0; ; i++) {
        if (i == imgs.length) break;
        imgs[i] = "/figures/2013-05-08-stratified-sampling/stratified-sample" + (i + 1) + ".png";
      }
      $("#stratified_sample").scianimator({
          "images": imgs,
          "delay": 200,
          "controls": ["first", "previous", "play", "next", "last", "loop", "speed"],
      });
      $("#stratified_sample").scianimator("play");
    });
  })(jQuery);
</script>

