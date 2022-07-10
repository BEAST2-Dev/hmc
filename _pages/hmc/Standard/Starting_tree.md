---
layout: site
title: BEAST 2 Help Me Choose Standard template --starting tree panel
tags: []
---

## Standard template -- starting tree panel

There are three types of starting trees available for standard analyses:

* random trees
* cluster trees, e.g. UPGMA, or neighbour joining
* fixed trees

In theory, MCMC will traverse state space and settle in the area with most posterior support. 
For this reason, random starting trees should be sufficient and they are preferred, because fixed starting points could result in allowing the MCMC to explore only part of the state space.
With fixed starting trees, multiple MCMC analyses may end up in the same local optimum, and we will not be able to diagnose this from the resulting posteriors.

However, the period of burn in can take a long time when there are many taxa and a fixed starting tree that can be expected to be reasonably close to the posterior may be a good option to reduce burn in.
A cluster tree based on the sequence data or a fixed tree obtained from another external analysis (e.g. maximum likelihood) could provide such a starting tree.

Of course, if you are not interested in estimating the tree but want to do an analysis on a predefined topology, use the fixed starting tree to specify that topology.

## Random trees

There are a number of ways to generate a random tree:

* `RandomTree` generates a tree based on the coalescent, and requires specifying a population size. It works well, but sometimes gets confused when there are many monophyletic constraints
* `SimpleRandomTree` ([BEASTLabs](https://github.com/BEAST2-Dev/BEASTLabs/)) produces random trees where branch lengths are drawn from an exponential distribution. It tends to be a bit more robust than `RandomTree` when there are many constraints.
* `ConstrainedRandomTree` ([BEASTLabs](https://github.com/BEAST2-Dev/BEASTLabs/)) can deal with `MultiMonophyleticConstraint`, which allows specifying many monophyletic constraints through a single (non-binary) tree specified in Newick format. This variante is coalescent based.
* `SimpleConstrainedRandomTree` ([BEASTLabs](https://github.com/BEAST2-Dev/BEASTLabs/)) is the simpler variant of `ConstrainedRandomTree` that knows how to deal with a `MultiMonophyleticConstraint`.

## Cluster trees

`ClusterTree` can be used to generate UPGMA or neighbour joining trees, but has many other options as well.

`ConstrainedClusterTree` ([BEASTLabs](https://github.com/BEAST2-Dev/BEASTLabs/)) can deal with `MultiMonophyleticConstraint`.

## Fixed trees

A tree obtained from another analysis can be entered as a tree in Newick format using a `NewickTree`.
There are a few options to manipulate this tree, for example, so that it has the right scale.
