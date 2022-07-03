---
layout: site
title: BEAST 2 Help Me Choose Death Rate Prior
tags: []
---

## Death rate prior

The death rate prior is the prior on the relative death rate of the birth-death tree prior.

Let \\(\lambda\\) be the birth rate, and \\(\mu\\) be the death rate of the model then  \\(m = \mu/\lambda\\). 
Since \\(\mu\\) and \\(\lambda\\) are rates, thus positive, \\(m\\) is lower bounded by 0.
If \\(m>1\\) this implies \\(\mu>\lambda\\) thus extinction exceeds speciation and we should expect the process to produce no taxa.
It is reasonable to assume \\(0<m<1\\).
Unless there is more information available, a uniform(0,1) prior on \\(m\\) seesm reasonable.
