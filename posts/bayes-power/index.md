---
title: Required sample sizes for Bayesian analysis
layout: single
author_profile: false
classes: wide
---

## What is this about?
For frequentist hypothesis testing, several power calculators (e.g. G\*Power[^1], powerandsamplesize.com[^2]) are available to determine the minimum sample size needed to detect an effect with a given probability (statistical power). No such calculators are available (to my knowledge) for the Bayesian versions of t-tests, ANOVA, and linear correlations returning a Bayes factor.[^3] Calculating statistical power for these techniques for given sample sizes can be done using simulation, and to save everyone a lot of time I will summarize my findings below.

Simulations and analyses were performed using Richard D. Morey's [BayesFactor](https://richarddmorey.github.io/BayesFactor/) package and the cluster computing [snowfall](https://cran.r-project.org/web/packages/snowfall/index.html) package for R.


## Minimum sample sizes needed

### Bayesian *t*-test
The analyses below show the minimum number of subjects needed *per condition* as a function of the true effect size in the population. This is based on a Bayes factor threshold of 3, a statistical power of 80% (i.e. you have an 80% probability of finding a BF<sub>10</sub> > 3), a noninformative Jeffreys prior placed on the variance of the normal population, and a Cauchy prior (JZS) placed on the standardized effect size with scale \\(\sqrt{2}/2\\). Note that these sample sizes are somewhat more conservative than a standard (frequentist) *t*-test.[^5] 

| Effect size[^4] | Cohen's *d* | Required sample size |
| --------------- | ----------- | -------------------- |
| Very small      | 0.01        | ~425,000             |
|                 | 0.10        | 3,050                |
| Small           | 0.20        | 667                  |
|                 | 0.30        | 275                  |
|                 | 0.40        | 147                  |
| Medium          | 0.50        | 91                   |
|                 | 0.60        | 62                   |
|                 | 0.70        | 45                   |
| Large           | 0.80        | 34                   |
|                 | 0.90        | 27                   |
|                 | 1.00        | 22                   |
| Very large      | 1.20        | 16                   |
| Huge            | 2.00        | 7                    |



[^1]: [https://www.psychologie.hhu.de/arbeitsgruppen/allgemeine-psychologie-und-arbeitspsychologie/gpower](https://www.psychologie.hhu.de/arbeitsgruppen/allgemeine-psychologie-und-arbeitspsychologie/gpower)
[^2]: [http://powerandsamplesize.com](http://powerandsamplesize.com)
[^3]: Note that the usefulness of Bayes factors is subject of discussion. Some authors (e.g. Kruschke) argue that precise description of posterior distributions is a better idea.
[^4]: Labels taken from Sawilowsky, S. (2009). New effect size rules of thumb. *Journal of Modern Applied Statistical Methods, 8,* 467–474. doi:10.22237/jmasm/1257035100
[^5]: See Rouder, J.N., Speckman, P.L., Sun, D., et al. (2009). Bayesian t tests for accepting and rejecting the null hypothesis. *Psychonomic Bulletin & Review, 16,* 225–237. doi:10.3758/PBR.16.2.225

