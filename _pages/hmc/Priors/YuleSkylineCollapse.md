---
layout: site
title: BEAST 2 Help Me Choose Yule-skyline collapse tree prior
tags: []
---

##  Yule-skyline collapse tree prior

The Yule-skyline collapse model is a pure-birth model which is used for identifying boundaries between species (species delimitation) and assumes all tips were sampled at the same time. 

Under the Yule skyline model, each epoch is associated with a birth rate. The birth rate of each epoch is sampled from a Gamma(&alpha; &beta;) distribution where &alpha; is the shape and &beta; is the rate.  Also see the [Yule sklyline blog](https://www.beast2.org/2022/06/01/yule-skyline-tree-prior.html).

Under the collapse model, taxa whose divergence time falls below time &epsilon; are clustered into a single species (Jones et al. 2015 and 2017).

These two tree priors are combined into the Yule-skyline collapse (YSC) model, overviewed in a [previous post](https://www.beast2.org/2022/08/01/speedemon.html).


## Collapse threshold  &epsilon;
The threshold &epsilon; describes the maximum amount of divergence that can be tolerated before two samples are considered to be different species. &epsilon; is expressed in the same units as the tree height. We recommend the user performs a sensitivity analysis to this term by running multiple MCMC replicates, each with a different value of &epsilon;. A guide for performing this exercise can be found in [Douglas and Bouckaert 2022](https://doi.org/10.1038/s42003-022-03723-z).

## Collapse weight  &omega;

The collapse weight 0<&omega;<1 is approximately the proportion of lineages which are clustered into species. The [collapse weight prior](https://beast2-dev.github.io/hmc/hmc//Priors/CollapseWeightPrior/) guide contains further details on this parameter.




## Birth rate shape &alpha;

The shape of the Gamma distribution is related to how peaked or modal the distribution of birth rates is. This defaults to 2. 

## Birth rate *rate* &beta;

The rate of the Gamma distribution is inversely related to the mean birth rate, which is inversely related to the expected tree height and length. The [birth rate rate](https://beast2-dev.github.io/hmc/hmc//Priors/BirthRateRatePrior/) guide contains further details on this parameter.


## Equal epochs

If `Equal Epochs` is false, the model uses birth rate epochs based on ~equally sized groups of lineages, otherwise it uses equal sized epochs that scale with the tree height. 

## Linked means

If `Linked Mean` is true, the model uses birth rate *rate* only for first epoch, and for other epochs uses the posterior mean of the previous epoch. This makes the Yule skyline prior behave like a smoothing prior, which emulates the biologically plausible assumption that birth rates in consecutive epochs are related. If false, each epoch is assumed independently drawn from the same Gamma distribution.

## References


Douglas, J., Bouckaert, R. Quantitatively defining species boundaries with more efficiency and more biological realism. _Commun Biol_ **5,** 755 (2022). [https://doi.org/10.1038/s42003-022-03723-z](https://doi.org/10.1038/s42003-022-03723-z)

Remco R Bouckaert. An efficient coalescent epoch model for Bayesian phylogenetic inference. Sys Bio, syac015, 2022 [doi:10.1093/sysbio/syac015](https://doi.org/10.1093/sysbio/syac015)

Jones, Graham, Zeynep Aydin, and Bengt Oxelman. "DISSECT: an assignment-free Bayesian discovery method for species delimitation under the multispecies coalescent." _Bioinformatics_ 31.7 (2015): 991-998. [https://doi.org/10.1093/bioinformatics/btu770](https://doi.org/10.1093/bioinformatics/btu770)

Jones, G. Algorithmic improvements to species delimitation and phylogeny estimation under the multispecies coalescent. _J. Math. Biol._ **74,** 447–467 (2017). https://doi.org/10.1007/s00285-016-1034-0


