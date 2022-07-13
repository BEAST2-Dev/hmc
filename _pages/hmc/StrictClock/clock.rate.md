---
layout: site
title: BEAST 2 Help Me Choose clock.rate
tags: []
---

## Clock model -- clock.rate

The `clock.rate` represents the mean clock rate of the clock model.

## `value`

When estimated, the starting value usually does not matter much, since the clock rate often quickly converges towards its posterior value.

Fixing the clock rate at 1 means the tree will be in units of substitutions.
When fixing the clock rate to another value (e.g. value from the literature), be aware of the units of the tree: if it is in millions of years (e.g. because node calibrations are in millions of years) the clock rate needs to be adjusted to represent mutations per millions of years.

## `estimate`

By default, BEAUTi works out automatically whether the estimate flag should be set or not, and the estimate box is disabled, so you don't need to choose to set this.

To override this behaviour, uncheck the `Mode => Automatic set clock rate` box. 
This is probably only needed when the only timing information is from a strong clock rate prior.

If there is timing information in the analysis (i.e. tip dates, node calibrations, strong clock rate prior) the clock rate should be estimated.
If the tree is shared among partitions, but the clock model is not shared, and this is the second partition, the clock rate should be estimated.
Otherwise, the clock rate should not be estimated.

## `lower`

Since this is a rate parameter, it cannot be negative, and the lower bound should be at least 0.
In rare occasions, it may help to put in a lower bound bigger than zero to prevent the MCMC escaping to an area of tree space with extremely large trees and extremely low clock rates.
Usually, a lower bound of 0 is fine.

## `upper`

Setting an upper bound is not recommended for the clock rate. 
It will be informed by the prior and the data.
In rare occasions, it may help to put in a large upper bound far away from the posterior to prevent the MCMC escaping to an extemely small trees and extremely large clock rates.
Usually, an upper bound of Infinity is fine.



See also [clock rate prior](../../Priors/ClockPrior/)