---
title: Required sample sizes for Bayesian analysis
layout: single
author_profile: false
classes: wide
---

## What is this about?
For frequentist hypothesis testing, several power calculators (e.g. G\*Power[^1], powerandsamplesize.com[^2]) are available to determine the minimum sample size needed to detect an effect with a given probability (statistical power). No such calculators are available (to my knowledge) for the Bayesian versions of *t*-tests, ANOVA, and linear correlations returning a Bayes factor.[^3] Calculating statistical power for these techniques for given sample sizes cannot be done analytically but can be done using simulation, and to save everyone a lot of time I will summarize my findings below.

## Minimum sample sizes needed

### Bayesian *t*-test
The analyses below show the minimum number of subjects needed *per condition* as a function of the true effect size in the population. This is based on a Bayes factor threshold of 3, a statistical power of 80% (i.e. you have an 80% probability of finding a BF<sub>10</sub> > 3), a noninformative Jeffreys prior placed on the variance of the normal population, and a Cauchy prior (JZS) placed on the standardized effect size with scale \\(\sqrt{2}/2\\). Note that these sample sizes are somewhat more conservative than a standard (frequentist) *t*-test.[^5] In the rightmost column you can find the required sample size for a standard (frequentist) *t*-test to reject the null hypothesis using a desired significance level of .05.

| True effect size[^4] | Cohen's *d* | Bayesian sample size | Frequentist sample size |
| -------------------- | ----------- | -------------------- | ----------------------- |
|                      | 0.00 (null) | 102[^6]              | N/A                     |
| Very small           | 0.01        | ~425,000             | 156,656                 |
|                      | 0.10        | 3,050                | 1,567                   |
| Small                | 0.20        | 667                  | 392                     |
|                      | 0.30        | 275                  | 175                     |
|                      | 0.40        | 147                  | 98                      |
| Medium               | 0.50        | 91                   | 63                      |
|                      | 0.60        | 62                   | 44                      |
|                      | 0.70        | 45                   | 32                      |
| Large                | 0.80        | 34                   | 25                      |
|                      | 0.90        | 27                   | 20                      |
|                      | 1.00        | 22                   | 16                      |
| Very large           | 1.20        | 16                   | 11                      |
| Huge                 | 2.00        | 7                    | 4                       |

### Bayesian test for linear correlation
The analyses below show the minimum number of paired observations (data points) needed as a function of the true correlation \\(\rho\\) in the population. This is based on a Bayes factor threshold of 3, a statistical power of 80% (i.e. you have an 80% probability of finding a BF<sub>10</sub> > 3), noninformative priors assumed for the population means and variances of the two populations, and a \\(\operatorname{Beta}(3,3)\\) prior distribution is assumed for \\(\rho\\). 

| True effect size[^7] | \\(\rho\\)  | Bayesian sample size | Frequentist sample size |
| -------------------- | ----------- | -------------------- | ----------------------- |
|                      | 0.00 (null) | 245[^6]              | N/A                     |
| Small                | 0.10        | 1300                 | 782                     |
|                      | 0.20        | 273                  | 193                     |
| Medium               | 0.30        | 109                  | 84                      |
|                      | 0.40        | 54                   | 46                      |
| Large                | 0.50        | 32                   | 29                      |
|                      | 0.60        | 21                   | 19                      |
|                      | 0.70        | 15                   | 13                      |
|                      | 0.80        | 11                   | 9                       |
|                      | 0.90        | 8                    | 6                       |

## Software used
Simulations and analyses were performed using Richard D. Morey's [BayesFactor](https://richarddmorey.github.io/BayesFactor/) package and the cluster computing [snowfall](https://cran.r-project.org/web/packages/snowfall/index.html) package for R.


[^1]: [https://www.psychologie.hhu.de/arbeitsgruppen/allgemeine-psychologie-und-arbeitspsychologie/gpower](https://www.psychologie.hhu.de/arbeitsgruppen/allgemeine-psychologie-und-arbeitspsychologie/gpower)
[^2]: [http://powerandsamplesize.com](http://powerandsamplesize.com)
[^3]: Note that the usefulness of Bayes factors is subject of discussion. Some authors (e.g. Kruschke) argue that precise description of posterior distributions is a better idea.
[^4]: Labels taken from Sawilowsky, S. (2009). New effect size rules of thumb. *Journal of Modern Applied Statistical Methods, 8,* 467–474. doi:10.22237/jmasm/1257035100
[^5]: See Rouder, J.N., Speckman, P.L., Sun, D., et al. (2009). Bayesian t tests for accepting and rejecting the null hypothesis. *Psychonomic Bulletin & Review, 16,* 225–237. doi:10.3758/PBR.16.2.225
[^6]: This concerns the sample size needed for BF<sub>01</sub> > 3 in the case where the true effect size is zero.
[^7]: Labels taken from Cohen, J. (1988). *Statistical power analysis for the behavioral sciences (2nd ed.)*

