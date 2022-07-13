---
layout: site
title: BEAST 2 Help Me Choose Birth rate prior
tags: []
---

## Birth rate prior 

The birth rate prior is the prior on the effective birth rate of the birth-death tree prior.
Let \\(\lambda\\) be the birth rate, and \\(\mu\\) be the death rate of the model then  \\(r = \lambda - \mu\\). 
There is no closed form formula for the relation between \\(r\\) and expected tree height \\(t\\) as far as I am aware, but I expect it not to be too far away from that of the Yule process, which equals the birth death model with \\(\mu=0\\).

## Step 1: Estimate mean \\(r\\)

First, we determine the expected root height \\(t\\). 
This can be a very rough estimate -- a ball park figure within an order of magnitude will do. For example, if there are no time calibrations and the tree is in units of substitutions, we do not expect the tree to be much over 1 or under 0.01, so \\(t=0.5\\) would do. If there is some prior knowledge about the mutation rate from the literature, say \\(c\\), then the tree will probably not much over \\(1/c\\) or below \\(0.01/c\\) so \\(0.5/c\\) might do as crude estimate.

For the Yule model, the maximum likelihood estimate of \\(\lambda\\) given he number of taxa \\(n\\) and root height estimate \\(t\\) is (Magallon & Sanderson, 2001, Steel & Mooers, 2010, Eq (9)):

$$ \lambda = ln(n/2)/t $$

so we can use this as guide for the mean of \\(r\\).

## Step 2: Estimate uncertainty in \\(r\\)

## Step 3: Use mean and 95% HPD from Step 1 & 2 to parameterise a distribution

See [Step 2 & 3](../YuleBirthRatePrior/) for the Yule birth rate prior on how do this.


## References

Magallon S, Sanderson MJ. Absolute diversification rates in angiosperm clades. Evolution. 2001 Sep;55(9):1762-80. <a href="http://doi.org/10.1111/j.0014-3820.2001.tb00826.x">doi:10.1111/j.0014-3820.2001.tb00826.x</a>.

Steel M, Mooers A. The expected length of pendant and interior edges of a Yule tree. Applied Mathematics Letters. 2010 Nov 1;23(11):1315-9. <a href="https://doi.org/10.1016/j.aml.2010.06.021">doi:10.1016/j.aml.2010.06.021</a>.