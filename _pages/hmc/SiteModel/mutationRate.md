---
layout: site
title: BEAST 2 Help Me Choose Site Model mutation rate
tags: []
---

## Site Model mutation rate

The substitution rate/mutation rate entry in the site model represents the *relative* rate of the partition. 

## `value`

Leave the starting value at 1.

## `estimate`
If you only have a single partition, there is no point in estimating this rate.

If you have multiple partitions (e.g. because you split the alignment on codon partitions in the Partitions panel, or because there are multiple loci in the data), it makes sense to set `estimate` to true. 

BEAUti will automatically add an operator that ensures that the average rate *per site* remains at one. This is indicated by the `Fix mean mutation rate` flag at the bottom of the site model panel. Keeping the average rate per site at one means that if you have two partitions, one of 2000 sites and another of 1000 sites, the mutation rate for the first partition can become 0.5, but then the rate for the second partition must become 2 to maintain an average site rate of 1 (0.5 x 2000 + R x 1000 = 3000 => R = 2). 

So, the average of the mutation rates do not necessarily have to be 1: in the example the average is (0.5+2)/2 = 1.25.

## `lower`

Since this is a (relative) rate parameter, the lower value should be at least 0.


## `upper`

An upper bound of the number of partitions is implied when the `Fix mean mutation rate` flag is set, and no further action is required.


## `Fix mean mutation rate`

The flag cannot be edited by default, but by toggling the menu `Mode => Automatic set fix mean substitution rate flag` checkbox, you can set it by hand.

When the flag is set, BEAUti automatically adds a delta exchange operator with appropriate weights on the substitution/mutation rates, which is the recommended way of using estimated substitution/mutation rates.