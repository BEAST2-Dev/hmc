---
layout: site
title: BEAST 2 Help Me Choose Bactrian random walk operator
tags: []
---

## Bactrian random walk operator

A random walk operator that selects a random dimension of the real parameter and perturbs the value a random amount according to a Bactrian distribution (Yang & Rodriguez, 2013), which is a mixture of two Gaussians:p(x) = 1/2*N(x;-m,1-m^2) + 1/2*N(x;+m,1-m^2) and more efficient than non-Bactrian RealRandomWalkOperator

## `parameter` (RealParameter)

The parameter to operate a random walk on. (required)

## `scaleFactor` (Double)

Scaling factor: larger means more bold proposals.
When `optimise` is true, this is automatically tuned during MCMC (recommended).

## `optimise` (Boolean)

Flag to indicate that the scale factor is automatically changed in order to achieve a good acceptance rate (default true)

## `kernelDistribution` (KernelDistribution)

Provides sample distribution for proposals (optional, default: bactrian)
See also [kernel distributions](/Operators/BactrianDistribution/index/).

## `weight` (Double)

Weight with which this operator is selected (required).
See also [operator weight tuning](/hmc/Operators/OperatorWeights/).

## References

Yang Z, Rodríguez CE. Searching for efficient Markov chain Monte Carlo proposal kernels. Proceedings of the National Academy of Sciences. 2013 Nov 26;110(48):19307-12. [doi: 10.1073/pnas.1311790110]((http
s://doi.org/10.1073/pnas.1311790110)).
