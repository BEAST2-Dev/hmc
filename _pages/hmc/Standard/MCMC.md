---
layout: site
title: BEAST 2 Help Me Choose Standard template -- MCMC panel
tags: []
---

## Standard template -- MCMC panel

Though MCMC is the workhorse of Bayesian inference, and the default option in the Standard template in BEAUti, MCMC does not always converge, or provide the information that we want.
Alternatives to MCMC are:

* [Coupled MCMC](https://github.com/nicfel/CoupledMCMC) (Müller & Bouckaert, 2020) can help with mixing, and provides higher [ESS](https://www.beast2.org/what-is-ess/) per hour at the cost of using extra threads.
* [Nested sampling](https://github.com/BEAST2-Dev/nested-sampling) (Maturana et al, 2019) not only provides a posterior sample, but estimates the marginal likelihood and standard deviation of that estimate.
* [Path/stepping stone sampling](https://github.com/BEAST2-Dev/model-selection) provides an estimate of the marginal likelihood, but no posterior sample.

## Obtaining a posterior sample with MCMC

Usually, running the same XML file multiple times (say 4) with MCMC is sufficient to establish whether the MCMC converges: 

1) check the ESSs in Tracer and make sure most values are over 200 -- some parameters that are not of interest can be kept below 200 but over 100, but posterior, likelihood and prior should be over 200. 
2) make sure parameter estimates for the different runs are similar by comparing distributions for each parameter in Tracer's marginal distribution panel.
3) make sure the tree posteriors are similar by using the [clade comparator](https://www.beast2.org/2020/04/20/comparing-tree-sets.html).

## Coupled MCMC -- when MCMC fails to converge

Coupled MCMC runs multiple (typically 4) chains in parallel, where one chain runs MCMC on the posterior, and the others on a 'heated' posterior. 
Heating the posterior allows easier escape from local maxima, so by interchanging states among chains, the posterior distribution can be more efficiently sampled.
In practice, this means that coupled MCMC can often converge where MCMC does not.
A further benefit is that it returns a higher ESS/unit of time, at the cost of more computation (Müller & Bouckaert, 2020).

To check convergence, run multiple coupled MCMC instances and check the three items listed above for MCMC on the output.


## Nested sampling -- when coupled MCMC fails to converge

Nested sampling provides another way to produce a posterior, and produces a marginal likelihood estimate and estimate of its uncertainty in one run.
By providing nested sampling with more than 1 particle, it can escape local maxima where even coupled MCMC gets stuck.
It tends to require longer run times, though a [parallel version](https://github.com/BEAST2-dev/nested-sampling/wiki/How-to-use-NS#multi-threaded-nested-sampling) exists that can speed things up.


ESS estimates are provided at the and of a nested sampling run. 
Like for MCMC and coupled MCMC, run multiple instances and compare parameter distributions in Tracer and tree distributions by clade comparator to check whether the analysis is sound.
If not, increase the sub-chain length and run again.

## Bayesian hypothesis testing

If you want to perform [Bayesian hypothesis testing in BEAST](http://www.beast2.org/2021/11/01/hypothesis-testing.html), first ask whether there is a reason *not* to do this, since it is usually computationally very expensive.

'''
Note: make sure the hypotheses matter.
If the question of interest is not changed by changing the hypothesis (e.g. strict vs
relaxed clock) there is no point in distinguishing the hypotheses.
'''

If there is no other way than to estimate marginal likelihoods, there are two options: path sampling and nested sampling (see previous section).
For path sampling, there is no good way to estimate the uncertainty of the marginal likelihood estimate other than run many analyses, while for nested sampling there is. On the other hand, nested sampling can take longer to finish.



## References

Maturana PM, Brewer BJ, Klaere S, Bouckaert RR. Model selection and parameter inference in phylogenetics using Nested Sampling. Systematic biology. 2019 Mar 1;68(2):219-33. <a href="https://doi.org/10.1093/sysbio/syy050">doi:10.1093/sysbio/syy050</a>.

Müller NF, Bouckaert RR. Adaptive Metropolis-coupled MCMC for BEAST 2. PeerJ. 2020 Sep 16;8:e9473. <a href="https://doi.org/10.7717/peerj.9473">doi:10.7717/peerj.9473</a>.