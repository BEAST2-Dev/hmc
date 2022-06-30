---
layout: site
title: BEAST 2 Help Me Choose WilsonBalding operator
tags: []
---

## WilsonBalding operator

Implements the unweighted Wilson-Balding branch swapping move (Drummond et al, 2002). 
This move is similar to one proposed by WILSON and BALDING 1998  and involves removing a subtree and re-attaching it on a new parent branch. 
See <a href='http://www.genetics.org/cgi/content/full/161/3/1307/F1'>picture</a>.

## `markclades` (Boolean)

Mark all ancestors of nodes changed by the operator as changed, up to the MRCA of all nodes changed by the operator (optional, default: false).
This option is used when a Pruned Tree ([BEASTLabs](https://github.com/BEAST2-Dev/BEASTLabs)) is included in the analyses, and can be left false for Standard template analyses.

## `weight` (Double)

Weight with which this operator is selected (required)

Wilson Balding is useful during burn-in, but later on during MCMC tends to have low acceptance rate, so the weight is usually set low.


## References

Drummond AJ, Nicholls GK, Rodrigo AG, Solomon W. Estimating mutation parameters, population history and genealogy simultaneously from temporally spaced sequence data. Genetics. 2002 Jul 1;161(3):1307-20. <a href="https://doi.org/10.1093/genetics/161.3.1307">doi:/10.1093/genetics/161.3.1307</a>.
