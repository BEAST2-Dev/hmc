---
layout: site
title: BEAST 2 Help Me Choose Kappa 1 prior
tags: []
---

## Kappa 1 Prior

The kappa1 parameter of the TN93 model (Tamura, Nei, 1993) represents how large transition rate A <-> G is when all transversion rates are set to 1. 
Since this is a rate parameter, a distribution with a range from 0 upwards is appropriate.

Rosenberg et al, 2003 found that a `lognormal(M=1,S=1.25)` distribution fits transition rates well based on empirical observations, so this is the default prior in BEAST.

## References

Rosenberg MS, Subramanian S, Kumar S. Patterns of transitional mutation biases within and among mammalian genomes. Molecular biology and evolution. 2003 Jun 1;20(6):988-93. <a href="https://doi.org/10.1093/molbev/msg113">doi:10.1093/molbev/msg113</a>.

Tamura K, Nei M. Estimation of the number of nucleotide substitutions in the control region of mitochondrial DNA in humans and chimpanzees. Molecular biology and evolution. 1993 May 1;10(3):512-26. <a href="https://doi.org/10.1093%2Foxfordjournals.molbev.a040023">doi:10.1093/oxfordjournals.molbev.a040023</a>.

