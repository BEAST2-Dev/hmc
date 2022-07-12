---
layout: site
title: BEAST 2 Help Me Choose Markov chained pop sizes -- parameter
tags: []
---

## Markov chained pop sizes -- parameter

Chain parameter to calculate distribution over.
The value of a parameter is assumed to be Gamma distributed with mean as the previous value in the parameter, or log normal if the `useLogNormal` flag is set to true.
For the Bayesian skyline, these are the population sizes for the consecutive groups going backward in time.
