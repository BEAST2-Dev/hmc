---
layout: site
title: BEAST 2 Help Me Choose Epoch Flex Operator
tags: []
---

## Epoch Flex Operator

Scale operator that scales random epoch in a tree

## `tree` (Tree)

Beast.tree on which this operation is performed (required)

## `kernelDistribution` (KernelDistribution)

Provides sample distribution for proposals (optional, default: bactrian)
See also [kernel distributions](/Operators/BactrianDistribution/index/).

## `optimise` (Boolean)

Flag to indicate that the scale factor is automatically changed in order to achieve a good acceptance rate (default true, recommended).

## `scaleFactor` (Double)

Scaling factor -- positive number that determines size of the jump: higher means bigger jumps. (optional, default: 0.05).

## `fromOldestTipOnly` (Boolean)

Only scale parts between root and oldest tip. If false, use any epoch between youngest tip and root. (optional, default: true).

## `groupSizes` (IntegerParameter)

The group sizes parameter. If specified, use group sizes as boundaries(and fromOldestTipOnly is ignored) (optional).

## `treeIntervals` (TreeIntervals)

Intervals for a phylogenetic beast tree. Must be specified if groupSizes is specified. (optional).

## `weight` (Double)

Weight with which this operator is selected (required).

