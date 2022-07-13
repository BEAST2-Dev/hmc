---
layout: site
title: BEAST 2 Help Me Choose Bactrian rate scale operator
tags: []
---

## Bactrian rate scale operator

Scale operator that finds scale factor according to a Bactrian distribution (Yang & Rodriguez, 2013), which is a mixture of two Gaussians: p(x) = 1/2*N(x;-m,1-m^2) + 1/2*N(x;+m,1-m^2) and more efficient than non-Bactrian scale operator.

## `kernelDistribution` (KernelDistribution)

Provides sample distribution for proposals (optional, default: bactrian)
See also [kernel distributions](../BactrianDistribution/).

## `parameter` (RealParameter)

The rate parameter is to be scaled.

## `scaleFactor` (Double)

Magnitude factor used for scaling. 
Larger values mean bolder proposals, but higher chance of rejection.
When `optimise` is set to true, this value is automatically tuned during MCMC.
A starting value of 0.1 seems to be OK in that case.

## `scaleAll` (Boolean)

If true, all elements of a parameter (not beast.tree) are scaled, otherwise one is randomly selected (optional, default: false)

## `scaleAllIndependently` (Boolean)

If true, all elements of a parameter (not beast.tree) are scaled with a different factor, otherwise a single factor is used (optional, default: false)

## `degreesOfFreedom` (Integer)

Degrees of freedom used when scaleAllIndependently=false and scaleAll=true to override default in calculation of Hasting ratio. Ignored when less than 1, default 0. (optional, default: 0)

## `indicator` (BooleanParameter)

Indicates which of the dimension of the parameters can be scaled. Only used when scaleAllIndependently=false and scaleAll=false. If not specified it is assumed all dimensions are allowed to be scaled. (optional)

## `rootOnly` (Boolean)

Scale root of a tree only, ignored if tree is not specified (default false) (optional, default: false)

## `optimise` (Boolean)

Flag to indicate that the scale factor is automatically changed in order to achieve a good acceptance rate (default true, recommended).

## `upper` (Double)

Upper Limit of scale factor (optional, default: 0.99999999)

## `lower` (Double)

Lower limit of scale factor (optional, default: 1.0E-8)

## `weight` (Double)

Weight with which this operator is selected (required).
Depending on how well the rate parameter mixes compared to other parameter, this weight can be increased (if ESSs are relatively low) or decreased (if ESSs are high).
See also [operator weight tuning](../OperatorWeights/).

## References

Yang Z, Rodríguez CE. Searching for efficient Markov chain Monte Carlo proposal kernels. Proceedings of the National Academy of Sciences. 2013 Nov 26;110(48):19307-12. [doi: 10.1073/pnas.1311790110](https://doi.org/10.1073/pnas.1311790110).
