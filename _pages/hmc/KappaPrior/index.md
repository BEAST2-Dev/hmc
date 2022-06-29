---
layout: site
title: BEAST 2 Help Me Choose Rate Kappa Prior
tags: []
---

## Kappa Prior

The kappa parameter of the HKY model (Hasegawa et al, 1985) represents how large transition rates are when all transversion rates are set to 1. 
Since this is a rate parameter, a distribution with a range from 0 upwards is appropriate.

Rosenberg et al, 2003 found that a `lognormal(M=1,S=1.25)` distribution fits well based on empirical observations, so this is the default prior in BEAST.

## References

Rosenberg MS, Subramanian S, Kumar S. Patterns of transitional mutation biases within and among mammalian genomes. Molecular biology and evolution. 2003 Jun 1;20(6):988-93. <a href="https://doi.org/10.1093/molbev/msg113">doi:10.1093/molbev/msg113</a>.

Hasegawa M, Kishino H, Yano TA. Dating of the human-ape splitting by a molecular clock of mitochondrial DNA. Journal of molecular evolution. 1985 Oct;22(2):160-74. <a href="https://doi.org/10.1007%2FBF02101694"> doi:10.1007/BF02101694</a>.
