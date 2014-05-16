---
layout: post
title: " The Newton Raphson Method for Root finding"
author: [yulijia]
categories: [Animation, Computational Statistics]
tags: [Newton Raphson Method, root finding]
reviewer: [yihui]
animation: true
---
{% include JB/setup %}

In numerical analysis, [Newton Raphson Method](http://en.wikipedia.org/wiki/Newton's_method) is a
method for finding successively better approximations to the roots (or zeroes) of a real-valued
function.

As mentioned in Wikipedia, the idea of the method is as follows: one starts with an initial guess
which is reasonably close to the true root, then the function is approximated by its tangent line
(which can be computed using the tools of calculus), and one computes the x-intercept of this
tangent line (which is easily done with elementary algebra). This x-intercept will typically be a
better approximation to the function's root than the original guess, and the method can be
iterated.

The function `newton.method()` in the [**animation** package](http://yihui.name/animation) can give
you a demonstration of the Newton-Raphson Method. Let's set the function
$$f(x)=5x{^2}-7x{^2}-40x+100$$, the starting point is 7.15 and the interval is $$[-6.2, 7.1]$$.


{% highlight r %}
library(animation)
ani.options(nmax = 100, interval = 1)
par(mar = c(3, 3, 1, 1.5), mgp = c(1.5, 0.5, 0), pch = 19)
newton.method(function(x) 5 * x^3 - 7 * x^2 - 40 * x + 100, init = 7.15, 
  rg = c(-6.2, 7.1))
{% endhighlight %}


<div class="scianimator">
<div id="newton_method_right" style="display: inline-block;">
</div>
</div>
<script type="text/javascript">
  (function($) {
    $(document).ready(function() {
      var imgs = Array(21);
      for (i=0; ; i++) {
        if (i == imgs.length) break;
        imgs[i] = "/figures/2013-04-30-newton-raphson-method-root-finding/newton-method-right" + (i + 1) + ".png";
      }
      $("#newton_method_right").scianimator({
          "images": imgs,
          "delay": 500,
          "controls": ["first", "previous", "play", "next", "last", "loop", "speed"],
      });
      $("#newton_method_right").scianimator("play");
    });
  })(jQuery);
</script>


The algorithm might not converge – it depends on the starting value. See the examples below.


{% highlight r %}
## does not converge!
par(mar = c(3, 3, 1, 1.5), mgp = c(1.5, 0.5, 0), pch = 19)
xx = newton.method(function(x) atan(x), rg = c(-5, 5), init = 1.5)
{% endhighlight %}


<div class="scianimator">
<div id="newton_method_wrong" style="display: inline-block;">
</div>
</div>
<script type="text/javascript">
  (function($) {
    $(document).ready(function() {
      var imgs = Array(12);
      for (i=0; ; i++) {
        if (i == imgs.length) break;
        imgs[i] = "/figures/2013-04-30-newton-raphson-method-root-finding/newton-method-wrong" + (i + 1) + ".png";
      }
      $("#newton_method_wrong").scianimator({
          "images": imgs,
          "delay": 500,
          "controls": ["first", "previous", "play", "next", "last", "loop", "speed"],
      });
      $("#newton_method_wrong").scianimator("play");
    });
  })(jQuery);
</script>


{% highlight r %}
xx$root  # Inf
{% endhighlight %}



{% highlight text %}
## [1] Inf
{% endhighlight %}

