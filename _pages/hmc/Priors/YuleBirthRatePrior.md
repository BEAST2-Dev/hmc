---
layout: site
title: BEAST 2 Help Me Choose Yule birth rate prior
tags: []
---

## Yule birth rate prior

The birth rate prior is the prior on the birth rate of the Yule tree prior. 
Here is a three step recipe to specify a prior on the birth rate.

## Step 1: Estimate mean

To determine a prior, first we determine the expected root height \\(t\\). This can be a very rough estimate -- a ball park figure within an order of magnitude will do. For example, if there are no time calibrations and the tree is in units of substitutions, we do not expect the tree to be much over 1 or under 0.01, so \\(t=0.5\\) would do. If there is some prior knowledge about the mutation rate from the literature, say \\(c\\), then the tree will probably not much over \\(1/c\\) or below \\(0.01/c\\) so \\(0.5/c\\) might do as crude estimate.

Let \\(\lambda\\) be the birth rate and we have \\(n\\) taxa, then the maximum likelihood estimate of \\(\lambda\\) given \\(n\\) and \\(t\\) is (Magallon & Sanderson, 2001, Steel & Mooers, 2010, Eq (9)):

$$ \lambda = ln(n/2)/t $$

which we can use as a mean of the prior on \\(\lambda\\).

## Step 2: Estimate uncertainty

Since the birth rate \\(\lambda\\) is a rate parameter, uncertainty is expressed in relative values (not absolute values). 
If one is *very* uncertain about the mean rate from Step 1 because the rate is based on distantly related species or genes, two orders of magnitude difference seems reasonable, that is, for a mean of 1 one would get a 95% HPD of 0.01 to 100.
If the mean is based on closely related genes and species, a 95% HPD that allows an order of magnitude difference in the rate seems appropriate if there is no further information.
If more information is available the 95% HPD could be reduced even further.

## Step 3: use mean and 95% HPD from Step 1 & 2 to parameterise a distribution

Choose a parametric distribution to specify the prior.
Since it is a rate, the distribution should be non-negative, e.g. a log-normal or (inverse) gamma distributions are appropriate.
Since birth rate cannot be 0, it makes sense to use a distribution that has density of 0 at 0, like the log-normal density is for any value of its parameters, while the (inverse) gamma allows a non-zero density for some value of its parameters.
I am not aware of any reason to choose one over the other for birth rate priors, so it is personal preference on which distribution to choose.

BEAUti shows the mean and 95% HPD of the distributions below the density graph, and updates them when updating paramaters of the distribution.
Use the mean and 95% HPD obtained from Step 1 & 2 to parameterise the chosen distribution so that the mean of Step 1 and the 95% HPD of Step 2 match with that of the distribution. 

Note that with the log-normal distribution \\(S=1.175\\) gives a range of two orders of magnitude, and with \\(S=2.35\\) it gives a range of four orders of magnitude. 
The median is in the middle of the range in logspace, e.g. with \\(M=-6.906,S=1.175\\), the 95% HPD range is 1e-4 to 1e-2 with median 1e-3. 
With \\(S=2.35\\) the range changes to 1e-5 to 1e-1, but the median remains at 1e-3.




## Alternative: specify root age prior.

Since the birth rate and root age are linked through the Yule prior, setting a prior on the root age can keep the birth rate in check, even with improper priors.
See [root age prior](../RootAgePrior/) for details.


## References

Magallon S, Sanderson MJ. Absolute diversification rates in angiosperm clades. Evolution. 2001 Sep;55(9):1762-80. <a href="http://doi.org/10.1111/j.0014-3820.2001.tb00826.x">doi:10.1111/j.0014-3820.2001.tb00826.x</a>.

Steel M, Mooers A. The expected length of pendant and interior edges of a Yule tree. Applied Mathematics Letters. 2010 Nov 1;23(11):1315-9. <a href="https://doi.org/10.1016/j.aml.2010.06.021">doi:10.1016/j.aml.2010.06.021</a>.