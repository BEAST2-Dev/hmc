---
layout: site
title: BEAST 2 Help Me Choose Rate CT Prior
tags: []
---

## Rate CT Prior

The rate CT parameter of the GTR model (Tavaré, 1986) represents how large transversion rate C <-> T is when all transversion rates are set to 1. 
Since this is a rate parameter, a distribution with a range from 0 upwards is appropriate.

Note that since BEAST normalises rates, not all six rates should be estimated to prevent unidentifiability.
Since the CT rate is usually one of the larger rates, fixing it to 1 prevents numerical instability, unlike fixing one of the transversion rates, which can be small.
So, it is not recommended to estimate the CT rate (and then no CT prior is required).


## References 

Tavaré S. Some probabilistic and statistical problems in the analysis of DNA sequences. Lectures on mathematics in the life sciences. 1986 Dec 31;17(2):57-86.
