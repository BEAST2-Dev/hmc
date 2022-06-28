---
layout: site
title: BEAST 2 Help Me Choose Relaxed Clock -- number of discrete rates
tags: []
---

## Relaxed Clock -- number of discrete rates

This entry represents the number of discrete rates to approximate the rate distribution by in the uncorrelated relaxed clock (Drummond et al, 2006). 
A negative value will cause the number of categories to be set equal to the number of branches in the tree. 
With a small number of branches, this default number of rates may result in a poor approximation of the rate distribution (cite?).
This problem can be circumvented by setting the number of discrete rates high enough, where 100 seems sufficiently large.

Note this is an issue with the uncorrelated relaxed clock implementation using a discretised rate distribution only. 
The [optimised relaxed clock](https://github.com/jordandouglas/ORC) (ORC) (Douglas et al, 2021) is an implementation using real valued rates, which benefits from more efficient operators making inference more efficient, which you can use as alternative.


## References

Douglas J, Zhang R, Bouckaert R. Adaptive dating and fast proposals: Revisiting the phylogenetic relaxed clock model. PLoS computational biology. 2021 Feb 2;17(2):e1008322. <a href="https://doi.org/10.1371/journal.pcbi.1008322">doi:10.1371/journal.pcbi.1008322</a>.

Drummond AJ, Ho SY, Phillips MJ, Rambaut A. Relaxed phylogenetics and dating with confidence. PLoS biology. 2006 May;4(5):e88. <a href="https://doi.org/10.1371/journal.pbio.0040088">doi:10.1371/journal.pbio.0040088</a>