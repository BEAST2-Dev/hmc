---
layout: site
title: BEAST 2 Help Me Choose HKY kappa
tags: []
---

## HKY kappa

The kappa parameter in the HKY (Hasegawa et al, 1985) nucleotide substitution model represents how large transition rates are when all transversion rates are set to 1. 

### `value`

Since the transition rates (A <=> G and C <=> T) tend to be larger than transversion rates (A <=> C, A <=> T, C <=> G and G <=> T), one expects a value larger than 1 for kappa. The default of 2 makes a good starting value. If not estimated, a value based on prior information can be used, but this would reduce the uncertainty in the analysis.

### `estimate`

Kappa can vary per dataset, so it is usually estimated under a `lognormal(M=1,S=1.25)` prior based on empirical observations of Rosenberg et al, 2003. When estimated, the start value usually does not matter too much if it is in the same order of magnitude as transitions, i.e. 1.

### `lower`

Since kappa is a rate parameter, it should always be positive and have a lower bound of at least 0. This is only relevant if `estimate` is true and ignored otherwise.

### `upper`

An upper value for the kappa parameter is usually not set, though kappa is usually in the range of 1 to low tens.
This is only relevant if `estimate` is true and ignored otherwise.

## References

Rosenberg MS, Subramanian S, Kumar S. Patterns of transitional mutation biases within and among mammalian genomes. Molecular biology and evolution. 2003 Jun 1;20(6):988-93. <a href="https://doi.org/10.1093/molbev/msg113">doi:10.1093/molbev/msg113</a>.

Hasegawa M, Kishino H, Yano TA. Dating of the human-ape splitting by a molecular clock of mitochondrial DNA. Journal of molecular evolution. 1985 Oct;22(2):160-74. <a href="https://doi.org/10.1007%2FBF02101694"> doi:10.1007/BF02101694</a>.

See also [substitution models](https://en.wikipedia.org/wiki/Substitution_model).
