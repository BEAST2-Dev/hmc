---
layout: site
title: BEAST 2 Help Me Choose Bit Flip Operator
tags: []
---

## Bit Flip Operator

Flip one bit in an array of boolean bits. 
The hastings ratio is designed so that all subsets of vectors with the same number of 'on' bits are equiprobable.

## `uniform` (Boolean)

When on, total probability of combinations with k 'on' bits is equal. Otherwise uniform on all combinations (default true).

## `parameter` (BooleanParameter)

The parameter to operate a flip on. (required)

## `weight` (Double)

Weight with which this operator is selected (required)

