---
layout: site
title: BEAST 2 Help Me Choose Site Model proportion invariable
tags: []
---

## Site Model proportion invariable

The proportion invariable represents the proportion of sites that is invariant, and is a value  between 0 (default) and 1 (Waddell, 1996).
When a significant number of sites in the alignment are constant sites (e.g. all A for all taxa for a larger number of sites), adding a proportion invariable sites can significantly improve the model fit.
Using a proportion invariable sites as implemented in BEAST 2 adds negligible computational cost, unlike adding gamma site rate categories.

Though it has been argued that mixing the invariable site model with the gamma site heterogeneity model leads to unidentifiability, this has been proven to be incorrect if care is taken in choosing the priors (Bouckaert 2020). 

## `value`

When no proportion invariable sites is desired, set it to 0. Set to a value larger than 0 but less than 1 if a proportion invariable sites is required.

## `estimate`

Though the proportion invariable sites can be determined from the alignment by calculating the number of sites that have the same character by maximum likelihood, it is preferable not mix maximum likelihood and Bayesian paradigms.
So, when a proportion invariable site model is desirable, the proportion is usually estimated.

## `lower` and `upper`

Since these are bounds on a proportion, the lower bound should be at least 0 and the upper at most 1.


## References

Bouckaert RR. OBAMA: OBAMA for Bayesian amino-acid model averaging. PeerJ. 2020 Aug 4;8:e9460. <a href="http://doi.org/10.7717/peerj.9460">doi:10.7717/peerj.9460</a>.

Waddell P. Evolutionary trees of apes and humans from DNA sequences. Handbook of human symbolic evolution. 1996:53-73.


See also [identifiability of gamma + I](http://www.beast2.org/2020/11/25/OBAMA.html), [gamma category count](gammaCategoryCount/), [gamma shape parameter](shape/).