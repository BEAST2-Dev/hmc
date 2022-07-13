---
layout: site
title: BEAST 2 Help Me Choose Tree stretch operator
tags: []
---

## Tree stretch operator

Scales tree skewing parts to take tip dates in account

## `meanRate` (RealParameter)

Mean clock rate -- inversely scaled if specified, but ignored if not specified.

## `tree` (Tree)

Beast.tree on which this operation is performed (required)

## `kernelDistribution` (KernelDistribution)

Provides sample distribution for proposals (optional, default: bactrian)
See also [kernel distributions](../BactrianDistribution/).

## `optimise` (Boolean)

Flag to indicate that the scale factor is automatically changed in order to achieve a good acceptance rate (default true).

## `scaleFactor` (Double)

Scaling factor -- positive number that determines size of the jump: higher means bigger jumps. (optional, default: 0.05).

## `fromOldestTipOnly` (Boolean)

Only scale parts between root and oldest tip. 
If false, use any epoch between youngest tip and root. (optional, default: true).
When tips are not dated, this option has no effect.

When tips are dated, a mixture of two tree stretch operators works best: one with `fromOldestTipOnly` true, and one with false.

## `groupSizes` (IntegerParameter)

The group sizes parameter. If specified, use group sizes as boundaries (and `fromOldestTipOnly` is ignored).

## `treeIntervals` (TreeIntervals)

Intervals for a phylogenetic beast tree. 
Must be specified if groupSizes is specified. (optional)

## `weight` (Double)

Weight with which this operator is selected (required).
See also [operator weight tuning](../OperatorWeights/).

