---
layout: page
title: Blog
---
{% include JB/setup %}

Statistical graphics are powerful -- your eyes will jump to the graph below immediately and skip this paragraph automatically. When we see a nice graph, we often wonder how it was made (e.g. [this one](http://stackoverflow.com/q/12675147/559676) via xkcd).

![via xkcd](http://i.imgur.com/4staRNH.png)

This blog aims to provide knowledge for statistical graphics by building them from source and further statistical applications with R. The website is based on Github/Jekyll, and graphs and analyses are generated dynamically through the R package [**knitr**](http://yihui.name/knitr), hence reproducibility is guaranteed, and readers can see the source code at the same time.

## Latest 10 posts

<ul class="posts">
  {% for post in site.posts limit:10 %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
  <li><a href="archive.html">Read More...</a></li>
</ul>



## Copyright

All the content in this website is licensed under [CC BY-NC-SA 3.0](http://creativecommons.org/licenses/by-nc-sa/3.0/).
