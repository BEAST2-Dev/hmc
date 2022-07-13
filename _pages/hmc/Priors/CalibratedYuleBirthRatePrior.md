---
layout: site
title: BEAST 2 Help Me Choose Calibrated Yule birth rate prior
tags: []
---

## Calibrated Yule birth rate prior

See [Yule birth rate prior](../YuleBirthRatePrior/).

Be aware that there is some unpredictable interaction between the calibrated Yule prior and calibrations, so always run an MCMC sampling from the prior and inspect the tree height distribution in tracer to be sure it is reasonable. 
If the distribution is not what you expect, adjust the birth rate prior till the prior distribution of the root height is satisfactory.