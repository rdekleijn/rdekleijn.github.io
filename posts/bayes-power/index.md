---
title: Required sample sizes for Bayesian analysis
layout: single
author_profile: false
classes: wide
---

## What is this about?
For frequentist hypothesis testing, several power calculators (e.g. G\*Power[^1], powerandsamplesize.com[^2]) are available to determine the minimum sample size needed to detect an effect with a given probability (statistical power). No such calculators are available (to my knowledge) for the Bayesian versions of t-tests, ANOVA, and linear correlations returning a Bayes factor[^3]. Calculating statistical power for these techniques for given sample sizes is done using simulation, and to save everyone a lot of time I will summarize my findings below.

Simulations and analyses were performed using Richard D. Morey's [BayesFactor](https://richarddmorey.github.io/BayesFactor/) package and the cluster computing [snowfall](https://cran.r-project.org/web/packages/snowfall/index.html) package for R.


## Minimum sample sizes needed
The analyses below show the minimum number of subjects needed per condition as a function of the true effect size in the population. This is based on Bayes factor threshold of 3, and a statistical power of 80% (i.e. you have an 80% probability of finding a BF<sub>10</sub> > 3).

| Effect size | Cohen's *d* | Required sample size |
| ----------- | ----------- | -------------------- |
| Very small  | 0.01        | >5000                |
| Small       | 0.20        | 664.                 |



[^1]: [https://www.psychologie.hhu.de/arbeitsgruppen/allgemeine-psychologie-und-arbeitspsychologie/gpower](https://www.psychologie.hhu.de/arbeitsgruppen/allgemeine-psychologie-und-arbeitspsychologie/gpower)
[^2]: [http://powerandsamplesize.com](http://powerandsamplesize.com)
[^3]: Note that the usefulness of Bayes factors is subject of discussion. Some authors argue that precise description of posterior distributions is a better idea.
