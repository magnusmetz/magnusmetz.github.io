---
layout: page
title: Blog
---
{% include JB/setup %}

Statistical graphics are powerful -- your eyes will jump to the graph below immediately and skip this paragraph automatically. When we see a nice graph, we often wonder how it was made (e.g. [this one](http://stackoverflow.com/q/12675147/559676) via xkcd).

![via xkcd](http://i.imgur.com/4staRNH.png)

Vistat aims to provide _working_ recipes for statistical graphics by building them from source. The website is based on Github/Jekyll, and graphs are generated dynamically through the R package [**knitr**](http://yihui.name/knitr), hence reproducibility is guaranteed, and readers can see the source code at the same time.

## Latest 10 posts

<ul class="posts">
  {% for post in site.posts limit:10 %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
  <li><a href="archive.html">Read More...</a></li>
</ul>

## How to contribute

You can [fork the repository](https://github.com/supstat/vistat) on Github, add your article to the `_source` directory and submit a pull request to us. We will run your code and upload images. For more details, see [about](about.html).

## Copyright

All the content in this website is licensed under [CC BY-NC-SA 3.0](http://creativecommons.org/licenses/by-nc-sa/3.0/). This site is a clone of [vistat](http://vis.supstat.com/) and hosted on [GitHub](https://github.com) Pages using the [Dinky theme](https://github.com/sodabrew/theme-dinky) for [Jekyll Bootstrap](http://jekyllbootstrap.com).
