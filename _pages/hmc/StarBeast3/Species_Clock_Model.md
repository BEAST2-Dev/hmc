---
layout: site
title: BEAST 2 Help Me Choose Standard template -- species clock model panel
tags: []
---

## StarBeast3 template -- species clock model panel

Here, we will consider the strict clock and the multispecies coalescent relaxed clock (Ogilvie at el. 2017). 


## Initial exploration

For an initial run when no experience with the type of data is available, running with the strict clock and simple substitution model and tree prior is a good way to find out whether there is signal in the data.

A relaxed clock analysis can then be added if there are a good number of mutations in the data and a reasonable number of taxa. 
If the distribution of the coefficient of variation is hugging zero, this is a signal that there is little rate variation among branches, and a strict clock is supported by the data.
If this distribution is not touching zero, this is a signal there is rate variation and a relaxed clock is supported by the data.
If you are unsure, you can run a [path sampling](https://github.com/BEAST2-Dev/model-selection) or [nested sampling](https://github.com/BEAST2-Dev/nested-sampling) analysis to perform Bayesian hypothesis testing.



## Estimating the clock rate


By default, the clock rate is fixed at 1. To estimate the clock rate, open `Mode` and uncheck ` Automatic set clock rate`. Then check the `estimate` button of `Clock.rate` in the `Species Clock Model` tab. The clock rate prior distribution should be set in the `Priors` tab using an [informed estimate](https://beast2-dev.github.io/hmc/hmc/Priors/ClockPrior/).


## Relaxed clock model


Under this model, each branch in the species tree is associated with a rate, and these rates are independent and identically drawn from a LogNormal distribution. The mean of this LogNormal distribution is fixed at 1 (to avoid non-identifiability with tree heights and clock rates), while the standard deviation is estimated. In contrast to the relaxed clock model used in a standard concatenated phylogenetic analysis, here, the gene trees inherit their branch substitution rates from the species tree. Thus, even though there could potentially be dozens or hundreds of gene trees, the number of branch substitution rates only grows with the size of the species tree.


When running the relaxed clock model, keep an eye on the estimated lognormal clock standard deviation. If its estimate is quite small (e.g. less than 0.1), then the data are very clock-like, and a strict clock may be adequate. Whereas, if the estimate is quite large (e.g. above 1), this suggests there may be issues with the dataset or the model. Specifically, it may indicate convergence issues, poor signal in the data perhaps due to a bad multiple sequence alignment, it may indicate errors in the taxon mapping, or various other issues.  


## References

Douglas J, Zhang R, Bouckaert R. Adaptive dating and fast proposals: Revisiting the phylogenetic relaxed clock model. PLoS computational biology. 2021 Feb 2;17(2):e1008322. <a href="https://doi.org/10.1371/journal.pcbi.1008322">doi:10.1371/journal.pcbi.1008322</a>.

Ogilvie, Huw A., Remco R. Bouckaert, and Alexei J. Drummond. "StarBEAST2 brings faster species tree inference and accurate estimates of substitution rates." Molecular biology and evolution 34.8 (2017): 2101-2114. <a href="https://doi.org/10.1093/molbev/msx126">doi:10.1093/molbev/msx126</a>.

Douglas, Jordan, Cinthy L. Jiménez-Silva, and Remco Bouckaert. "StarBeast3: Adaptive Parallelized Bayesian Inference under the Multispecies Coalescent." Systematic Biology (2022). <a href="https://doi.org/10.1093/sysbio/syac010">10.1093/sysbio/syac010</a>.
