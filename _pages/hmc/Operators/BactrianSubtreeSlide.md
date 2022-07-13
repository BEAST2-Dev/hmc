---
layout: site
title: BEAST 2 Help Me Choose Subtree slide operator
tags: []
---

## Subtree slide operator

Moves the height of an internal node along the branch. 
If it moves up, it can exceed the root and become a new root. 
If it moves down, it may need to make a choice which branch to slide down into.


## `size` (Double): 

Size of the slide, default 1.0 (optional, default: 1.0).
Bigger sizes result in bolder moves, but higher chance of rejection.
Smaller size may result in fewer topology changes and the proposals just move the node height of an internal node.

The size is automatically adjusted during MCMC when `optimise` is true.

## `kernelDistribution` (KernelDistribution)

Provides sample distribution for proposals (optional, default: bactrian). 
See also [kernel distributions](../BactrianDistribution/).

## `optimise` (Boolean)

Flag to indicate that the size is automatically changed in order to achieve a good acceptance rate (default true).

## `limit` (Double)

Limit on step size, default disable, i.e. -1. (when positive, gets multiplied by tree-height/log2(n-taxa). (optional, default: -1.0)

## `markclades` (Boolean): 

Mark all ancestors of nodes changed by the operator as changed, up to the MRCA of all nodes changed by the operator (optional, default: false).

## `weight` (Double): 

Weight with which this operator is selected (required).
The weight is usually set relatively high.
See also [operator weight tuning](../OperatorWeights/) 


