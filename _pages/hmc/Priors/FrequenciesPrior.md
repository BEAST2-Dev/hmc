---
layout: site
title: BEAST 2 Help Me Choose Frequencies prior
tags: []
---

## Frequencies prior

This is the prior on base frequencies for reversible nucleotide substitution models. 
Frequencies have to be in the range 0 to 1, and there is an extra constraint: the sum over all frequencies has to be 1.
Usually, there is a sufficiently strong signal in alignment data for the prior on this parameter to be inconsequential.

A uniform [0,1] prior could be suitable, but in practice we know that it rarely happens that frequencies are very close to zero.
A Dirichlet(4,4,4,4) prior still allows for a wide range of frequency values, but discourages values close to zero.
This prior also performs well in well calibrated simulation studies (Bouckaert & Drummond, 2017).

## References

Bouckaert RR, Drummond AJ. bModelTest: Bayesian phylogenetic site model averaging and model comparison. BMC evolutionary biology. 2017 Dec;17(1):1-1. <a href="http://doi.org/10.1186/s12862-017-0890-6">doi:10.1186/s12862-017-0890-6</a>.
