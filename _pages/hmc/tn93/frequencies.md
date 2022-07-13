---
layout: site
title: BEAST 2 Help Me Choose TN93 frequencies
tags: []
---

## TN93 frequencies

Substitution model equilibrium state frequencies for the TN93 nucleotide substitution model (Tamura & Nei, 1993). 

Frequencies is set to one of `estimated`, `empirical` or `equal`:

* `estimated` = frequencies are estimated during the MCMC. This increases the number of parameters to be estimated compared to the other two options, and introduces some uncertainty, but follows the Bayesian philosophy closest. 
* `empirical` = frequencies are initialised according to the *maximum likelihood* estimate based on the alignment, so [fA, fC, fG, fT] is set proportional to [#A, #C, #G, #T] where #A is the number of As in the alignment, #C the number of Cs, etc. This reduces the number of parameters to be estimated compared to estimated frequencies, and is usually close to the frequency distribution when estimated. However, it may result in a slight bias of the substitution model parameter estimates, and the analysis does not take uncertainty of frequencies in account. Also, it mixes maximum likelihood paradigm in with a Bayesian analysis.
* `equal` = frequencies are set to [fA, fC, fG, fT] = [0.25, 0.25, 0.25, 0.25]. 

In general `estimated` is preferred, but if it hampers mixing and increasing the operator weight on the frequency operators does not help, `empirical` will provide a good alternative.

See also [substitution models](../../SiteModel/substModel).

## References

Tamura K, Nei M. Estimation of the number of nucleotide substitutions in the control region of mitochondrial DNA in humans and chimpanzees. Molecular biology and evolution. 1993 May 1;10(3):512-26. <a href="https://doi.org/10.1093%2Foxfordjournals.molbev.a040023">doi:10.1093/oxfordjournals.molbev.a040023</a>.
