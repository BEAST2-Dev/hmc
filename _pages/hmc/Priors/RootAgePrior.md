---
layout: site
title: BEAST 2 Help Me Choose Root age prior
tags: []
---

## Root age prior

By specifying a root age prior for the tree, it is possible to keep priors on parameters of the tree prior (like the birth rate for the Yule prior, or population size for coalescent priors) in check, even if an improper prior is defined on there parameters (e.g. a Uniform(0,\\(\Infty\\)) prior on birth rate).
These parameters are linked to the root age via the tree prior, so these parameter can not vary independently of the height of a tree.


## How to determine a root age prior

Following the recommendations of O'Hagan et al (2006) Chapter 6, 

1) determine a lower (\\(t_{low}\\)) and upper bound (\\(t_{hi}=1\\)) where the root age may be with 95% probability. 
2) estimate the expected age at which there is 50% change the age is lower, and 50% the age is higher (i.e the median).
3) fit a parametric distribution to \\(t_{low}\\), \\(t_{hi}=1\\) and median.


## Step 1: Determine a lower (\\(t_{low}\\)) and upper bound (\\(t_{hi}=1\\))

It is not necessary for the estimates of the bounds to be strongly informative: having 4 orders of magnitude difference is fine if that reflects the uncertainty you have for the age range. Often, there is more information available that can help estimating the range. Here are some situations and some hints on how to determine bounds:

### Strong information about the root age

If you have strong information about the age of the tree based on previous information, this can be used to inform the bounds.
For example, for SARS-CoC-2 we know it emerged in the second half of 2019 giving us an upper bound with high probability, and a lower bound should be at least as high as the oldest sample in the analysis.

### No timing information available

If there are no time calibrations and the tree is in units of substitutions, we do not expect the tree to be much over 1 or under 0.01, so \\(t_{low}=0.01,t_{hi}=TODO\\) would do. 

### Strong clock rate prior, but no other timing information

If you have a strong clock rate prior based on previous *independent* analyses, but no tip dates or clade calibrations, this can still inform the age of a tree. 
Use the age estimates of the independent analyses that form the basis of the clock rate prior to inform.
Also, be aware that if the clock rate is \\(c\\), then the tree will probably not much over \\(TODO/c\\) or below \\(0.01/c\\), which give you extra constraints on the bounds.

### Timing information available

If there is age information in the form of clade calibrations or sampled tips, be aware that the root ages more than ten times higher than the oldest calibration or tip date are very hard to estimate, and get increasing uncertain the higher this fraction.
If there is no other information, an upper bound about ten times the oldest calibration or tip date would then be sensible.





## Step 2: Determine a median

Based on information about the data from the literature or previous experience, estimate the expected age at which there is 50% change the age is lower, and 50% the age is higher (i.e the median).

## Step 3: Fit a parametric distribution 

Choose a parametric distribution to specify the prior.
Since the root age is non-negative, the range of the distribution should be non-negative and e.g. log-normal or (inverse) gamma distributions are appropriate.
I am not aware of any reason to choose one over the other for root age priors, so it is personal preference on which distribution to choose.

BEAUti shows the mean and 95% HPD of the distributions below the density graph, and updates them when updating paramaters of the distribution.
Use the median and 95% HPD obtained from Step 1 & 2 to parameterise the chosen distribution so that the mean of Step 1 and the 95% HPD of Step 2 match with that of the distribution. 

Note that with the log-normal distribution \\(S=1.175\\) gives a range of two orders of magnitude, and with \\(S=2.35\\) it gives a range of four orders of magnitude. 
The median is in the middle of the range in logspace, e.g. with \\(M=-6.906,S=1.175\\), the 95% HPD range is 1e-4 to 1e-2 with median 1e-3. 
With \\(S=2.35\\) the range changes to 1e-5 to 1e-1, but the median remains at 1e-3.



## How to add a root prior in BEAUti

A root age prior can be added in the priors panel by clicking the `+ Add priors` button at the bottom.
In the dialog that pops up, select all taxa (click first taxon, use keys Ctrl-A or Cmd-A to select the rest) and add `root` for the label.
Click the `OK` button, and a new entry with label `root.prior` appears in the list of priors.
Select a parametric distribution in the drop-down box with distributions, and parameterise according to your prior.

```
Note: if clock prior is added when a root age distribution is selected this may indicate there is no other timing information that can inform the clock rate and the analysis will struggle to converge if the root age prior is quite wide.

If there is not strong timinig information, the mean clock rate of the clock model should not be estimated: uncheck the estimate box in the clock model panel -- you may need to uncheck via menu `Mode => Automatic set clock rate` to enable the estimate box.
```




## References 

O'Hagan A, Buck CE, Daneshkhah A, Eiser JR, Garthwaite PH, Jenkinson DJ, Oakley JE, Rakow T. Uncertain judgements: eliciting experts' probabilities. 2006