---
layout: site
title: BEAST 2 Help Me Choose Relaxed clock -- normalize
tags: []
---

## Relaxed clock -- normalize

Whether to normalize the average rate (default false), which ensures that the branch mean rate is equal to the mean clock rate, taking the length of branches in account.
However, there is a computational cost involved, since every time a branch rate change is proposed by an operator, all branche rates change, so the tree likelihood needs to be recalculated for each node in the tree.
The mean clock rate is logged by the `RateStatistic` logger, which also logs the variance and coefficient of variation of a relaxed clock.
Usually, this mean clock rate deviates only little from the actual mean clock rate.
So, since the mean clock rate is available in the trace log (though it differs slightly from the clock rate parameter) there is no need to normalize.
