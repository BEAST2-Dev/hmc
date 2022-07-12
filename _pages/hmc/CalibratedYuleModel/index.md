---
layout: site
title: BEAST 2 Help Me Choose Calibrated Yule model
tags: []
---

## Calibrated Yule model

Yule prior with calibrated monophyletic clades (Heled & Drummond, 2012) that compensates for the interaction of the Yule process and clade calibrations. 
With this prior, the marginal distribution of the calibrated nodes (the MRCA of clades) is identical to the specified calibration, but the Yule is not preserved over the whole tree space, only among sub-spaces.

This works well when there are only a small number of calibrations, but becomes computationally expensive when there are many of them. 
If you want to use many calibrations, it may be better to use the Yule model, which is uncalibrated.
Make sure to sample from the prior in order to understand how calibrations and Yule model interact.

## Parameters

It has a single parameter, the birth rate, which is usually estimated and requires a [hyper prior](../../Priors/YuleBirthRatePrior/).

## Tip dates

The model assumes all tips are sampled at the same time (i.e. no tip dates).
If you have tip dates, consider a birth death sampling prior or coalescent tree prior instead.

## References

Heled J, Drummond AJ. Calibrated tree priors for relaxed phylogenetics and divergence time estimation. Systematic biology. 2012 Jan 1;61(1):138-49. <a href="https://doi.org/10.1093/sysbio/syr087">doi:10.1093/sysbio/syr087</a>.
