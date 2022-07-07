---
layout: site
title: BEAST 2 Help Me Choose Proportion invariable prior
tags: []
---

## Proportion invariable Prior

The proportion invariable prior is the prior on the proportion invariable parameter in the site model (Waddell, 1996).
Usually, the proportion invariable parameter converges to somewhere close to the proportion of constants sites in the alignment, i.e., sites that only contain a single character.
This model can be chosen when a substantial number of sites can be expected to be invariable, or -- since there is no computational penalty in the BEAST 2 implementation -- even when there is not.

Because there tends to be a lot of information in the data driving the proportion invariable estimate, no strong prior is required, and a uniform prior on the range 0 to 1 is fine.

If more information is available, a Beta distribution could be a good alternative, allowing the proportion invariable to be in the range 0 to 1, but with more emphasis on the range where the proportion can be expected to be.
For example a Beta(alpha=1,beta=4) prior used in Bouckaert (2020) puts more emphasis on lower rather than larger values of the proportion invariant, and allowed for identifiability in combination with gamma site heterogeneity when the lower bound on the shape parameter was set to 0.1 (Bouckaert, 2020).


## References

Bouckaert RR. OBAMA: OBAMA for Bayesian amino-acid model averaging. PeerJ. 2020 Aug 4;8:e9460. <a href="http://doi.org/10.7717/peerj.9460">doi:10.7717/peerj.9460</a>.

Waddell P. Evolutionary trees of apes and humans from DNA sequences. Handbook of human symbolic evolution. 1996:53-73.