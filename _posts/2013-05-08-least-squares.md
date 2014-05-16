---
layout: post
title: "Least Squares Fitting"
author: [yulijia]
categories: [Animation, Linear Models]
tags: [Least Squares]
reviewer: [yihui]
animation: true
---
{% include JB/setup %}

[Least squares](http://en.wikipedia.org/wiki/Least_squares) fitting is a mathematical procedure for
finding the best-fitting curve to a given set of points by minimizing the sum of the squares of the
offsets ("the residuals") of the points from the curve. *Least squares* means that the overall
solution minimizes the sum of the squares of the errors made in the results of every single
equation.

The function `least.squares()` in the [**animation** package](http://yihui.name/animation) has
provided an illustration of least squares in univariate linear regression.

let's assume that the relationship between x andy is a linear one.

Let $$y=ax+b$$ be the eauation of the best fit line to the data. We need to determine the valuses
of both the slop $$a$$ and intercept $$b$$. Assuming each data point carries eauql weight, each
$$y_{i}$$ point has exactly the same actual error asscociated with it, we find $$a$$ and $$b$$ by
minimizing the sum of the squares of the deviations of the actual values of $$y_{i}$$ from the
line's calcualted value of y.

The formulas for $$a$$ and $$b$$ are:

$$a=SLOPE=\frac{n\sum{x_{i}y_{i}}-\sum {x_{i}}\sum{y_{i}}}{n\sum{x_{i}^{2}}-(\sum{x_{i}})^2}$$

$$b=INTERCEPT=\frac{\sum{x_{i}^{2}}\sum{y_{i}}-\sum{x_{i}}\sum{y_{i}}}{n\sum{x_{i}^{2}}-(\sum{x_{i}})^2}$$

Here is the simple demonstration of the meaning of least squares in univariate linear regression.

## With slope changing



{% highlight r %}
library(animation)
ani.options(interval = 0.3)
par(mar = c(4, 4, 0.5, 0.1), mgp = c(2, 0.5, 0), tcl = -0.3)
## slope changing
least.squares()
{% endhighlight %}


<div class="scianimator">
<div id="slope_changing" style="display: inline-block;">
</div>
</div>
<script type="text/javascript">
  (function($) {
    $(document).ready(function() {
      var imgs = Array(50);
      for (i=0; ; i++) {
        if (i == imgs.length) break;
        imgs[i] = "/figures/2013-05-08-least-squares/slope-changing" + (i + 1) + ".png";
      }
      $("#slope_changing").scianimator({
          "images": imgs,
          "delay": 300,
          "controls": ["first", "previous", "play", "next", "last", "loop", "speed"],
      });
      $("#slope_changing").scianimator("play");
    });
  })(jQuery);
</script>


## With intercept changing

{% highlight r %}
library(animation)
ani.options(interval = 0.3)
par(mar = c(4, 4, 0.5, 0.1), mgp = c(2, 0.5, 0), tcl = -0.3)
# slope changing
least.squares(ani.type = "intercept")
{% endhighlight %}


<div class="scianimator">
<div id="intercept_changing_" style="display: inline-block;">
</div>
</div>
<script type="text/javascript">
  (function($) {
    $(document).ready(function() {
      var imgs = Array(50);
      for (i=0; ; i++) {
        if (i == imgs.length) break;
        imgs[i] = "/figures/2013-05-08-least-squares/intercept-changing_" + (i + 1) + ".png";
      }
      $("#intercept_changing_").scianimator({
          "images": imgs,
          "delay": 300,
          "controls": ["first", "previous", "play", "next", "last", "loop", "speed"],
      });
      $("#intercept_changing_").scianimator("play");
    });
  })(jQuery);
</script>

