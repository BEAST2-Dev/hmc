---
layout: site
title: BEAST 2 Help Me Choose Bactrian Up Down Operator
tags: []
---

## Bactrian Up Down Operator

Like the non Bactrian UpDownOperator, this element represents an operator that scales two (or more) parameters in different directions, but uses a Bactrian proposal distribution for the scale value. 
The up parameter is multiplied by this scale and the down parameter is divided by this scale.

## `scaleFactor` (Double)

Magnitude factor used for scaling. 
Larger values mean bolder proposals, but higher chance of rejection.
When `optimise` is set to true, this value is automatically tuned during MCMC.
A starting value of 0.1 seems to be OK in that case.

## `up` (StateNode)

Zero or more items to scale upwards (optional, default: [])

## `down` (StateNode)

Zero or more items to scale downwards (optional, default: [])

## `optimise` (Boolean)

Flag to indicate that the scale factor is automatically changed in order to achieve a good acceptance rate (default true) (optional, default: true)

## `elementWise` (Boolean)

Flag to indicate that the scaling is applied to a random index in multivariate parameters (default false) (optional, default: false)

## `upper` (Double)

Upper Limit of scale factor (optional, default: 10.0)

## `lower` (Double)

Lower limit of scale factor (optional, default: 0.0)

## `kernelDistribution` (KernelDistribution)

Provides sample distribution for proposals (optional, default: bactrian)
See also [kernel distributions](/Operators/BactrianDistribution/index/).

## `weight` (Double)

Weight with which this operator is selected (required)

