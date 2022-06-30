---
layout: site
title: BEAST 2 Help Me Choose Bactrian delta exchange operator
tags: []
---

## Bactrian delta exchange operator

Delta exchange operator that proposes through a Bactrian distribution for real valued parameters.

## `parameter` (RealParameter) or `intparameter` (IntegerParameter)

One of both should be specified -- this parameter is operated on.

## `delta` (Double)

Magnitude of change for two randomly picked values.
If auto optimize is set to true, this value will be adjusted for optimal balance between boldness of moves and acceptance probability.

## `autoOptimize` (Boolean)

If true, the window size `delta` will be adjusted during the MCMC run to improve mixing. 

## `integer` (Boolean)

If true, changes are all integers. Can usually be left to false.

## `weightvector` (IntegerParameter)

Weights on a vector parameter (optional). 
The mean of the items will be left unchanged.
For example, mutation rates for differently sized partitions can be updated so that the mean mutation rate per site remains 1 after a proposal.

## `kernelDistribution`  (KernelDistribution)

Provides sample distribution for proposals (optional, default: bactrian). 
See also [kernel distributions](/Operators/BactrianDistribution/index/).


## `weight` (Double)

Weight with which this operator is selected (required).
Usually left fairly low, unless the parameter operated on (e.g. frequencies for a substitution model) is very low compared to other parameters.


