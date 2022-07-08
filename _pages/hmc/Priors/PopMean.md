---
layout: site
title: BEAST 2 Help Me Choose Pop mean prior
tags: []
---

## Pop mean prior

This is the prior on the scale parameter of the gamma distribution over population sizes for the SpeciesTreePrior in StarBeast.
This makes this parameter half the expected population size on all branches for constant population function, but a quarter of the expected population size for tip branches only for linear population functions.

Consider using StarBeast3 (Douglas et al, 2022) instead, which is much more efficient.

## References

Douglas J, Jiménez-Silva CL, Bouckaert R. StarBeast3: Adaptive Parallelized Bayesian Inference under the Multispecies Coalescent. Systematic Biology. 2022 Feb 17. <a href="http://doi.org/10.1093/sysbio/syac010">doi:10.1093/sysbio/syac010</a>.
