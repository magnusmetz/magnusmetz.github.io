---
layout: page
title: About
group: navigation
---
{% include JB/setup %}

This page shows you all the instructions on how to contribute to Vistat. Before you get started, you need to fork the [supstat/vistat](https://github.com/supstat/vistat) repository to your own Github account (click the `Fork` button). You are assumed to have basic knowledge of GIT and R.

## New Article

To start a new article, run

{% highlight bash %}
rake post title="A Title"
{% endhighlight %}

and you will get an [R Markdown](http://www.rstudio.com/ide/docs/authoring/using_markdown) (Rmd) file under `_source/` named `yyyy-mm-dd-a-title.Rmd`, which is a plain text file and you can edit it with your favorite text editor. At the moment, RStudio has the best support for Rmd files. Here is an [Rmd sample file](https://github.com/yihui/knitr-examples/blob/master/001-minimal.Rmd) and its [output](https://github.com/yihui/knitr-examples/blob/master/001-minimal.md).

If you do not have or understand `rake`, just copy an existing Rmd file, rename and open it with a text editor.

## Edit an Article

There are a few fields in the header such as `author` and `tags`; if you have multiple entries, use the comma to separate them, e.g. `author: [taiyun, yihui]`. Note all authors need to put their information in [`_config.yml`](https://github.com/supstat/vistat/blob/gh-pages/_config.yml), and input the author id's to the `author` field (the same applies to reviewers).

You can write math in the LaTeX syntax, e.g. `$$\alpha+\beta$$` in a paragraph renders inline like $$\alpha+\beta$$, and `$$f(x)=\frac{1}{\sqrt{2\pi}}e^{-x^2/2}$$` in a separate paragraph renders the display style

$$f(x)=\frac{1}{\sqrt{2\pi}}e^{-x^2/2}$$

If you want to generate animations, set `animation: true` in the preamble of the article and use the chunk option `fig.show='animate'` in the chunk header ([example](https://github.com/supstat/vistat/blob/gh-pages/_source/2012-11-06-brownian-motion-with-r.Rmd)).

## Compilation

The executable script `_bin/knit` is essentially an R script. For Linux/Mac users, you can compile an Rmd file to md by

{% highlight bash %}
./_bin/knit _source/yyyy-mm-dd-your-post.Rmd
{% endhighlight %}

For Windows users, use `Rscript` instead:

{% highlight bash %}
Rscript ./_bin/knit _source/yyyy-mm-dd-your-post.Rmd
{% endhighlight %}

You can certainly preview the article inside your editor like RStudio, and the above approach is necessary only when you are ready to submit the article. Do not worry about images -- we will compile your article again after it is accepted, and images will be re-generated and stored in the right place.

## Preview

If you want to preview your articles locally (<http://localhost:4000>), you can run

{% highlight bash %}
rake preview
{% endhighlight %}

which is basically a wrapper to `jekyll --server --auto`. Of course you need to install Jekyll first.

## Submission

After you are done with an article, commit it to your forked repository and submit a [pull request](https://help.github.com/articles/using-pull-requests) to us. We will get it reviewed and you will see comments online. Further revisions may be required, in which case you just make the revision and continue to commit in the changes, and they will appear in the previous pull request.

Please commit the source file only (`*.Rmd`) and do not commit the output files (`*.md` and figures). We will re-compile the source files and upload images after we accept the article. Therefore if your article involves special packages or data, you should add clear instructions on them in the article.

## Reviewers

Everyone is welcome to become a reviewer for Vistat. Reviews are public in the pull requests on Github. There are no _anonymous_ reviewers here.

## Contributors

We have had {{site.authors | size}} contributors so far:

{% for author in site.authors %}
- [{{author[1].name}}]({{author[1].homepage}}) {{ author[1].bio }}
{% endfor %}

