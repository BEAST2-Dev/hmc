---
layout: site
title: BEAST 2 Help Me Choose Markov chained pop sizes -- reverse
tags: []
---

## Markov chained pop sizes -- reverse

Interpret the parameter in reverse.
Instead of chaining dimension //(i//) to //(i-1//), chain dimension to //(i+1//).
If the `isJeffreys` flag is set, it is applied to the last dimension instead of the first.
Not recommended for Bayesian skyline, since post-processing in Tracer assumes reverse=false.