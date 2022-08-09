---
layout: site
title: BEAST 2 Help Me Choose Beta beta
tags: []
---

##  Beta distribution -- beta

Second shape parameter, defaults to 1.

The parameter `beta` can be interpreted as the number of times (plus one) a one has been observed, so setting `beta` to one means no observations, `beta=4` means 3 observations.
Likewise, the parameter `alpha` can be interpreted as the number of times (plus one) a zero has been observed.

If both `alpha` and `beta` shape parameters are 1, the Beta distribution becomes a uniform distribution.

Values of `alpha` and `beta` less than 1 lead to distributions that are highly skewed towards 0 and 1.

Values of `alpha` and `beta` more than 1 lead to distributions that have mean `alpha/(alpha+beta)` and zero density at 0 and 1.

See also [Beta distribution](https://en.wikipedia.org/wiki/Beta_distribution).


Jordan Douglas' distribution viewer: 
<iframe width='1224' height='768' src='https://jordandouglas.github.io/distributions/' title='Distribution Viewer'></iframe>
