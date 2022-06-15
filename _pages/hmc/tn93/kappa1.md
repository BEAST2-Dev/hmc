---
layout: site
title: BEAST 2 Help Me Choose tn93 kappa1
tags: []
---

## TN93 kappa1

The kappa1 parameter in the TN93 () nucleotide substitution model represents how large the A<->G transition rate is when all transversion rates are set to 1. 

### `value`

Since the transition rates (A <=> G and C <=> T) tend to be larger than transversion rates (A <=> C, A <=> T, C <=> G and G <=> T), one expects a value larger than 1 for kappa1. The default of 2 makes a good starting value. If not estimated, a value based on prior information can be used, but this would reduce the uncertainty in the analysis.

### `estimate`

Kappa1 can vary per dataset, so it is usually estimated under a `lognormal(M=1,S=1.25)` prior based on empirical observations of Rosenberg et al, 2003. When estimated, the start value usually does not matter too much if it is in the same order of magnitude as transitions, i.e. 1.

### `lower`

Since kappa1 is a rate parameter, it should always be positive and have a lower bound of at least 0. This is only relevant if `estimate` is true and ignored otherwise.

### `upper`

An upper value for the kappa1 parameter is usually not set, though kappa1 is usually in the range of 1 to low tens.
This is only relevant if `estimate` is true and ignored otherwise.

## References

Rosenberg MS, Subramanian S, Kumar S. Patterns of transitional mutation biases within and among mammalian genomes. Molecular biology and evolution. 2003 Jun 1;20(6):988-93. <a href="https://doi.org/10.1093/molbev/msg113">doi:10.1093/molbev/msg113</a>.

Tamura K, Nei M. Estimation of the number of nucleotide substitutions in the control region of mitochondrial DNA in humans and chimpanzees. Molecular biology and evolution. 1993 May 1;10(3):512-26. <a href="https://doi.org/10.1093%2Foxfordjournals.molbev.a040023">doi:10.1093/oxfordjournals.molbev.a040023</a>.

See also [TN93 kappa2](kappa2/).
