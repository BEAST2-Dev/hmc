---
layout: site
title: BEAST 2 Help Me Choose Site Model shape
tags: []
---

## Site Model shape

Shape parameter of gamma distribution used when the gamma site rate heterogeneity model (Yang, 1994) is used, and the [gamma category count](../gammaCategoryCount/) is set to a number larger than 1.
The shape parameter is ignored if gammaCategoryCount is 1 or less.

## `value` and `estimate`

It is unusual for the shape parameter not to be estimated, so BEAUti automatically set the estimate flag to true when gamma category count is set to a number larger than 1. Also, it unsets the flag if the gamma category count is set back to 1 or lower.

A reasonable starting value for the shape parameter is 1.

## `lower`

Shape parameter values lower than 0.1 lead to site rate very close to 0 (Bouckaert, 2020). 
If this happens, there are probably a lot of invariable sites in the alignment, and using the invariable site model (possibly in combination with gamma site rate heterogeneity) makes more sense than using the a shape parameter with such very low value. 
Note that using the invariable site model as implemented in BEAST 2 adds negligible computational cost, unlike adding gamma site rate categories.

Therefore, a lower bound of 0.1 is recommended.

## `upper`

An upper bound is not necessary or useful. 
However, if shape parameter estimates become large (>16), this indicates there is hardly any site heterogeneity in the data, and it is computationally more efficient to not use the gamma site rate heterogeneity model (i.e. set category count to 1).

## References

Bouckaert RR. OBAMA: OBAMA for Bayesian amino-acid model averaging. PeerJ. 2020 Aug 4;8:e9460. <a href="http://doi.org/10.7717/peerj.9460">doi:10.7717/peerj.9460</a>.

Yang Z. Maximum likelihood phylogenetic estimation from DNA sequences with variable rates over sites: approximate methods. Journal of Molecular evolution. 1994 Sep;39(3):306-14. <a href="http://doi.org/10.1007/BF00160154">doi:10.1007/BF00160154</a>.

See also [identifiability of gamma + I](http://www.beast2.org/2020/11/25/OBAMA.html), [gamma category count](../gammaCategoryCount/), [proportion invariable](../proportionInvariant/).