---
layout: site
title: BEAST 2 Help Me Choose MCMC store every
tags: []
---

## MCMC store every

Store the state to disk every X number of samples so that we can resume computation later on if the process failed half-way, or the MCMC has not converged and requires longer sampling.
If less or equal to zero, the state will be stored with default frequency (every 5000 states for most BEAUti templates).

Resuming requires the trace log, tree log and state file to be available. 
Storing the state more often than trace log or tree log is stored results in potential mismatches when resuming.
Therefore, it makes most sense to set the `storeEvery` the same as the trace log and and tree log `logEvery` value.

If resuming is not required, `storeEvery` can be set the same or higher than the `chainLength`.
