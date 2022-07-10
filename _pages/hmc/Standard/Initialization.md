---
layout: site
title: BEAST 2 Help Me Choose Standard template -- initialization panel
tags: []
---

## Standard template -- initialization panel

The initialisation panel allows you to set starting values for all state nodes, usually parameters and the tree.

For parameters, the `lower` and `upper` bounds can be defined.
Lower and upper bounds are usually provided through the BEAUti template and have sensible values most of the time.

The `value` entry can be used to provide a sensible starting value.

The `dimension` entry determines the dimension of the parameter, which is most often 1, but for frequencies it is 4 for nucleotide data, and 20 for amino acid data.

The `minor-dimension` entry is used for two-dimensional parameters and specifies the size of the minor dimension. 
A minor dimension of 1 indicates it is just an array.
This entry can usually be left to its default value.

The `estimate` should be left checked. 
If not checked, the parameter is removed from the state and will be kept constant throughout the MCMC.

See also [starting tree panel](/Standard/Starting_tree/) for alternative ways to initialis the tree.