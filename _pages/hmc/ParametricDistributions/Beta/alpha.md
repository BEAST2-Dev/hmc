---
layout: site
title: BEAST 2 Help Me Choose Beta alpha
tags: []
---

## Beta distribution -- alpha

First shape parameter, defaults to 1.
If both `alpha` and `beta` shape parameters are 1, the Beta distribution becomes a uniform distribution.

The parameter `alpha` can be interpreted as the number of times (plus one) a zero has been observed, so setting `alpha` to one means no observations, `alpha=4` means 3 observations.
Likewise, the parameter `beta` can be interpreted as the number of times (plus one) a one has been observed.

Values of `alpha` and `beta` less than 1 lead to distributions that are highly skewed towards 0 and 1.

Values of `alpha` and `beta` more than 1 lead to distributions that have mean `alpha/(alpha+beta)` and zero density at 0 and 1.


See also [Beta distribution](https://en.wikipedia.org/wiki/Beta_distribution).


Jordan Douglas' distribution viewer: 
<iframe width='1224' height='768' src='https://jordandouglas.github.io/distributions/' title='Distribution Viewer'></iframe>
