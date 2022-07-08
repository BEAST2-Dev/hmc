---
layout: site
title: BEAST 2 Help Me Choose Growth rate prior
tags: []
---

## Growth rate prior

This is the prior on the growth rate parameter under the coalescent model with an exponential growth rate.
When the growth rate is zero, the population is constant through time.
A positive growth rate results in an exponentially growing population size towards the present, and a negative growth rate results in an exponentially shrinking population size towards the present.

In principle, there is no theoretical upper or lower bound on the growth rate, though be aware that a value of ln(2)=0.69 already implies a doubling of the population per unit of time (so -0.69 implies a halving per unit of time).
You can adjust your 95% HPD to take this in account.
Distributions that cover an infinite range but prefer values closer to 0 over values far away from 0 can be suitable, such as the Laplace and normal distributions.

If you have reason to believe the population is growing, a slight bias towards positive values can be justified.
Be aware that this results in a lower tree than under the constant population size through time, and the prior on present day population size may need to be adjusted to prefer higher values than under the constant population size.

See also [exponential population mean prior](/hmc/Priors/ePopSizePrior/).
