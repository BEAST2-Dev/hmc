---
layout: site
title: BEAST 2 Help Me Choose Standard template -- operators panel
tags: []
---

## Standard template -- operators panel

There are two sections in the operators panel

* a list of operators
* an entry for the operator schedule

The list of operators allow specifying operator parameters, the most important being the operator weight. 

## Adjusting operator weights

The weight determines how often the operator is allowed to make proposals relative to other operators.
Default values are probably fine for a wide range of data sets, but you might want to change these values when after running MCMC some parameters have low ESSs. 
If that happens, identify the operators that do proposals for that parameter, and increase the weight of these operators.

For example, if base frequencies of the substitution model have low ESS, the delta exchange operator can have its weight increased from 0.1 to say 0.2 if ESSs are only slightly worse than other parameteres, or 0.5 if the ESSs is considerably less than other parameters.
If the prior has low ESS, find the delta-exchange operator for frequencies, and adjust the weight entry.

If the `prior` has low ESS in Tracer but the `likelihood` has good ESS, find the parameter that mixes badly. 
If it is the tree prior, consider increasing the weight on Epoch Flex operators and the Tree Stretch operators.

If the `likelihood` has low ESS but the `prior` has good ESS, this may be due to the likelihood of one of multiple partitions having low ESS. 
Consider increasing the weight of all tree operators for that partition.



## Tuning operator parameters

At the end of an MCMC run, an operator report is printed that looks someting like this:

```
Operator                                              Tuning    #accept    #reject      Pr(m)  Pr(acc|m)
ScaleOperator(YuleBirthRateScaler.t:dna)             0.29041       1949       2021    0.03989    0.49093 Try setting scaleFactor to about 0.084
ScaleOperator(YuleModelTreeScaler.t:dna)             0.68394        393       3580    0.03989    0.09892 Try setting scaleFactor to about 0.827
ScaleOperator(YuleModelTreeRootScaler.t:dna)         0.71922        421       3587    0.03989    0.10504 
Uniform(YuleModelUniformOperator.t:dna)                    -      10305      29590    0.39894    0.25830 
SubtreeSlide(YuleModelSubtreeSlide.t:dna)            0.28411        541      19587    0.19947    0.02688 Try decreasing size to about 0.142
Exchange(YuleModelNarrow.t:dna)                            -        629      19238    0.19947    0.03166 
Exchange(YuleModelWide.t:dna)                              -          7       3998    0.03989    0.00175 
WilsonBalding(YuleModelWilsonBalding.t:dna)                -          6       3907    0.03989    0.00153 
ScaleOperator(KappaScaler.s:dna)                     0.57917         23         91    0.00133    0.20175 
DeltaExchangeOperator(FrequenciesExchanger.s:dna)    0.03331         58         70    0.00133    0.45313 Try setting delta to about 0.064

     Tuning: The value of the operator's tuning parameter, or '-' if the operator can't be optimized.
    #accept: The total number of times a proposal by this operator has been accepted.
    #reject: The total number of times a proposal by this operator has been rejected.
      Pr(m): The probability this operator is chosen in a step of the MCMC (i.e. the normalized weight).
  Pr(acc|m): The acceptance probability (#accept as a fraction of the total proposals for this operator).
```

In case the actual acceptance probability for an operator is not close enough to the target, there can be some suggestions to change the target. If you plan to run another replicate of the analysis, this should be done in the XML, or in BEAUti in the operators panel (use menu View/Show operators panel to show the list of operators).

Above, it is suggested to change the scaleFactor for the birth rate scaler to 0.084.
Open the XML in BEAUti, go the the operators panel, open the birth rate scale operator and change the default value of 0.75 to 0.084.





## Tuning the operator schedule



Operators can have tuneable parameters, such as the scale factor for the scale operator and window size for the real random walk operator. If the operator is allowed to optimise this parameter (when the `optimise` attribute is set to `true`, as is the default for most operators), this parameter is changed during the MCMC to get an optimal balance between boldness of them move and acceptance rate. For many operators, the target acceptance probability is 0.234, but for [Bactrian operators](http://www.beast2.org/2021/04/26/bactrian-proposals.html) it is usually a bit higher at around 0.4.


### `autoOptimize`

The way tuneable parameters are changed is determined by the operator schedule. 
The default operator schedule has the `autoOptimize` input that determines whether to automatically optimise operator settings (true by default). 

### `autoOptimizeDelay`

If `autoOptimize` is true, it does not start to optimise immediately, but waits a number of MCMC samples. 
The `autoOptimizeDelay` input determines the number of samples to skip before auto optimisation kicks in (default=10000). 
This is to ensure that most of burn-in is skipped, because this is time during the MCMC that proposals are not typical for the stationary part of the chain. 
It may be necessary to increase `autoOptimizeDelay` for large analyses. 
When there are many suggestions in the operator report at the end of the MCMC run, this is a sign that changing the delay can be beneficial.

### `transform`

After `autoOptimizeDelay` sampels are skipped, for every operator the number of accepted and rejected proposals are tracked and the parameter is tuned based on

* the desired operator acceptance probability
* the number of accepts and rejects so far
* logAlpha, which is the difference between the log posterior of previous state and the log posterior of proposed state + Hastings ratio
* the `transform` for the operator schedule. This can be `none`, `log`, or `sqrt` and is `none` by default.
 
To guarantee that the MCMC produces a proper sample, tuning should gradually be reduced to the point of not changing parameters, so the proposed change is proportional to 1/number of proposals (where number of proposals = number of accepts  + number of rejects). However, since 1/x drops down too quick sometimes, it is possible to use a log transform, that is use 1/log(x), or a square root transform (use 1/sqrt(x)). 
The latter is not recommended, since it may nor drop down fast enough, but the log transform should be OK for difficult to converge analyses.


