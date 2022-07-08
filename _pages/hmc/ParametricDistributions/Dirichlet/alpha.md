---
layout: site
title: BEAST 2 Help Me Choose Dirichlet alpha
tags: []
---

## Dirichlet alpha

Coefficients of the Dirichlet distribution that form a [concentration parameter]( https://en.wikipedia.org/wiki/Concentration_parameter) for the distribution.

Its values can be interpreted as the number of observations plus one for each of the dimensions to which the Dirichlet distribution is applied.

The dimension of the parameter must be the same as the number of dimensions to which the Dirichlet distribution is applied.
For example, if applied as prior on base frequencies for a nucleotide substitution model, the dimension of alpha must be 4, given the dimension of the frequencies parameter is 4.

Setting all values of alpha to 1 results in a uniform distribution over a simplex.

See also [Dirichlet distribution](https://en.wikipedia.org/wiki/Dirichlet_distribution).


