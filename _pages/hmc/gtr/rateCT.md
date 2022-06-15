---
layout: site
title: BEAST 2 Help Me Choose GTR rate CT
tags: []
---

## GTR rate CT

Substitution rate between C and T (default 1) in the GTR (Tavaré, 1986) nucleotide substitution model. 


### `value`

Since the transition rates (A <=> G and C <=> T) tend to be larger than the transversion rates (A <=> C, A <=> T, C <=> G and G <=> T), one expects a value larger than 1 for rate AG. The default of 1 makes a good starting value if estimated. If not estimated, a value based on prior information can be used, but this would reduce the uncertainty in the analysis.

### `estimate`

Rate CT can vary per dataset, so it is usually estimated. Note that at least one of the GTR rates needs to be fixed (i.e. not estimated), because estimating them all leads to unidentifiability due to BEAST normalising rates so that the average rate is 1. Fixing a transition rate (rate AG or rate CT) usually provides more numerical stability than fixing a transversion rate), so setting estimate for rate CT to false is recommended if the estimate flag for rate AG is set to true.

### `lower`

Since rate CT is a rate parameter, it should always be positive and have a lower bound of at least 0. This is only relevant if `estimate` is true and ignored otherwise.

### `upper`

An upper value for the rate CT parameter is usually not set, though rate CT is usually in the range of 1 to to low teens.
This is only relevant if `estimate` is true and ignored otherwise.


## References 

Tavaré S. Some probabilistic and statistical problems in the analysis of DNA sequences. Lectures on mathematics in the life sciences. 1986 Dec 31;17(2):57-86.

See also [substitution models](https://en.wikipedia.org/wiki/Substitution_model).