---
layout: site
title: BEAST 2 Help Me Choose Standard Template Clock Model
tags: []
---

## Choosing a clock model

Here, we will consider the strict clock, uncorrelated relaxed clock (Drummond et al, 2006, Douglas et al, 2021) and random local clock (Drummond & Suchard, 2010).

## Initial exploration

For an initial run when no experience with the type of data is available, running with the strict clock and simple substitution model and tree prior is a good way to find out whether there is signal in the data.

A relaxed clock analysis can then be added if there are a good number of mutations in the data and a reasonable number of taxa. 
If the distribution of the coefficient of variation is hugging zero, this is a signal that there is little rate variation among branches, and a strict clock is supported by the data.
If this distribution is not touching zero, this is a signal there is rate variation and a relaxed clock is supported by the data.
If you are unsure, you can run a [path sampling](https://github.com/BEAST2-Dev/model-selection) or [nested sampling](https://github.com/BEAST2-Dev/nested-sampling) analysis to perform Bayesian hypothesis testing.

## Which relaxed clock model to use

There are three implementations of relaxed clock models in BEAST 2

* the classic uncorrelated relaxed clock (Drummond et al, 2006) that works well when rates and branch lengths are not very correlated, but is not efficient when they are.
* a version that introduces new operators (Zhang & Drummond, 2020) that works well when branch lengths and rates are highly correlated, but is less efficient if they are not.
* the [optimised relaxed clock](https://github.com/jordandouglas/ORC)(ORC) version that adapt operators (Douglas et al, 2021) and works well whether the rates and branch lengths are correlated or not and due to new operators is more efficient than the other two.

Unless a specific feature of the first two implementation is of interest, the ORC should be used for best performance.

## Further exploring the relaxed clock

If a relaxed clock is supported, there is a choice of different clock rate distributions. The default for ORC is a log-normal distribution, but exponential and gamma distributions are options as well. 
Make sure to make the mean of the distribution 1, since the rates are relative to the mean clock rate in ORC.
For example, for the exponential set the mean to 1 and do not estimate this parameter.
For a gamma, set `mode` to `OneParameter` and estimate the `alpha` parameter (`beta` is ignored in this parameterisation) and specify a prior on `alpha`.

If no substantial differences are observed in the posterior distribution ([trees appear to be similar](https://www.beast2.org/2020/04/20/comparing-tree-sets.html) and parameter estimates appear the same in Tracer) choose one of the rate distributions and report the analysis is robust for the choice of distribution.

However, if substantial differences are observed, a [path sampling](https://github.com/BEAST2-Dev/model-selection) or [nested sampling](https://github.com/BEAST2-Dev/nested-sampling) analysis may be required for selecting the most appropriate model.

## Further explorations

A random local clock allows the clock model to behave like a strict clock (if there are no rate changes) and a relaxed clock (if there are many rate changes).
The number of rate changes is sampled during MCMC, and is drive by the data and prior.
From this perspective, it is superior to the strict clock and relaxed clock models.
However, it may suffer from convergence issues.



## References

Douglas J, Zhang R, Bouckaert R. Adaptive dating and fast proposals: Revisiting the phylogenetic relaxed clock model. PLoS computational biology. 2021 Feb 2;17(2):e1008322. <a href="https://doi.org/10.1371/journal.pcbi.1008322">doi:10.1371/journal.pcbi.1008322</a>.

Drummond AJ, Ho SY, Phillips MJ, Rambaut A. Relaxed phylogenetics and dating with confidence. PLoS biology. 2006 May;4(5):e88. <a href="https://doi.org/10.1371/journal.pbio.0040088">doi:10.1371/journal.pbio.0040088</a>

Drummond AJ, Suchard MA. Bayesian random local clocks, or one rate to rule them all. BMC biology. 2010 Dec;8(1):1-2. <a href="https://doi.org/10.1186/s12862-020-01609-4">doi:10.1186/s12862-020-01609-4</a>.

Zhang R, Drummond A. Improving the performance of Bayesian phylogenetic inference under relaxed clock models. BMC evolutionary biology. 2020 Dec;20(1):1-28.