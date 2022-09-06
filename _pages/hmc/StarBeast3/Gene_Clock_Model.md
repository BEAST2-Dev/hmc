---
layout: site
title: BEAST 2 Help Me Choose StarBeast3 template -- gene clock model panel
tags: []
---

## StarBeast3 template -- gene clock model panel


Individual genes can evolve at different rates and gene clock rates can be estimated, to capture their *relative* rate. 
When check boxes are ticked in the table, the gene clock rate will be estimated.

Sensible options are 
* estimate all clock rates
* estimate all clock rates but one

## Estimate all clock rates

When estimating all clock rates, use a prior on each of the clock rate with mean of 1 and a variance that is not very high.
This results in an average rate close to 1, and usually mixes well, though might introduce some small amount of uncertainty.

Note that these are relative rates -- the mean rate of the [species tree clock ](../../StarBeast3/Species_Clock_Model/) determines the overall clock rate.

## Estimate all clock rates but one

In this case, gene clock rates are relative to the locus that does not have its gene clock rate estimated. 
It allows for wider priors on gene clock rates, and slightly reduced uncertainty, but with many loci may lead to worse mixing.


## Switch all estimate boxes on/off

To set all estimate flags at the same time, click the checkbox in the title bar of the table above the other check boxes.


## References

Douglas, J, Jiménez-Silva, CL, Bouckaert, RR. "StarBeast3: Adaptive Parallelized Bayesian Inference under the Multispecies Coalescent." Systematic Biology (2022). <a href="https://doi.org/10.1093/sysbio/syac010">10.1093/sysbio/syac010</a>.


