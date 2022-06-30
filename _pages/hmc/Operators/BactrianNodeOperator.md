---
layout: site
title: BEAST 2 Help Me Choose Bactrian node operator
tags: []
---

## Bactrian node operator

Randomly selects true internal tree node (i.e. not the root) and move node height uniformly in interval restricted by the nodes parent and children.

## `scaleFactor` (Double)

Scaling factor: larger means more bold proposals (optional, default: 1.0).
Larger values mean bolder proposals, but lower acceptance rates.
The scale factor is automatically adjusted during MCMC for optimal balance when the optimise flag is set to true.

## `optimise` (Boolean)

Flag to indicate that the scale factor is automatically changed in order to achieve a good acceptance rate (default true).

## `kernelDistribution` (KernelDistribution)

Provides sample distribution for proposals (optional, default: bactrian).

## `markclades` (Boolean)

Mark all ancestors of nodes changed by the operator as changed, up to the MRCA of all nodes changed by the operator. (optional, default: false)
This option is used when a Pruned Tree ([BEASTLabs](https://github.com/BEAST2-Dev/BEASTLabs)) is included in the analyses, and can be left false for Standard template analyses.

## `weight` (Double)

Weight with which this operator is selected (required).
This is usually set quite high, since there are many nodes in the tree that need to be moved individually.


