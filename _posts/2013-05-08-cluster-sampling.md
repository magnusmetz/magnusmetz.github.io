---
layout: post
title: "Cluster Sampling"
author: [yulijia]
categories: [Animation, Sampling Survey]
tags: [cluster, sampling]
reviewer: [yihui]
animation: true
---
{% include JB/setup %}

[Cluster sampling](http://en.wikipedia.org/wiki/Cluster_sampling) is a sampling technique used when
"natural" but relatively homogeneous groupings are evident in a statistical population. In this
technique, the total population is divided into these groups (or clusters) and a simple random
sample of the groups is selected. Then the required information is collected from a simple random
sample of the elements within each selected group.

A common motivation for cluster sampling is to reduce the total number of interviews and costs
given the desired accuracy. Assuming a fixed sample size, the technique gives more accurate results
when most of the variation in the population is within the groups, not between them.

I am not familiar with this technology, I just copy the wiki for the introduction. But I think
everyone may familiar with one of the version of cluster sampling, it's called **area sampling** or
**geographical cluster sampling**. A geographically dispersed population can be expensive to
survey, so we can apply a census for thousand people in each area.

In the [**animation** package](http://yihui.name/animation), function `sample.cluster()` is a
demonstration for cluster sampling, here is the example.


{% highlight r %}
library(animation)
ani.options(nmax = 30, interval = 1)
par(mar = rep(1, 4))
sample.cluster(col = c("bisque", "white"))
{% endhighlight %}


<div class="scianimator">
<div id="sample_cluster" style="display: inline-block;">
</div>
</div>
<script type="text/javascript">
  (function($) {
    $(document).ready(function() {
      var imgs = Array(30);
      for (i=0; ; i++) {
        if (i == imgs.length) break;
        imgs[i] = "/figures/2013-05-08-cluster-sampling/sample-cluster" + (i + 1) + ".png";
      }
      $("#sample_cluster").scianimator({
          "images": imgs,
          "delay": 200,
          "controls": ["first", "previous", "play", "next", "last", "loop", "speed"],
      });
      $("#sample_cluster").scianimator("play");
    });
  })(jQuery);
</script>


Each rectangle stands for a cluster, and the simple random sampling without replacement is
performed for each cluster. All points in the clusters being sampled will be drawn out.
