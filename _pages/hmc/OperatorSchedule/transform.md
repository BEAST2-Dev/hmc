---
layout: site
title: BEAST 2 Help Me Choose Operator schedule --- transform
tags: []
---

## Operator schedule -- transform

This determine the transformation used when optimisation coercible parameters of operators. 
Let \\(c\\) be the number of times the operator schedule selected an operator to optimise.
The coercible parameters is updated with a weight proportional to \\(1/c\\), if transform is `none`, \\(1/\log(c)\\) if transform is `log` and \\(1/\sqrt(c)\\) if transform is `sqrt`.

To guarantee auto optimisation stops changing the operators, `sqrt` and `log` should not be used (page 66-69, Fagundes De Carvalho, 2018).



## References

Fagundes De Carvalho LM. Statistical approaches to viral phylodynamics (Doctoral dissertation, University of Edinburgh). 2018. <a href="http://hdl.handle.net/1842/35510">online</a>.
