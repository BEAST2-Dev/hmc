---
layout: site
title: BEAST 2 Help Me Choose Standard template priors panel
tags: []
---

## Standard template -- priors panel

Here, we will concentrate on the choice of tree prior. Other priors have their own 'help me choose' information with hints specific to these priors that you can find by clicking the little question mark button next to the prior.

## Interest in some parameter of interest i.e. tree prior is not a nuisance parameter

If you are interested in some parameter that is estimated through a tree prior, e.g. diversification rate through time in the [Yule skyline model]() (Bouckaert, 2022), or reproductive number, this possibly narrows down the available choice in tree priors to just 1.
Be aware of the limitations and applicability of the model.

## Tree prior is a nuisance parameter -- Coalescent vs birth/death prior

Tree priors roughly can be classified as either coalescent based models and birth/death based models (uniform tree priors are [frowned upon](http://www.beast2.org/2021/05/31/uniform-tree-prior.html), so will be ignored).
Coalescent based models assume a small sample from a well mixing population, or at least well mixing within demes, and tend to be appropriate for samples from closely related species or within a species.
Birth/death models tend to be more appropriate for samples from different species.

However, both coalescent and birth death priors have flexible variants that can accommodate any tree, e.g. [BICEPS](https://github.com/rbouckaert/biceps) (Bouckaert, 2022) and Bayesian skyline (Drummund et al, 2005) for coalescent and [BDSKY](https://github.com/BEAST2-Dev/bdsky/) (Stadler et al, 2012) for birth/death priors.
So, if your sample is a mixture of samples from a species and quite different species, one of these can be appropriate.
Birth/death models usually have more parameters, potentially highly correlated, so require more mental effort for specifying priors than coalescent models.

```
Note: outgroups are not necessary for rooting a tree when infering rooted time trees in BEAST. 
So, in a sample from one species + outgroup, the outgroup can be removed.
```

## Parametric vs non-parametric

Some tree priors assume a population size history or diversification rate history that can be described by a function parameterised by various parameters. 
For example the coalescent with constant population, coalescent with exponential growth, and Yule prior.
Use these simple priors if you are exploring the data, or have some information how the data behaves, e.g exponential growth of the start of a viral outbreak.

Other tree priors do not assume a pre-defined trajectory, but split time into epochs, and usually assume a constant parameter in the epoch, but allow changes between epochs, for example, BICESP, Bayesian skyline, BDSKY, Yule skyline.
These priors allow a wider range of tree shapes and sizes than parametric models, so are more appropriate if there is no other information or there is interest in population or diversification history.

## Contemporary vs sampled through time

Some priors, notably (calibrated) Yule, simple birth/death and Yule skyline assume all samples are taken at the same time.
If your sample contains samples taken at different times, these priors are not appropriate, and though it is possible to run BEAST with them, be aware that assumptions of these priors are violated, so the tree generating process is not well defined.

All coalescent priors can handle dated tips, so a flexible non-parametric tree prior like BICEPS or Bayesian skyline can be considered.

## Calibrated vs uncalibrated

Node calibrations are priors on the height of internal nodes.
These usually interfere with the tree prior in unpredictable ways, and it is often necessary to sample from the prior to see the effect.
For the Yule prior with a small number of node calibrations, the interaction can be compensated for using the calibrated Yule prior (Heled & Drummond, 2012).

If node calibrations are based on fossils, you can consider the [CladeAge](https://github.com/BEAST2-Dev/cladeage) package (Matschiner et al, 2017), which allow node priors to be specified according to information about the fossil discovery process.
If the fossil discovery process can be assumed to be homogeneous for all fossils in the analysis, consider the [sampled ancestors](https://github.com/CompEvol/sampled-ancestors) package (Gavryushkina et al, 2014).
This allows nodes representing fossil findings to be ancestral to current day samples.

## Structured vs unstructured

When the sample is taken from demes where they are relatively isolated, a structured tree prior is more appropriate.

[MultyTypeTree](https://tgvaughan.github.io/MultiTypeTree/) (Vaughan et al, 2014) implements the structured coalescent. 
It has deteriorating performance with more than 4 demes.
[MASCOT](https://github.com/nicfel/Mascot) (Müller et al, 2018) provides a structured coalescent approximation that is computationally efficient, and where population size and migration rates can be informed by a generalised linear model (Yang et al, 2019).

[BDMM](https://github.com/denisekuehnert/bdmm) (Kühnert et al, 2016) provides a structured birth death model.

Note that both MASCOT and BDMM are sensitive to priors on migration rates and other parameters, so care must be taken in providing well thought out priors.



## References

Bouckaert RR. An Efficient Coalescent Epoch Model for Bayesian Phylogenetic Inference, Systematic Biology, syac015, 2022 <a href="https://doi.org/10.1093/sysbio/syac015">doi:10.1093/sysbio/syac015</a>.

Drummond AJ, Rambaut A, Shapiro BE, Pybus OG. Bayesian coalescent inference of past population dynamics from molecular sequences, Molecular Biology and Evolution. 22(5):1185-92, 2005. <a href="http://doi.org/10.1093/molbev/msi103">doi:10.1093/molbev/msi103</a>.

Gavryushkina A, Welch D, Stadler T, Drummond AJ. Bayesian inference of sampled ancestor trees for epidemiology and fossil calibration. PLoS computational biology. 2014 Dec 4;10(12):e1003919. <a href="https://doi.org/10.1371/journal.pcbi.1003919">doi:10.1371/journal.pcbi.1003919</a>.

Heled J, Drummond AJ. Calibrated tree priors for relaxed phylogenetics and divergence time estimation. Systematic biology. 2012 Jan 1;61(1):138-49. <a href="https://doi.org/10.1093/sysbio/syr087">doi:10.1093/sysbio/syr087</a>.

Kühnert D, Stadler T, Vaughan TG, Drummond AJ. Phylodynamics with migration: a computational framework to quantify population structure from genomic data. Molecular biology and evolution. 2016 Apr 9;33(8):2102-16. <a href="https://doi.org/10.1093/molbev/msw064">doi:10.1093/molbev/msw064</a>.

Matschiner M, Musilová Z, Barth JM, Starostová Z, Salzburger W, Steel M, Bouckaert R. Bayesian phylogenetic estimation of clade ages supports trans-Atlantic dispersal of cichlid fishes. Systematic biology. 2017 Jan 1;66(1):3-22. <a href="https://doi.org/10.1093/sysbio/syw076">doi:10.1093/sysbio/syw076</a>.

Müller NF, Rasmussen D, Stadler T. MASCOT: parameter and state inference under the marginal structured coalescent approximation. Bioinformatics. 2018 Nov 15;34(22):3843-8. <a href="http://doi.org/10.1093/bioinformatics/bty406">doi:10.1093/bioinformatics/bty406</a>.

Stadler T, Kühnert D, Bonhoeffer S, Drummond AJ. Birth–death skyline plot reveals temporal changes of epidemic spread in HIV and hepatitis C virus (HCV). Proceedings of the National Academy of Sciences. 2013 Jan 2;110(1):228-33. <a href="https://doi.org/10.1073/pnas.120796511">doi:10.1073/pnas.120796511</a>.

Vaughan TG, Kühnert D, Popinga A, Welch D, Drummond AJ. Efficient Bayesian inference under the structured coalescent. Bioinformatics. 2014 Aug 15;30(16):2272-9. <a href="https://doi.org/10.1093/bioinformatics/btu201">doi:10.1093/bioinformatics/btu201</a>.

Yang J, Müller NF, Bouckaert R, Xu B, Drummond AJ. Bayesian phylodynamics of avian influenza A virus H9N2 in Asia with time-dependent predictors of migration. PLoS computational biology. 2019 Aug 6;15(8):e1007189. <a href="https://doi.org/10.1371/journal.pcbi.1007189">doi:10.1371/journal.pcbi.1007189</a>.