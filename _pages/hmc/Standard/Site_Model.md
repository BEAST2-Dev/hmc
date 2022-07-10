---
layout: site
title: BEAST 2 Help Me Choose Standard template -- site model panel
tags: []
---

## Standard template -- site model panel

The choice of site model depends on the data type in the alignment.

## Nucleotide & Amino acid data

If you do not want to choose, for some data types site models that perform Bayesian model averaging is available: [bModelTest](https://github.com/BEAST2-Dev/bModelTest) (Bouckaert & Drummond, 2017) for nucleotide data and [OBAMA](https://github.com/rbouckaert/obama/) (Bouckaert, 2020) for amino acid data.
With these site models, you can set and forget and move on to the next panel in BEAUti.
During MCMC, the state jumps between various reversible substitution models, with and without gamma rate heterogeneity, with and without proportion invariable, and between equal and estimated frequencies.
An extra benefit of model averaging is that model uncertainty is included in the posterior, where fixing the model may contribute to reduced uncertainty, thus making the posterior look more confident than it should.

Note this assumes you are interested using reversible substitution models. 
For other models, use the default site model.

## Other data

For data other than nucleotide or amino acid alignments use the default site model.

## References

Bouckaert RR. OBAMA: OBAMA for Bayesian amino-acid model averaging. PeerJ. 2020 Aug 4;8:e9460. <a href="http://doi.org/10.7717/peerj.9460">doi:10.7717/peerj.9460</a>.

Bouckaert RR, Drummond AJ. bModelTest: Bayesian phylogenetic site model averaging and model comparison. BMC evolutionary biology. 2017 Dec;17(1):1-1. <a href="http://doi.org/10.1186/s12862-017-0890-6">doi:10.1186/s12862-017-0890-6</a>.


