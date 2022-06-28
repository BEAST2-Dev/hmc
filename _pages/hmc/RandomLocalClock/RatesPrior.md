---
layout: site
title: BEAST 2 Help Me Choose random local clock -- rate prior
tags: []
---

## Random local clock -- rate prior

Since the rate parameter has different meaning for different settings of the `scaling` and `ratesAreMultipliers` settings, there are different strategies for determining the prior.

If `scaling=true`, the rate prior should have a mean of 1, and is `scaling=false`, the rate prior should have a mean of the expected clock rate -- see [clock prior](ClockPrior/index/) for details.

Be aware that the variance of the prior should be rather small if `ratesAreMultipliers=true`, and can be larger when `ratesAreMultipliers=false`.

Since these are rates, they are positive values and a distribution with a positive range should be used, e.g. one of the log-normal, gamma, inverse gamma, Weibel distributions.