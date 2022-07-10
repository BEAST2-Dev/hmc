---
layout: site
title: BEAST 2 Help Me Choose Pop size prior
tags: []
---

## Pop size prior

The population size prior for the population of the coalescent tree prior with constant population.
Note that this is the [effective population size](https://en.wikipedia.org/wiki/Effective_population_size), which can be  significantly smaller than the actual population size (Frankman, 1997).
Knowledge of actual population size can therefore not directly used to inform the prior, but values from the literature could be used for inspiration. 
Alternatively, use the following approach based on expected tree height:

## Step 1

First, estimate a range that the root height can be plausible to be in.
Let \\(t_{low}, t_{hi}\\) be a rough estimate of the 95 % HPD interval for the tree height.
Note that \\(t_{low}\\) and \\(t_{hi}\\) can be orders of magnitude apart if you have no further information.
For example, if there are no time calibrations and the tree is in units of substitutions, we do not expect the tree to be much over 1 or under 0.01, so \\(t_{low}=0.01,t_{hi}=1\\) would do. If there is some prior knowledge about the mutation rate from the literature, say \\(c\\), then the tree will probably not much over \\(1/c\\) or below \\(0.01/c\\).

## Step 2

Next, the population size \\(N\\) and root height \\(t\\) are related as \\((E[t]=2(1-1/N)\\) (Tavaré et al, 1997) so we can use \\(N=1-2/t\\), so by plugging in \\(t_{low}\\) for \\(t\\) gives us \\(N_{low}\\), and likewise plugging in \\(t_{hi}\\) for \\(t\\) gives use \\{N_{hi}\\.
As sanity check, compare these bounds with actual population size and make sure they are in a similar order of magnitude.

## Step 3

Finally, since population sizes are non-zero positive numbers, choose a distribution that has a positive range, like the log-normal or (inverse) gamma distribution.
Fit the 95% HPD to the \\(N_{low}\\) and \\(N_{hi}\\) values obtained above.





## References 

Frankham R. Effective population size/adult population size ratios in wildlife: a review. Genetics Research. 1995 Oct;66(2):95-107. <a href="https://doi.org/10.1017/S0016672300034455">doi:10.1017/S0016672300034455</a>.

Tavaré S, Balding DJ, Griffiths RC, Donnelly P. Inferring coalescence times from DNA sequence data. Genetics. 1997 Feb 1;145(2):505-18. <a href="http://doi.org/10.1093/genetics/145.2.505">doi:10.1093/genetics/145.2.505</a>.