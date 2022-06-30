---
layout: site
title: BEAST 2 Help Me Choose SampleOffValues operator
tags: []
---

## SampleOffValues operator

Sample values from a distribution

## `values` (RealParameter): 

Vector of target values (required)

## `indicators` (BooleanParameter): 

Sample only entries which are 'off' (optional)

## `dist` (ParametricDistribution)

Distribution to sample from. (required)

## `all` (Boolean)

If true, sample all off values in one go. (optional, default: false)

## weight (Double)

Weight with which this operator is selected (required)


