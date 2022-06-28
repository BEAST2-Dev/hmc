---
layout: site
title: BEAST 2 Help Me Choose random local clock -- rate change prior
tags: []
---

## Random local clock -- rate change prior

This prior is over the number of internal nodes where a rate change takes place in the random local clock (Drummond & Suchard, 2010).
When this is 0, the model behaves like the strict clock, and when it is the number of internal nodes it behaves like a relaxed clock (uncorrelated if `ratesAreMultipliers=false` and correlated if `ratesAreMultipliers=true`).

Usually, you want to encourage a low number of rate changes, so for example a Possion distribution with a low mean as prior would be appropriate.
If the data indicates there are many rate changes, the random local clock will accomodate this if the prior is not too strong.


## References

Drummond AJ, Suchard MA. Bayesian random local clocks, or one rate to rule them all. BMC biology. 2010 Dec;8(1):1-2. <a href="https://doi.org/10.1186/s12862-020-01609-4">doi:10.1186/s12862-020-01609-4</a>.
