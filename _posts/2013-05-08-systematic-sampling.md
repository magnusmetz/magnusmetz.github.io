---
layout: post
title: "Systematic Sampling"
author: [yihui]
categories: [Animation, Sampling Survey]
tags: [Systematic Sampling]
reviewer: []
animation: true
---
{% include JB/setup %}

The function `sample.system()` in the [**animation** package](http://yihui.name/animation) shows
you the systematic sampling. [Systematic
Sampling](http://en.wikipedia.org/wiki/Systematic_sampling) is often used instead of random
sampling. It is also called an $$N^{th}$$ name selection technique. After the required sample size
has been calculated, every $$N^{th}$$ record is selected from a list of population members. As long
as the list does not contain any hidden order, this sampling method is as good as the random
sampling method. Its only advantage over the random sampling technique is simplicity. Systematic
sampling is frequently used to select a specified number of records from a computer file.



{% highlight r %}
library(animation)
par(mar = rep(1, 4), lwd = 2)
sample.system()
{% endhighlight %}


<div class="scianimator">
<div id="systematic_sampling" style="display: inline-block;">
</div>
</div>
<script type="text/javascript">
  (function($) {
    $(document).ready(function() {
      var imgs = Array(50);
      for (i=0; ; i++) {
        if (i == imgs.length) break;
        imgs[i] = "/figures/2013-05-08-systematic-sampling/systematic-sampling" + (i + 1) + ".png";
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

