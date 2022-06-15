---
layout: site
title: BEAST 2 Help Me Choose MCMC sample from prior
tags: []
---

## MCMC sample from prior

Flag to indicate whether to ignore the likelihood when sampling (default false). 
The distribution with id `likelihood` in the posterior input will be ignored when this flag is set.

Since BEAST models tend to be complex with interacting distributions, it is always good practice to sample from the prior before sampling from the posterior.
A sample from the prior provides insight in these interactions. 
Also, comparing a sample from the prior with that of the posterior allows you to infer whether conclusions follow from prior assumptions, or are informed by the data.
