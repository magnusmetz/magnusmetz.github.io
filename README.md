# Vistat

When we see fancy graphs in a paper or a webpage, we often wonder how they
were made. This website serves as a gallery of statistical graphics and
visualizations with reproducible program code that makes the plots.

See <http://vis.supstat.com> for more information.

For admins, you are recommended to compile the website under Linux, and you
will need a couple of packages. For example, you can install them under
Ubuntu:

```bash
sudo apt-get install rake jekyll sshfs r-base
```

Then `install.packages('knitr')` in R. The whole website can be built (after
all missing packages have been installed) using

```bash
rake knit
```

and previewed at http://localhost:4000 by

```bash
rake preview
```
