---
layout: site
title: BEAST 2 Help Me Choose Standard template partitions panel
tags: []
---

## Standard template -- partitions panel

The partitions panel is where you add new alignments and other data associated with taxa.

## Add (+) button

The add button is an alternative to the items under the `File` menu and is positioned at the bottom of the list of partitions (bottom of screen).
After clicking, choose the type of partition to add -- the range of choices differs with different packages installed, and if no package is installed BEAUti assumes an alignment is added and skips this step.
Then, a file chooser dialog appears where you can select the file containing the data. 
The behaviour of BEAUti may change depending on the type of data, for example, with geography data a dialog can pop up showing how latitude and longitudes are associated with taxa.

## Delete (-) button

Select one of more partitions, then the delete button becomes enabled and clicking it removes these partitions from the analysis.
Handy when for example overlapping partitions are defined in a NEXUS file and only the non-overlapping set of partitions need to be included in the analysis.

## Replace (r) button

Select a single partition, and the replace button becomes enabled.
After clicking the button a file chooser dialog is opened that allows you to choose an alignment that will be used instead of the alignment in the partition.

Note that if trees are linked, but taxa from the replacement alignment do not match those of other alignments, this may lead to XML that cannot be run.

## Split button

The split button can be used to split an alignment on codon positions.
Splitting coding nucleotide alignments that way and using a different site model for each of them tends to improve the fit to the data (Shapiro et al, 2006).
Select one or more partitions and the split button becomes enabled. 
After clicking, BEAUti shows options on how to split.
After splitting, the tree will be shared among the new partitions.




## Link/unlink buttons

Above the list of partitions, you find buttons to link or unlink models for the different partitions. 
Select two or more partitions and the (un)link buttons become enabled.

### Link/unlink tree models buttons

Partitions should only have their trees linked if they share a common history, for example, different loci of mitochondrial dna, or a dna partition and geographical data partition.
If you have different partitions with different histories (e.g. a nuclear and a mitochondrial gene) you should consider using a multi species coalescent methods like [StarBeast3](https://github.com/rbouckaert/starbeast3) (Jordan et al, 2022) or [snapper](https://github.com/rbouckaert/snapper) (Stolz et al, 2021).
Sharing a tree with such data can lead to biased and overconfident estimates (Ogilvie et al. 2016).

### Link/unlink clock models buttons

Do not link clocks for partitions that have different trees: only strict clock models can be shared in this case.

If partitions share a tree and have different mean rates, but can be expected to have the same rate variation on branches (e.g. different loci of mitochondrial dna), link the clock. 
Relative rates can be estimated using the substitution rate in the site model panel.

If partitions share a tree but can not be expected to have the same rate variation on branches (e.g. gene sequence partitions and a geographical location partition), unlink the clocks.

### Link/unlink site model buttons

When a single tree is used in the analysis, site models are not usually not linked.
With multiple trees, and there is an interest in one of the site model parameters, site models can be linked.

Another reason for linking site models is that a single site model can be configured in the site model panel, then unlinking all site models leaves all partitions with the same site model (another way to achieve this is by setting up the site model of the first partition in the site model panel, then clone all other partitions from the first partition).




## References

Douglas J, Jiménez-Silva CL, Bouckaert R. StarBeast3: Adaptive Parallelized Bayesian Inference under the Multispecies Coalescent. Systematic Biology. 2022 Feb 17. <a href="http://doi.org/10.1093/sysbio/syac010">doi:10.1093/sysbio/syac010</a>.

Ogilvie HA, Heled J, Xie D, Drummond AJ. Computational performance and statistical accuracy of *BEAST and comparisons with other methods. Systematic biology. 2016 May 1;65(3):381-96. <a href="http://dx.doi.org/10.1093/sysbio/syv118">doi:10.1093/sysbio/syv118</a>.

Shapiro B, Rambaut A, Drummond AJ. Choosing appropriate substitution models for the phylogenetic analysis of protein-coding sequences. Molecular biology and evolution. 2006 Jan 1;23(1):7-9. <a href="http://doi.org/10.1093/molbev/msj021">doi:10.1093/molbev/msj021</a>.

Stoltz M, Baeumer B, Bouckaert R, Fox C, Hiscott G, Bryant D. Bayesian inference of species trees using diffusion models. Systematic Biology. 2021 Jan;70(1):145-61. <a href="http://doi.org/10.1093/sysbio/syaa051">doi:10.1093/sysbio/syaa051</a>.
