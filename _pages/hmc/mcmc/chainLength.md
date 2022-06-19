---
layout: site
title: BEAST 2 Help Me Choose MCMC chain length
tags: []
---

## MCMC chain length

Length of the MCMC chain i.e. number of samples taken in main loop. The number of samples required differs from data sets to data set and model to model. This means that the chain length needs to be determined experimentally: run an initial chain with a chain length of say 10 million -- this seems to cover most cases, but you can check the trace file part way through the run to see how the chain is behaving.

After (or during) the run, open the trace log in [Tracer](https://github.com/beast-dev/tracer/releases/) to see whether the MCMC is already through burn in: all traces should look like hairy caterpillars and there should be no trend lines. 

If the traces do not look like this, then the chain length needs to be increased. Depending on how far away the traces look from their ideal, you may increase a little (perhaps double the chain length) or increase a lot (add a zero).

Note that when changing the chain length, you might want to change the [log frequency](../tracelog/logEvery/) as well.

## Alternatives

If it turns out that ESSs never become large enough, and increasing the chain length does not help, you could consider using [Coupled MCMC](https://github.com/nicfel/CoupledMCMC) (Müller & Bouckaert, 2020) instead. 
Coupled MCMC usually mixes better, especially for poorly mixing MCMC analyses, at the cost of running extra threads.

## References

Müller NF, Bouckaert RR. Adaptive Metropolis-coupled MCMC for BEAST 2. PeerJ. 2020 Sep 16;8:e9473. <a href="http://doi.org/10.7717/peerj.9473>doi:10.7717/peerj.9473</a>.
