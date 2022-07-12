---
layout: site
title: BEAST 2 Help Me Choose Operator schedule -- auto optimize delay
tags: []
---

## Operator schedule -- auto optimize delay

The auto optimize delay is the  number of samples to skip before auto optimisation kicks in.
Delaying auto optimisation of operators may be useful because during burn-in an atypical part of the state space is sampled.
Optimising for that part of the state space may be sub-optimal.

By default, it is 10000.
When you run an analysis and the operator report at the end of the MCMC run suggests a lot of changes to operator paramaters, this may be an indication that auto optimisation is not working properly.
In this case, increasing the auto-optimize delay may improve automatic operator tuning.
