---
layout: site
title: BEAST 2 Help Me Choose GTR rate priors
tags: []
---

## GTR rate priors

The rate parameters of the GTR model (Tavaré, 1986) are typically not all estimated.
Since BEAST normalises rates, not all six rates should be estimated to prevent unidentifiability.
Since the CT rate is usually one of the larger rates, fixing it to 1 prevents numerical instability, unlike fixing one of the transversion rates (AC, AT, CG, GT), which can be small.
So, it is not recommended to estimate the CT rate (and then no CT prior is required).

Since this is a rate parameter, a distribution with a range from 0 upwards is appropriate.
Furthermore, unless characters are missing from the aligment, GTR rates tend to be non-zero, so a prior should be 0 at 0.

Assuming the CT rate is fixed at 1, the mean of the tranversion rate priors (rates AC, AT, CG, GT)  should be below 1, e.g. 0.5 and for example a Gamma(shape=2, scale=0.25) could be appropriate.
Furthermore, the rate prior on the remaining transition (rate AG) should have a mean the same as the other transition rate, i.e. 1 and for example a Gamma(shape=2, scale=0.5) could be appropriate. 

## References 

Tavaré S. Some probabilistic and statistical problems in the analysis of DNA sequences. Lectures on mathematics in the life sciences. 1986 Dec 31;17(2):57-86.
