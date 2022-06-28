---
layout: site
title: BEAST 2 Help Me Choose random local clock -- scaling
tags: []
---

## Random local clock -- scaling

If true, branch rates are normalised taking branch lengths in account so that the mean branch rate is equal to the mean clock rate.
Consequently, any MCMC proposal that changes any of the rates affect all branch rates and the tree likelihood for all internal nodes need to be recalculated.

If false, then ignore the mean clock rate and leave rates unscaled.
In this case, rates are not normalised so the rate parameter represents actual clock rates.

If scaling=true, the rate prior should have a mean of 1, and is scaling=false, the rate prior should have a mean of the expected clock rate.

See also [rate prior](/RandomLocalClock/RatesPrior/)