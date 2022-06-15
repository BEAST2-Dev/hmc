---
layout: site
title: BEAST 2 Help Me Choose MCMC operator schedule
tags: []
---

## MCMC operator schedule

Specify operator selection and optimisation schedule for the MCMC run.
The default operator schedule changes the way operators behave during the MCMC so that operators are optimally tuned to produce the most efficient proposals: not too bold that they always get rejected, not to timid that it takes a long time to traverse the whole space.
 
The [Bactrian operator schedule](https://www.beast2.org/2021/04/26/bactrian-proposals.html) replaces standard operators with Bactrian variants.


See also: operator schedule settings -- 
[auto optimize](../OperatorSchedule/autoOptimize/), 
[auto optimize delay](../OperatorSchedule/autoOptimizeDelay/), 
[detailed rejection](../OperatorSchedule/detailedRejection/), 
[transform](../OperatorSchedule/transform/), 
[weight](../OperatorSchedule/weight/), 
[weight is percentage](../OperatorSchedule/weightIsPercentage/).