---
layout: site
title: BEAST 2 Help Me Choose Mutation rate prior
tags: []
---

## Mutation rate prior

The mutation rate prior is the prior on the relative mutation rates/substitution rates for tree likelihoods of partitions.

This prior is only added when the `Fix mean substitution rate` flag at the bottom of the site model panel is set to false.
This can only be done when the menu `Mode => Automatically set fix mean substitution rate flag` is un-checked -- which should only be done in exceptional circumstances.
Note that if there is more than one clock rate for the partitions, there is the danger of unidentifiability.

The mutation rate is a rate prior, so has a range of zero to infinity.
So, only distributions with similar or narrower range are suitable, like a log normal, or (inverse) gamma distribution.
It depends on the reason for estimating this rate on how to inform the distribution, though I cannot think of a scenario on when to use this option at the moment. 
Let me know if you encountered a situation where this prior was required.
