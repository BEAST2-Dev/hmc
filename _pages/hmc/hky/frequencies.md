---
layout: site
title: BEAST 2 Help Me Choose HKY frequencies
tags: []
---

## HKY frequencies

Substitution model equilibrium state frequencies for the HKY (Hasegawa et al, 1985) nucleotide substitution model, 

Frequencies is set to one of `estimated`, `empirical` or `equal`:

* `estimated` = frequencies are estimated during the MCMC. This increases the number of parameters to be estimated compared to the other two options, and introduces some uncertainty, but follows the Bayesian philosophy closest. 
* `empirical` = frequencies are initialised according to the *maximum likelihood* estimate based on the alignment, so [fA, fC, fG, fT] is set proportional to [#A, #C, #G, #T] where #A is the number of As in the alignment, #C the number of Cs, etc. This reduces the number of parameters to be estimated compared to estimated frequencies, and is usually close to the frequency distribution when estimated. However, it may result in a slight bias of the substitution model parameter estimates, and the analysis does not take uncertainty of frequencies in account. Also, it mixes maximum likelihood paradigm in with a Bayesian analysis.
* `equal` = frequencies are set to [fA, fC, fG, fT] = [0.25, 0.25, 0.25, 0.25]. 

In general `estimated` is preferred, but if it hampers mixing and increasing the operator weight on the frequency operators does not help, `empirical` will provide a good alternative.


## References

Hasegawa M, Kishino H, Yano TA. Dating of the human-ape splitting by a molecular clock of mitochondrial DNA. Journal of molecular evolution. 1985 Oct;22(2):160-74. <a href="https://doi.org/10.1007%2FBF02101694"> doi:10.1007/BF02101694</a>.

See also [substitution models](/hmc/SiteModel/substModel/).
