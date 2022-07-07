---
layout: site
title: BEAST 2 Help Me Choose Bactrian tree scale operator
tags: []
---

## Bactrian Scale Operator

Scale operator that finds scale factor according to a Bactrian distribution (Yang & Rodriguez, 2013), which is a mixture of two Gaussians: p(x) = 1/2*N(x;-m,1-m^2) + 1/2*N(x;+m,1-m^2) and more efficient than non-Bactrian scale operator.

## `kernelDistribution` (KernelDistribution)

Provides sample distribution for proposals (optional, default: bactrian)
See also [kernel distributions](/Operators/BactrianDistribution/index/).

## `tree` (Tree)

Beast tree for wich divergence times are scaled.

## `scaleFactor` (Double)

Magnitude factor used for scaling. 
Larger values mean bolder proposals, but higher chance of rejection.
When `optimise` is set to true, this value is automatically tuned during MCMC.
A starting value of 0.1 seems to be OK in that case.

## `rootOnly` (Boolean)

Scale root of a tree only, ignored if tree is not specified.
For scaling the whole tree, the epoch flex and tree stretch operators are more efficient, so `rootOnly=true` is recommended.

## `optimise` (Boolean)

Flag to indicate that the scale factor is automatically changed in order to achieve a good acceptance rate (default true, recommended).

## `upper` (Double)

Upper Limit of scale factor (optional, default: 0.99999999).

## `lower` (Double)

Lower limit of scale factor (optional, default: 1.0E-8).

## `weight` (Double)

Weight with which this operator is selected (required).
See also [operator weight tuning](/hmc/Operators/OperatorWeights/)

## References

Yang Z, Rodríguez CE. Searching for efficient Markov chain Monte Carlo proposal kernels. Proceedings of the National Academy of Sciences. 2013 Nov 26;110(48):19307-12. [doi: 10.1073/pnas.1311790110]((http
s://doi.org/10.1073/pnas.1311790110)).
