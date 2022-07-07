---
layout: site
title: BEAST 2 Help Me Choose Exchange operator
tags: []
---

## Exchange operator

Implements branch exchange operations. 
There is a NARROW and WIDE variety. 
The narrow exchange is very similar to a rooted-beast.tree nearest-neighbour interchange but with the restriction that node height must remain consistent.

## `isNarrow` (Boolean)

If true (default) a narrow exchange is performed, otherwise a wide exchange.

## `markclades` (Boolean) 

Mark all ancestors of nodes changed by the operator as changed, up to the MRCA of all nodes changed by the operator (optional, default: false).
This option is used when a Pruned Tree ([BEASTLabs](https://github.com/BEAST2-Dev/BEASTLabs)) is included in the analyses, and can be left false for Standard template analyses.

## `weight` (Double)

Weight with which this operator is selected (required).
See also [operator weight tuning](/hmc/Operators/OperatorWeights/) 

For narrow exchange, the weight is usually set relatively high, where it proposes only local changes to the tree.

Wide exchange is useful during burn-in, but later on during MCMC tends to have low acceptance rate, so the weight is usually set low.



