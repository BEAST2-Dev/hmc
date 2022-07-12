---
layout: site
title: BEAST 2 Help Me Choose Cluster tree -- cluster type
tags: []
---

## Cluster tree -- cluster type

This it the type of [hierarchical clustering](https://en.wikipedia.org/wiki/Hierarchical_clustering) algorithm used for generating initial tree. 
Should be one of 

* `single` single linke clustering
* `average` average link clustering
* `complete` complete link clustering
* `upgma` unweighted pair group method with arithmetic mean ([UPGMA](https://en.wikipedia.org/wiki/UPGMA)), equals average link clustering
* `mean` mean link clustering
* `centroid` centroid link clustering
* `ward` measures increase in variance
* `adjcomplete` adjusted complete link
* `neighborjoining` [neighbour joining](https://en.wikipedia.org/wiki/Neighbor_joining) algorithm
* `neighborjoining2` corrects tree for tip data, unlike plain neighborjoining 

The default `average` is the same as `upgma`.


See also [hierarchical clustering](https://en.wikipedia.org/wiki/Hierarchical_clustering), 
[UPGMA](https://en.wikipedia.org/wiki/UPGMA), 
[neighbour joining](https://en.wikipedia.org/wiki/Neighbor_joining).