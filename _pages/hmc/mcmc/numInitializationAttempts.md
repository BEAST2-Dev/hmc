---
layout: site
title: BEAST 2 Help Me Choose MCMC num initialization attempts
tags: []
---

## MCMC number of initialization attempts

The MCMC state is usually initialised using a random tree, which may not always lead to a posterior that is not-zero due to numerical error or due to priors not providing any support.
With a zero posterior (-Infinity log posterior), the MCMC cannot start, so it may be necessary to try another random tree. The number of initialisation attempts sets the number of tries before giving up (default=10). 
