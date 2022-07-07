---
layout: site
title: BEAST 2 Help Me Choose Operator weight tuning
tags: []
---

## Operator weights

Each operator has a relative weight, and the operator schedule selects operators with a probability proportional to that weight.
Increasing the weight of an operator usually results in higher [ESSs](https://www.beast2.org/what-is-ess/) for the parameter that proposals are made for.

Some operators require more expensive recalculations than others, for example, scaling a substitution model parameter (e.g. kappa for HKY) requires recalculation of the likelihood for the complete tree, while scaling the root height only requires recalculation of partials at at the root.
Operators that move a few internal nodes require recalculation of partials from the nodes that changed height and/or position to the root of the tree.
Operators that scale a large part or the whole of the tree, or change the mean clock rate require recalculations of every partial in the tree, which is relatively expensive.
Operators on tree prior hyperparameters (like on the birth rate of the Yule model) do not require treel ikelihood calculations but only the tree prior to be recalculated, so are typically computationally cheap (assuming the tree prior can be calculated efficiently).

Generally, operator weights for substitution model parameters, mean clock rate parameters and tree scaling are therefore kept as low as possible, while still providing good ESSs for these parameters and good mixing of the trees.

## Weight tuning

Weights can be altered from the default if you observe low ESSs in Tracer.

### Low ESS for single parameter

If only a few parameters (like the kappa and base frequencies parameters for the HKY substitution model) have low ESSs compared to other entries in the trace log, this can be fixed by increasing the operator weight.
ESS for single parameters is more or less proportional to the weight of the operator, so if you want an ESS of 200, but observe an ESS of 50, increase the operator weight by a factor of 200/50=4.
 
### High ESS for single parameter

If the ESS of a single parameter is very far from the rest (say over twice the desired ESS), it may be worth reducing the weight to reducing calculation time.

### Low ESS for correlated parameters

Correlation between parameters can be shown in Tracer in the `joint-marginal` panel.

If you spot high correlation between some parameters that have low ESS, e.g. clock rate and tree height, increase the weight of operators that operate on both of them, like the up-down operator for clock and tree, or the TreeStretchOperator that takes also includes the clock rate.

### Low ESS for prior and tree height/length

If the ESS for prior and tree height and length are low relative to other parameters, this usually indicates bad mixing of the tree.

There are many operators that do proposals for trees, and the ones that move single internal node heights and sub-tree slide a node already have high weights.
For very large trees, it may be worth increasing the weight of these operators.
If that does not help, consider increasing the weight of the BICEPS operators: epoch flexer and tree stretcher.



 