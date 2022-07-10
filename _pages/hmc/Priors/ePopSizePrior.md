---
layout: site
title: BEAST 2 Help Me Choose Exponential pop size prior
tags: []
---

## Exponential pop size prior

This is the prior on the present day population size under the coalescent model with an exponential growth rate.
Note that this is the [effective population size](https://en.wikipedia.org/wiki/Effective_population_size), which can be  significantly smaller than the actual population size (Frankman, 1997).
Knowledge of actual population size can therefore not directly used to inform the prior, but values from the literature could be used for inspiration. 


The coalescent with constant population size is a special case of exponential growth with growth rate zero.
Arguably, the same approach as for the prior on population size with constant population applies to determining this prior: let \\(t_{low}, t_{hi}\\) be a rough estimate of the 95 % HPD interval for the tree height.
The population size \\(N\\) and root height \\(t\\) are related as \\((E[t]=2(1-1/N)\\) (Tavaré et al, 1997) so we can use \\(N=1-2/t\\) as mean for our prior, so by plugging in \\(t_{low}\\) for \\(t\\) gives us \\(N_{low}\\), and likewise plugging in \\(t_{hi}\\) for \\(t\\) gives use \\{N_{hi}\\.
Since population sizes are non-zero positive numbers, choose a distribution that has a positive range, like the log-normal or (inverse) gamma distribution.
Fit the 95% HPD to the \\(N_{low}\\) and \\(N_{hi}\\) values obtained above.

If a positive growth rate can be assumed the root of tree will be younger than under a constant population size. 
So, the population mean needs to be higher than under the constant population model. 
Unfortunately, there is no closed form formulat that I know if (please let me know if you know how to calculate this efficiently), the only way to see the effect of increasing the prior on population mean is to sample from the prior through MCMC.
Some experimentation may be necessary to get a satisfactory prior tree height.

See also [growth rate prior](/hmc/Priors/GrowthRatePrior/), [population size prior](/hmc/Priors/PopSizePrior/) for constant population.


## References

Frankham R. Effective population size/adult population size ratios in wildlife: a review. Genetics Research. 1995 Oct;66(2):95-107. <a href="https://doi.org/10.1017/S0016672300034455">doi:10.1017/S0016672300034455</a>.

Tavaré S, Balding DJ, Griffiths RC, Donnelly P. Inferring coalescence times from DNA sequence data. Genetics. 1997 Feb 1;145(2):505-18. <a href="http://doi.org/10.1093/genetics/145.2.505">doi:10.1093/genetics/145.2.505</a>.