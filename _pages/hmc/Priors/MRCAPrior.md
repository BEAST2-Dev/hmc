---
layout: site
title: BEAST 2 Help Me Choose MRCA prior
tags: []
---

## MRCA prior

This is a prior on the most recent common ancestor (MRCA) of a set of taxa.

## Adding MRCA priors

* In the priors panel, click the `+ Add Prior` button at the bottom of the list.
* If you have packages installed with other priors, possibly a dialog is shown where you can choose the type of prior: select `MRCA Prior` from the drop down box and click `OK`.
* A dialog pops up where you can specify the taxon set by moving taxa from the list of candidates to the list of taxa and vice versa by selecting one of more taxa and use the `<<` and `>>` buttons in between the lists.
* Specify the taxon list name, say `xyz` and click the `OK` button.
* A new entry with a button labelled `xyz.prior` appears in the list of priors. Click this button if you want to change the list of taxa.
* To specify a distribution select one from the drop-down box. 
* By clicking the button with the triangle on the left hand side, the parameters of the distribution can be edited, and some other options (monophyletic, tipsonly, use originate) can be changed.

## Deleting MRCA priors

The MRCA prior can be deleted in BEAUti in the priors panel by clicking the `-` button next to the MRCA prior.

## Taxon set

Set of taxa for which prior information is available.
This can be changed by clicking the `xyz.prior` button in the list of priors in the priors panel.

## `monophyletic`

Whether the taxon set is monophyletic (forms a clade without other taxa) or nor. 
Default is false, and in this case the trace log will record when the clade is monophyletic.

## `tipsonly`

Flag to indicate tip dates are to be used instead of the MRCA node. 
If set to true, the prior is applied to the height of all tips in the taxonset and the monophyletic flag is ignored. 

## `use originate`

Use parent of clade instead of clade. 
Cannot be used with tipsonly, or on the root.

## `distribution`

Parametric distribution: distribution used to calculate prior over MRCA time, e.g. normal, beta, gamma. 
This distribution is over the age (TODO) of the MRCA node in the tree.
