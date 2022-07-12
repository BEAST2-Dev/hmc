---
layout: site
title: BEAST 2 Help Me Choose Newick tree -- threshold
tags: []
---

## Newick tree -- threshold

Threshold under which node heights (derived from lengths) are set to zero.
Since the Newick tree only specifies branch lengths, not node heights, the lack of precision in these branch lengths can cause the tips to have a height that substantially deviates from zero.
For ultrametric trees (i.e. trees for which the length from the root to the tips is the same for all trees) represented in Newick format setting the threshold to a non-zero level can be used to compensate for this lack of precision.

