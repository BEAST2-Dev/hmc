---
layout: site
title: BEAST 2 Help Me Choose Site Model gamma category count
tags: []
---

## Site Model gamma category count

Gamma category count determines the number of categories used when the gamma site heterogeneity model (Yang, 1994) is used. 
Site rate heterogeneity models capture the phenomenon of some sites evolving faster than other sites, e.g., when the alignment consists of coding DNA it is well known that 3rd codon position sites evolve a lot faster than 1st and 2nd codon position sites (an alternative in this case is to split the alignment in partitions by codon position and use a separate relative substitution rate for each of the partitions (Shapiro et al. 2006)).
There are other mechanisms causing rate heterogeneity, like coding dna consisting of a mixture of more and less conserved regions.

The larger the category count, the more rates are used to approximate a gamma distribution. 
However, the computational cost is linear in the category count, so setting it at `n` means `n` times more computation is needed for the tree likelihood, and since the tree likelihood calculation usually dominates the calculation of the posterior, this means the MCMC takes approximately `n` times more computation.

When gamma category count is set to 1 or lower, no gamma rate heterogeneity is used, and all sites use the same rate.
A generally used number of categories is 4 when gamma rate heterogeneity is desired.

When running the gamma rate heterogeneity model, keep an eye out on the estimate of the shape parameter: if it is large (>16) this indicates there is almost no rate heterogeneity in the data, and using the model just wastes computation.


## References

Shapiro B, Rambaut A, Drummond AJ. Choosing appropriate substitution models for the phylogenetic analysis of protein-coding sequences. Molecular biology and evolution. 2006 Jan 1;23(1):7-9. <a href="http://doi.org/10.1093/molbev/msj021">doi:10.1093/molbev/msj021</a>.

Yang Z. Maximum likelihood phylogenetic estimation from DNA sequences with variable rates over sites: approximate methods. Journal of Molecular evolution. 1994 Sep;39(3):306-14. <a href="http://doi.org/10.1007/BF00160154">doi:10.1007/BF00160154</a>.