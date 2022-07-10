---
layout: site
title: BEAST 2 Help Me Choose Site model subst model
tags: []
---

## Site model subst model

This entry of the site model represents the substitution model along branches in the tree.
For initial exploratory analyses, the HKY model for nucleotide data, or WAG for amino acid data can be considered.

A common practice is to run maximum likelihood based model selection model to inform the substitution model. 
These methods assume a particular tree potentially biasing the analysis, causes double usage of the data (once with maximum likelihood, one with Bayesian analysis), and fixing the substitution model does not take model uncertainty in account potentially underestimating uncertainty in parameter estimates.

## Nucleotide & Amino acid data

If you do not want to choose, for some data types site models that perform Bayesian model averaging is available: [bModelTest](https://github.com/BEAST2-Dev/bModelTest) (Bouckaert & Drummond, 2017) for nucleotide data and [OBAMA](https://github.com/rbouckaert/obama/) (Bouckaert, 2020) for amino acid data.
With these *site models*, you can set and forget and move on to the next panel in BEAUti.
During MCMC, the state jumps between various reversible substitution models as well as, with and without gamma rate heterogeneity, with and without proportion invariable, and between equal and estimated frequencies.


## Nucleotide model not available?

If you insist on using a fixed model suggested by a pre-analysis, it can happen that the model is not available. 
For nucleotide models, the [SSM](https://github.com/BEAST2-Dev/substmodels/) package provides a set of named models.
If the model is still not there, choose the GTR model and click on menu `Mode => Allow parameter linking`.
Next to the GTR parameters a link button appears that allows you to create any reversible model by linking one or more rate parameters.


## Other data

For data other than nucleotide or amino acid alignments use one of the models compatible with your data.
Model selection methods like path sampling or nested sampling (Maturana et al, 2019) can be used to select one of these models.


## References

Bouckaert RR. OBAMA: OBAMA for Bayesian amino-acid model averaging. PeerJ. 2020 Aug 4;8:e9460. <a href="http://doi.org/10.7717/peerj.9460">doi:10.7717/peerj.9460</a>.

Bouckaert RR, Drummond AJ. bModelTest: Bayesian phylogenetic site model averaging and model comparison. BMC evolutionary biology. 2017 Dec;17(1):1-1. <a href="http://doi.org/10.1186/s12862-017-0890-6">doi:10.1186/s12862-017-0890-6</a>.

Maturana PM, Brewer BJ, Klaere S, Bouckaert RR. Model selection and parameter inference in phylogenetics using Nested Sampling. Systematic biology. 2019 Mar 1;68(2):219-33. <a href="https://doi.org/10.1093/sysbio/syy050">doi:10.1093/sysbio/syy050</a>.
