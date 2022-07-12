---
layout: site
title: BEAST 2 Help Me Choose Trace log -- log every
tags: []
---

## Trace log -- log every

Number of the MCMC steps before a sample is being logged.

Usually, a total of ten thousand samples in the trace log is sufficient, and having more samples only wastes disk space and makes processing the trace log more cumbersome. So,  taking the total number of MCMC steps and divide this by 10.000 makes a good value for `logEvery`.

Note that the required chain length differs between data sets and models, so that is a value that needs to be established by a bit of experimentation. 

It is probably a good idea to keep the `logEvery` of the tree log the same as that of the tree log.