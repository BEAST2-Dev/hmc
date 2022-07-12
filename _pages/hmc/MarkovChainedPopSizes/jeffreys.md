---
layout: site
title: BEAST 2 Help Me Choose Markov chained pop sizes -- jeffreys
tags: []
---

## Markov chained pop sizes -- jeffreys

Use Jeffrey's prior (1/X prior) on the first parameter of the chain linked parameters.
If false, a uniform \\((0,\infty)\\) is used instead.
Note that both priors are not proper priors, and sampling from the prior or path or nested sampling may fail.
Possible solutions to keep the population sizes for the Bayesian skyline inside a reasonable range:

* specify the initial mean: if specified, this first entry will be linked by a Gamma with mean with that value,
* add bounds on the population size parameter, 
* or add a vague root age prior.