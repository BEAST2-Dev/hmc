---
layout: site
title: BEAST 2 Help Me Choose Random local clock -- rates are multipliers
tags: []
---

## Random local clock -- rates are multipliers

True if the rates should be treated as multipliers and rates at internal nodes that are switch points are calculated as the the product of the parent rate and the branch rate.
This can make the random local clock behave more like a correlated clock if the [prior on rates](/RandomLocalClock/RatesPrior/) is narrow. 
However, the implication is also that if a rate change is proposed at a switch point, the complete clade below gets new rates and therefore the tree likelihood needs to recalculate partials for all these nodes, which is less efficient than if rates are not multipliers.