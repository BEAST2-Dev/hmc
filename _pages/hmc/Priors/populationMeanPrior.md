---
layout: site
title: BEAST 2 Help Me Choose Population mean prior
tags: []
---

## Population mean prior

This is the prior on the hyperparameter representing the mean of exponential distribution over population sizes in the extended Bayesian skyline model (Heled & Drummond, 2008).
Note that this is the [effective population size](https://en.wikipedia.org/wiki/Effective_population_size), which can be  significantly smaller than the actual population size (Frankman, 1997).
Knowledge of actual population size can therefore not directly used to inform the prior, but values from the literature could be used for inspiration. 
Alternatively, use the following approach based on expected tree height:

Since there is no closed form formula for the expected tree height based on population sizes, a crude approximation is to use a rough estimate of the expected tree height ((\t\\), and take \\(N=1-2/t\\) as mean of the population size distribution.

Depending on how uncertain you are about the estimate, a 95% HPD around \\(N\\) can be established: if very uncertain, use two orders of magnitude giving range \\([N/0.01, 100N]\\), if uncertain use one order of magnitude giving range \\([N/0.1, 10N]\\).

Since the mean population is a positive number, a distribution with range from 0 to infinity like the log-normal or (inverse) gamma distribution is appropriate.
Note that a 1/X prior without bounds on \\(N\\) (which was the default in previous versions of BEAST 2) is not a proper prior, and can lead to problems when performing model selection or sampling from the prior.

Fit the chosen distribution to the 95% HPD established above.

It is recommended to sample from the prior to see how tree heights are affected by the remainder of the priors, and adjust thise population mean prior if they are not according to expectation.

## References

Frankham R. Effective population size/adult population size ratios in wildlife: a review. Genetics Research. 1995 Oct;66(2):95-107. <a href="https://doi.org/10.1017/S0016672300034455">doi:10.1017/S0016672300034455</a>.

Heled J, Drummond AJ. Bayesian inference of population size history from multiple loci. BMC evolutionary biology. 2008 Dec;8(1):1-5. <a href="https://doi.org/10.1186/1471-2148-8-289">doi:10.1186/1471-2148-8-289</a>.

