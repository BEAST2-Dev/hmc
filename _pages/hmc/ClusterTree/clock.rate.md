---
layout: site
title: BEAST 2 Help Me Choose Cluster tree -- clock.rate
tags: []
---

## Cluster tree -- clock.rate

The clock rate parameter, used to divide all divergence times by, to convert from substitutions to times.
By default, this is set to 1, so the cluster tree will be in units of substitutions.
This may result in a relatively small tree, resulting in numerical issues (especially with the tree prior) resulting in the MCMC not being able to start.
Decreasing the clock rate to something more realistic than the default 1.0 may solve this problem.
