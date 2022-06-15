---
layout: site
title: BEAST 2 Help Me Choose Screen log -- log every
tags: []
---

## Screen log -- log every

Number of the MCMC steps before a sample is being logged to screen.

Since it gives real time feedback on how far the chain has progressed, and an estimate of the time per million states, from which the rest of the run time can be estimated, the log frequency should be chosen such that screen output is regularly created, but not too often that the screen log races over the screen (which can significantly reduce the speed of the MCMC algorithm). Since every data set is different with different run times, some experimentation is required to find a good value for `logEvery`.

For BEAST runs on servers, there is not much information in the screen log that is not already in the trace log (typically only some run-time information), so a low frequency (i.e. high value for `logEvery`) will do.