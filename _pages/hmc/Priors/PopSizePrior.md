---
layout: site
title: BEAST 2 Help Me Choose Pop size prior
tags: []
---

## Pop size prior

The population size prior for the population of the coalescent tree prior with constant population.
Note that this is the [effective population size](https://en.wikipedia.org/wiki/Effective_population_size), which can be  significantly smaller than the actual population size (Frankman, 1997).
Especially in the case of viruses, there can be many order of magnitude difference.
Knowledge of actual population size can therefore not directly used to inform the prior, though values from the literature could be used for inspiration. 


## Option 1: Inferring prior from tree age estimate

Use the following approach based on expected tree height:

### Step 1

First, estimate a range that the root height can be plausible to be in.
Let \\(t_{low}, t_{hi}\\) be a rough estimate of the 95 % HPD interval for the tree height.
Note that \\(t_{low}\\) and \\(t_{hi}\\) can be orders of magnitude apart if you have no further information.
For example, if there are no time calibrations and the tree is in units of substitutions, we do not expect the tree to be much over 1 or under 0.01, so \\(t_{low}=0.01,t_{hi}=1\\) would do. If there is some prior knowledge about the mutation rate from the literature, say \\(c\\), then the tree will probably not much over \\(1/c\\) or below \\(0.01/c\\).

### Step 2

Next, the population size \\(N\\) and root height \\(t\\) are related as \\((E[t]=2(1-1/N)\\) (Tavaré et al, 1997) so we can use \\(N=1-2/t\\), so by plugging in \\(t_{low}\\) for \\(t\\) gives us \\(N_{low}\\), and likewise plugging in \\(t_{hi}\\) for \\(t\\) gives use \\{N_{hi}\\.
As sanity check, compare these bounds with actual population size and make sure they are in a similar order of magnitude.

### Step 3

Finally, since population sizes are non-zero positive numbers, choose a distribution that has a positive range, like the log-normal or (inverse) gamma distribution.
Fit the 95% HPD to the \\(N_{low}\\) and \\(N_{hi}\\) values obtained above.


## Option 2: Add prior on root age

Instead of indirectly determining the population size prior, the population size can be left with a uniform \\([0,\infinity]\\) prior, and an MRCA prior can be added to the root age.
Though this leaves an improper prior on the population size, the population size is linked to the root age by the coalescent prior, so it is not a parameter that can vary independently.

A root age prior can be added in the priors panel by clicking the `+ Add priors` button at the bottom.
In the dialog that pops up, select all taxa (click first taxon, use keys Ctrl-A or Cmd-A to select the rest) and add `root` for the label.
Click the `OK` button, and a new entry with label `root.prior` appears in the list of priors.
Select a parametric distribution in the drop-down box with distributions, and parameterise according to your prior.

```
Note: if clock prior is added when a root age distribution is selected this may indicate there is no other timing information that can inform the clock rate and the analysis will struggle to converge if the root age prior is quite wide.

If there is not strong timinig information, the mean clock rate of the clock model should not be estimated: uncheck the estimate box in the clock model panel -- you may need to uncheck via menu `Mode => Automatic set clock rate` to enable the estimate box.
```


## References 

Frankham R. Effective population size/adult population size ratios in wildlife: a review. Genetics Research. 1995 Oct;66(2):95-107. <a href="https://doi.org/10.1017/S0016672300034455">doi:10.1017/S0016672300034455</a>.

Tavaré S, Balding DJ, Griffiths RC, Donnelly P. Inferring coalescence times from DNA sequence data. Genetics. 1997 Feb 1;145(2):505-18. <a href="http://doi.org/10.1093/genetics/145.2.505">doi:10.1093/genetics/145.2.505</a>.