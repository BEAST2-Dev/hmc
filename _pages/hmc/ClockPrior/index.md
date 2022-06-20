---
layout: site
title: BEAST 2 Help Me Choose Clock Prior
tags: [prior]
---

## Clock Prior

The clock prior is the prior on the mean clock rate. 

One should be careful about the units of the clock rate: a rate of 1e-12 mutations/site/year is 1e-6 mutations/site/million year. 
So, if your tree is in units of millions of years, the mean rate would be 1e-6, for a tree in millenia 1e-9, and for a tree in years it would be 1e-12.

Here is a three step recipe to specify a prior on the clock rate.

## Step 1: determine the expected clock rate 

Often, the literature provides some information about mutation rates for species similar to the one you are analysing.
For example Kumar et al (2002) suggest an average mammalian genome mutation rate is 2.2e−9 per base pair per year.
Sanjuán et al (2010) provide rates for some viruses ranging from 1e−8 to 1e−6 for DNA viruses and from 1e−6 to 1e−4 for RNA viruses. Jenkins et al (2002) has estimates for 50 RNA virussues in the range 1e-4 to 1e-2.
Krasovec et al (2020) estimate a rate of 5.5e−10 for phytoplankton.
There is probably some prior research available on closely related species to use as initial mean mutation rate, so search the literature for this. 
Experience from previous analyses can be used as well, if there is no overlap in the data being used in these analyses.

## Step 2: determine the uncertainty about the mean

Since the clock rate is a rate parameter, uncertainty is expressed in relative values (not absolute values). 
If one is *very* uncertain about the mean rate from Step 1 because the rate is based on distantly related species or genes, two orders of magnitude difference seems reasonable, that is, for a mean of 4e-6 one would get a 95% HPD of 4e-8 to 4e-4.
If the mean is based on closely related genes and species, a 95% HPD that allows an order of magnitude difference in the rate seems appropriate if there is no further information.
If more information is available the 95% HPD could be reduced even further.

## Step 3: use mean and 95% HPD from Step 1 & 2 to parameterise a distribution

Choose a parametric distribution to specify the prior.
Since it is a rate, the distribution should be non-negative, e.g. a log-normal or (inverse) gamma distributions are appropriate.
Since clock rate cannot be 0, it makes sense to use a distribution that has density of 0 at 0, like the log-normal density is for any value of its parameters, while the (inverse) gamma allows a non-zero density for some value of its parameters.
I am not aware of any reason to choose one over the other for clock rate priors, so it is personal preference on which distribution to choose.

BEAUti shows the mean and 95% HPD of the distributions below the density graph, and updates them when updating paramaters of the distribution.
Use the mean and 95% HPD obtained from Step 1 & 2 to parameterise the chosen distribution so that the mean of Step 1 and the 95% HPD of Step 2 match with that of the distribution. 

## Some other priors in use and why they are less desirable

### Uniform [0, Infinity)

A uniform prior is sometimes seen as non-informative: every clock rate is equally probably, and no preference is given to any particular value.
However, a Uniform [0, Infinity) is an [improper prior](https://en.wikipedia.org/wiki/Prior_probability#Improper_priors): it does not integrate to 1, and hampers creating a reasonable sample from the prior. In fact, sampling from the prior usually leads to the clock rate wandering off to infinity. This means comparing prior with posterior becomes a meaningless exercice.

### Uniform [0, 1]

So, how about restricting the range to [0, 1]? In general, the clock rate is a small number, in the range 1e-2 to 1e-10 depending on the species and time units of the tree. A uniform prior of [0, 1] implies that more than 99% of the probability mass (for rates of order 1e-2) and more than 99.9999% of the probability mass (for rates of order 1e-6 and smaller) is assumed a priori to be larger than the expected rate. So, even though we know beforehand that the rate should be of order 1e-2 or less (which we can find out from the literature), the uniform [0, 1] badly misrepresents that knowledge.

### Uniform other

Furthermore, the density is not 0 at 0, which we know beforehand cannot be true.

If a uniform prior could be used as follows: for an expected mean of say 1e-4 (from Step 1) but large uncertainty about this mean, a uniform [1e-5, 1e-3] prior could represent that knowledge. 
Still, if the data implies a clock rate outside this range this is not allowed by a uniform prior, so a log-normal or (inverse) gamma distribution would be a better choice.

### Jeffrey's prior 1/X

This is an [improper prior](https://en.wikipedia.org/wiki/Prior_probability#Improper_priors) that has infinite support at 0, contrary to our knowledge about clock rates. Putting a lower and upper bound on the clock rate parameter would make it a proper prior. The motivation of the prior is that it is invariant under transformation of units, which would be done away with by putting finite bounds on the parameter.

The 1/X prior can be approximated by a gamma(0.001,1000.0) prior (Lunn et al, 210, <a href="https://www.mrc-bsu.cam.ac.uk/wp-content/uploads/bugsbook_chapter5.pdf">section 5.2.7</a>) , making it a proper prior. However, note that this implies a mean rate of 1, which may deviate considerably from what we can expect from the literature (see Step 1).


## Miscellaneous

There is a vast literature about setting priors, e.g. Banner et al, (2020) and Sarma and Kay (2020) and references.
It is good practice to describe the prior in the methods section, and provide justification (e.g. reference to literature for mean, and magnitude of variance based on uncertainty about the rate).


## References

Banner KM, Irvine KM, Rodhouse TJ. The use of Bayesian priors in Ecology: The good, the bad and the not great. Methods in Ecology and Evolution. 2020 Aug;11(8):882-9. <a href=" https://doi.org/10.1111/2041-210X.13407">doi:10.1111/2041-210X.13407</a>.

Jenkins GM, Rambaut A, Pybus OG, Holmes EC. Rates of molecular evolution in RNA viruses: a quantitative phylogenetic analysis. Journal of molecular evolution. 2002 Feb;54(2):156-65.

Krasovec M, Rickaby RE, Filatov DA. Evolution of mutation rate in astronomically large phytoplankton populations. Genome biology and evolution. 2020 Jul 1.

Kumar S, Subramanian S. Mutation rates in mammalian genomes. Proceedings of the National Academy of Sciences. 2002 Jan 22;99(2):803-8.

Lunn D, Jackson C, Best N, Thomas A, Spiegelhalter D. The BUGS book. A Practical Introduction to Bayesian Analysis, Chapman Hall, London. 2013.

Sanjuán R, Nebot MR, Chirico N, Mansky LM, Belshaw R. Viral mutation rates. Journal of virology. 2010 Oct 1;84(19):9733-48.

Sarma A, Kay M. Prior setting in practice: Strategies and rationales used in choosing prior distributions for Bayesian analysis. InProceedings of the 2020 chi conference on human factors in computing systems 2020 Apr 21 (pp. 1-12). <a href="http://doi.org/10.1145/3313831.3376377">doi: 10.1145/3313831.3376377</a>.

