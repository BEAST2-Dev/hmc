---
layout: site
title: BEAST 2 Help Me Choose kernel distribution
tags: []
---

## Kernel distributions

Bactrian operators sample from a `kernel distribution` from which a proposal is created.
The following kernel distributions are currently implemented, many of them propossed in Yang & Rodríguez (2013) and Thawornwattana et al (2018).

| Name    | Distribution         | Bactrian? |
|---------|----------------------|-----------|
| uniform |  uniform distribution | no |
| normal | normal distribution | no |
| laplace | Laplace distribution | no |
| t4 |   T-distribution with 4 degrees of freedom | no |
| cauchy | Cauchy distribution  | no |
| bactrian_normal | normal distribution  | yes |
| bactrian_laplace | Laplace distribution | yes |
| bactrian_triangle | triangle shaped distribution | yes |
| bactrian_uniform | uniform distribution | yes |
| bactrian_t4 |  T-distribution with 4 degrees of freedom | yes |
| bactrian_cauchy | Cauchy distribution | yes |
| bactrian_box | box-shaped distribution | yes |
| bactrian_airplane | airplane distribution | yes |
| bactrian_strawhat  | strawhat distribution |yes |
|--------------------|-----------------------|----|

The default kernel distribution is the Bactrian normal distribution.
This seems to perform well for a wide range of cases (see also [BEAST 2 benchmark](http://www.beast2.org/2021/04/26/bactrian-proposals.html)).
So, there does not seem a compelling reason to switch -- let me know if you know any.


## References

Yang Z, Rodríguez CE. Searching for efficient Markov chain Monte Carlo proposal kernels. Proceedings of the National Academy of Sciences. 2013 Nov 26;110(48):19307-12. [doi: 10.1073/pnas.1311790110]((http
s://doi.org/10.1073/pnas.1311790110)).

Thawornwattana Y, Dalquen D, Yang Z. Designing simple and efficient Markov chain Monte Carlo proposal kernels. Bayesian Analysis. 2018;13(4):1037-63. [doi: 10.1214/17-BA1084](http
s://doi.org/10.1214/17-BA1084),