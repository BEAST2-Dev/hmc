---
layout: site
title: BEAST 2 Help Me Choose MCMC pre burnin
tags: []
---

## MCMC pre burnin

Number of burn in samples taken before entering the main loop. 
These samples do not show up in the trace and tree logs, nor is there screen output.
So, the logs will only contain samples from the stationary part of the MCMC run. 
This reduces the size of these log files, which can be useful for reducing disk space and time transferring and processing logs.

Since the amount of burn-in required is not known beforehand, this needs to be determined experimentally.
Usually, 10% of the [chain length](../chainLength/) is sufficient, but that is an unknown quantity as well.
If disk space is of no consideration, setting pre-burnin to zero is fine, but then burn-in needs to be removed from trace and tree log in post-processing applications like Tracer, TreeAnnotator, DensiTree, etc..
