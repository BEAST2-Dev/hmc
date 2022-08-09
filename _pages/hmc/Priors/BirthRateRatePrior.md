---
layout: site
title: BEAST 2 Help Me Choose Birth rate *rate* prior
tags: []
---

## Birth rate *rate* prior 

The Yule skyline model is a pure-birth model where each epoch is associated with a birth rate. This model is useful when all tips are sampled at the same time. The birth rate of each epoch is sampled from a Gamma(&alpha; &beta;) distribution where &alpha; is the shape and &beta; is the rate. Here, we provide a guide for selecting a prior distribution for the birth rate *rate* &beta;.  Also see the [Yule sklyline blog post](https://www.beast2.org/2022/06/01/yule-skyline-tree-prior.html).

## Step 1: Estimate uncertainty in birth rate &lambda;

Estimate the uncertainty behind the birth rate &lambda; under the standard 1-epoch Yule model using this [Step 1 & 2](https://beast2-dev.github.io/hmc/hmc/Priors/YuleBirthRatePrior/) for the Yule birth rate prior.


## Step 2: Parameterise a distribution

Here, &lambda; will be drawn from a Gamma(&alpha;, &beta;) distribution. By default, &alpha;=2. Here, we must select &beta; such that the 95% credible interval of the Gamma distribution is equal to the upper and lower 95% HPD intervals of &lambda;.  This can be [achieved using R](https://www.beast2.org/2017/05/05/using-r-to-estimate-probability-distribution-parameters-using-quantiles-or-hpd-intervals.html).



## Alternative: specify root age prior.

Since the effective birth rate and root age are linked through the Yule Skyline prior, setting a prior on the root age can keep the birth rate in check, even with improper priors. See [root age prior](../RootAgePrior/) for details.





## References

Bouckaert, RR. An efficient coalescent epoch model for Bayesian phylogenetic inference. Sys Bio, syac015, 2022 [doi:10.1093/sysbio/syac015](https://doi.org/10.1093/sysbio/syac015)
