---
layout: site
title: BEAST 2 Help Me Choose Indicators prior
tags: []
---

## Indicators prior

This is the prior on the total number of population size changes in the population function of the extended Bayesian skyline model (Heled & Drummond, 2008).
If this number is zero, there are no population size changes and the model behaves like a coalescent with a constant population size.

Usually, a low number of population size changes should be encouraged, so a distribution with a low mean can be used for this.

This is an integer number, so a Poisson prior with a low mean value could be appropriate.

## References

Heled J, Drummond AJ. Bayesian inference of population size history from multiple loci. BMC evolutionary biology. 2008 Dec;8(1):1-5. <a href="https://doi.org/10.1186/1471-2148-8-289">doi:10.1186/1471-2148-8-289</a>.