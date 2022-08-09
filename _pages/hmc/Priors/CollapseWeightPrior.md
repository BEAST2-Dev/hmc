---
layout: site
title: BEAST 2 Help Me Choose collapse weight rate prior
tags: []
---

## Collapse weight prior 

In species delimitation, the collapse weight 0<&omega;<1 is the proportion of taxa which which are to be clustered with other taxa into species. If there are N taxa, there are expected to be (1-&omega;)N species. Thus, lower values of &omega; are associated with splitting, while higher values of &omega; are associated with lumping. 




## Step 1: Estimate mean

First, we estimate the expected number of species m in the dataset. There are numerous definitions of what can constitute a species, including morphological differentiation and reproductive isolation. In this model, we are considering the coalescent concept, however other concepts may be used  to inform this prior, including the morphology of the organisms, the number of populations sampled from, and any known reproductive patterns within/between the populations. The expected (mean) value of &omega; is thus 1 - m/N. 

If there is no available information on m, then skip to Step 3.

**Running example:** Suppose there are N=20 taxa. 19 were sampled from four distinct populations, where each population is characterised by one or more distinct morphological traits. The final taxon is an outgroup. Thus, we would expect an average of m=5 species, and thus our expected value of &omega; is 0.75. 


## Step 2: Estimate uncertainty

Next, we estimate the lower m1, and upper m2, limits for how many species are expected to exist in the samples. m1 and m2 can constitute the 95% HPD interval and should be centered around the estimate of the mean m.  Just like m, m1 and m2 can be informed by morphological, reproductive, geographical, or genomic information.

There is great debate around *lumping* versus *splitting*, and whether it is preferred to be more conservative while delimiting species  (i.e. by lumping when faced with uncertainty), or whether it is preferred to be conservative while clustering individuals into a species (i.e. by splitting when faced with uncertainty). Thus, m1 and m2 can be further adjusted by accounting for which philosophy we prefer in this context. A lumping approach can be achieved by lowering m1 and/or m2, while a splitting approach is achieved by further increasing m1 and/or m2.

The lower and upper limits of the collapse weight &omega;1 and &omega;2 can be calculated as  1 - m2/N and  1 - m1/N, respectively.



**Running example:** In this research context, we wish the delimitation to be conservative, so we will adjust m1 accordingly. Three of the populations are geographically close, and we suspect there could be migration between the three populations. Thus, we believe there could be as few as 3 species, but set m1=2 to be conservative. One of the four populations has a great amount of phenotypical diversity and we suspect there could potentially be three-to-four different species within the population in our sample. Thus, we set m2=8.  Therefore, we will estimate &omega;1=0.6  and &omega;2=0.9.

## Step 3: use the uncertainty to parameterise a distribution

A Beta(&alpha;, &beta;) prior distribution is appropriate for this parameter because it is bound between 0 and 1, and can adopt a range of different shapes. The expected value of this distribution is &alpha;/(&alpha; + &beta;).

**Case 1: &omega;1 and &omega;2 were informed using the steps above**
Use &omega;1 and &omega;2  to inform the 95% HPD of the beta distribution. This can be achieved using R. See [blog post](https://www.beast2.org/2017/05/05/using-r-to-estimate-probability-distribution-parameters-using-quantiles-or-hpd-intervals.html).

**Case 2: No information on number of species, no preference between lumping or splitting**
A Beta(1,1) distribution should suffice. This is equivalent to Uniform(0,1).

**Case 3: No information on number of species, preference towards lumping**
A Beta(&alpha;,1) distribution may be appropriate, where &alpha;>1. This is the default prior in BEAUti, where &alpha;=3.

**Case 4: No information on number of species, preference towards splitting**
A Beta(1,&beta;) distribution may be appropriate, where &beta;>1. 




## References
Carstens, Bryan C., et al. "How to fail at species delimitation." _Molecular ecology_ 22.17 (2013): 4369-4383. [https://doi.org/10.1111/mec.12413](https://doi.org/10.1111/mec.12413)

Jones, Graham, Zeynep Aydin, and Bengt Oxelman. "DISSECT: an assignment-free Bayesian discovery method for species delimitation under the multispecies coalescent." _Bioinformatics_ 31.7 (2015): 991-998. [https://doi.org/10.1093/bioinformatics/btu770](https://doi.org/10.1093/bioinformatics/btu770)

Jones, G. Algorithmic improvements to species delimitation and phylogeny estimation under the multispecies coalescent. _J. Math. Biol._ **74,** 447–467 (2017). https://doi.org/10.1007/s00285-016-1034-0

Douglas, J., Bouckaert, R. Quantitatively defining species boundaries with more efficiency and more biological realism. _Commun Biol_ **5,** 755 (2022). [https://doi.org/10.1038/s42003-022-03723-z](https://doi.org/10.1038/s42003-022-03723-z)


