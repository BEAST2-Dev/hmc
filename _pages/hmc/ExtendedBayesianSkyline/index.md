---
layout: site
title: BEAST 2 Help Me Choose Extended Bayesian skyline
tags: []
---

## Extended Bayesian skyline

Calculates the probability of a beast.tree conditional on a population size function that is split into epochs, where the number of epochs is sampled. 
Note that this does not take the number of possible tree interval/tree topology combinations in account, in other words, the constant required for making this a proper distribution that integrates to unity is not calculated (partly, because we don't know how for sequentially sampled data).
