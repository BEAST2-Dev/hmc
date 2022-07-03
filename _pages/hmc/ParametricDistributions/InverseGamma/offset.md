---
layout: site
title: BEAST 2 Help Me Choose Inverse Gamma offset
tags: []
---

## Inverse Gamma offset

Offset of origin (defaults to 0), which shifts the distribution by a fixed amount, namely the offset.
Setting the offset to `x` means lower bounds becomes `x` and the mean has `x` added to them.
It does not affect the variance.

This can be useful for example to specify a node calibration with an inverse gamma distribution when a lower bound is known beforehand.


See also: [Inverse gamma distribution](https://en.wikipedia.org/wiki/Inverse-gamma_distribution).


Jordan Douglas' distribution viewer: 
<iframe width='1224' height='768' src='https://jordandouglas.github.io/distributions/' title='Distribution Viewer'></iframe>
