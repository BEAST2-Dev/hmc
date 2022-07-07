---
layout: site
title: BEAST 2 Help Me Choose Gamma shape prior
tags: []
---

## Gamma Shape Prior

The gamma shape prior is the prior on the gamma shape parameter of the gamma site rate heterogeneity model (Yang, 1994).

Use of the model implies some variability is to be expected in the rate at which sites evolve.

Gamma shape values over 16 can be considered implausible, given at these values there is no substantial difference between slowest and fastest category rate in the model.

Gamma shape values below 0.1 lead to the slowest rates being practically indistinguishable from zero (Bouckaert 2020), and a category with invariable rates is more efficient since the BEAST 2 implementation calculates its contribution in constant time.

So, a lower bound of 0.1 and upper bound of 16 can be argued to be sensible.
By default, BEAUti suggests an exponential distribution with mean 1 for the gamma shape prior.


## References

Bouckaert RR. OBAMA: OBAMA for Bayesian amino-acid model averaging. PeerJ. 2020 Aug 4;8:e9460. <a href="http://doi.org/10.7717/peerj.9460">doi:10.7717/peerj.9460</a>.

Yang Z. Maximum likelihood phylogenetic estimation from DNA sequences with variable rates over sites: approximate methods. Journal of Molecular evolution. 1994 Sep;39(3):306-14. <a href="http://doi.org/10.1007/BF00160154">doi:10.1007/BF00160154</a>.
