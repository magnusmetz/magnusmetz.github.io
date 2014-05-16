---
layout: post
title: "Sample Mean Monte Carlo Integration"
author: [yulijia]
categories: [Animation, Computational Statistics]
tags: [sample mean, Monte Carlo]
reviewer: [yihui]
animation: true
---
{% include JB/setup %}

As discussed [before](sample-mean-monte-carlo-integration.Rmd), in physics and statistics many of
the problems Monte Carlo is used on is under the form of the estimate of an integral unkown in
closed form: $$\hat{\theta}=\int_0^1 f(u)du$$, which can be seen as the evalutaion of $$Ef(u)$$,
where $$u \sim U(0,1)$$. There is another Monte Carlo method named mean-value Monte Carlo method.
Thus proposes to generate $$B$$ numbers uniformly from $$(0,1)$$ and take their average: to
estimate $$\theta$$, $$B=\frac{1}{B}\sum\limits_{b=1}^{B}f(u_b)$$.

In the [**animation** package](http://yihui.name/animation), the function `MC.samplemean()` can be
used to estimate the area under the curve, by computing the average function values. Let's me show
you a quick example, see below.


{% highlight r %}
library(animation)
MC.samplemean(border = NA)$est
{% endhighlight %}


<div class="scianimator">
<div id="hit_or_miss_montre_carlo" style="display: inline-block;">
</div>
</div>
<script type="text/javascript">
  (function($) {
    $(document).ready(function() {
      var imgs = Array(50);
      for (i=0; ; i++) {
        if (i == imgs.length) break;
        imgs[i] = "/figures/2013-04-30-sample-mean-monte-carlo-integration/hit-or-miss-montre-carlo" + (i + 1) + ".png";
      }
      $("#hit_or_miss_montre_carlo").scianimator({
          "images": imgs,
          "delay": 200,
          "controls": ["first", "previous", "play", "next", "last", "loop", "speed"],
      });
      $("#hit_or_miss_montre_carlo").scianimator("play");
    });
  })(jQuery);
</script>


{% highlight text %}
## [1] 0.1815
{% endhighlight %}


## Reference
1.Monte
Carlo,[http://www-stat.stanford.edu/~susan/courses/s208/node14.html](http://www-stat.stanford.edu/~susan/courses/s208/node14.html)
