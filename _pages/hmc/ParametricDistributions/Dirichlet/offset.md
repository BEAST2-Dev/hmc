---
layout: site
title: BEAST 2 Help Me Choose Dirichlet offset
tags: []
---

## Dirichlet offset

Offset of origin (defaults to 0), which shifts the distribution by a fixed amount, namely the offset.
Setting the offset to `x` means lower bounds becomes `x` and the mean has `x` added to them.
It does not affect the variance.

This can be useful for example to specify a node calibration with a gamma distribution when a lower bound is known beforehand.


See also [Dirichlet distribution](https://en.wikipedia.org/wiki/Dirichlet_distribution).
