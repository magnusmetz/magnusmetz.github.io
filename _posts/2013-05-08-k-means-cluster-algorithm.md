---
layout: post
title: "K Means Cluster Algorithm"
author: [yulijia]
categories: [Animation, Data Mining, Machine Learning, Multivariate Statistics]
tags: [K-means, cluster]
reviewer: [yihui]
animation: true
---
{% include JB/setup %}

The [k-means clustering](http://en.wikipedia.org/wiki/K-means_clustering) aims to partition $$n$$
observations into $$k$$ clusters in which each observation belongs to the cluster with the nearest
mean, serving as a prototype (clustering center) of the cluster. Generally speaking, it may include
a series of iterations: finding cluster centers, computing distances between sample points, and
redefining cluster membership. It is one of the top 10 algorithms in data mining.

In the [**animation** package](http://yihui.name/animation), function `kmeans.ani()` is a
demonstration for k-means cluster algorithm, here is the example. The beautiful graph let me think
this demostration function is the best one in the **animation** package.


{% highlight r %}
library(animation)
cent = 1.5 * c(1, 1, -1, -1, 1, -1, 1, -1)
x = NULL
for (i in 1:8) x = c(x, rnorm(25, mean = cent[i]))
x = matrix(x, ncol = 2)
kmeans.ani(x, centers = 4, pch = 1:4, col = 1:4)
{% endhighlight %}


<div class="scianimator">
<div id="k_means" style="display: inline-block;">
</div>
</div>
<script type="text/javascript">
  (function($) {
    $(document).ready(function() {
      var imgs = Array(32);
      for (i=0; ; i++) {
        if (i == imgs.length) break;
        imgs[i] = "/figures/2013-05-08-k-means-cluster-algorithm/k-means" + (i + 1) + ".png";
      }
      $("#k_means").scianimator({
          "images": imgs,
          "delay": 500,
          "controls": ["first", "previous", "play", "next", "last", "loop", "speed"],
      });
      $("#k_means").scianimator("play");
    });
  })(jQuery);
</script>

