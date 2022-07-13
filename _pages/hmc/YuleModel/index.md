---
layout: site
title: BEAST 2 Help Me Choose Yule model
tags: []
---

## Yule model

The Yule model is a pure birth model (i.e. no deaths or tip sampling) that can be used as tree prior for taxon sets that are all sampled at the same time.

## Tip dates

The model assumes all tips are sampled at the same time (i.e. no tip dates).
If you have tip dates, consider a birth death sampling prior or coalescent tree prior instead.

## Parameters

It has a single parameter, the birth rate, which is usually estimated and requires a [hyper prior](../../Priors/YuleBirthRatePrior/).


## Calibrations

If you have calibrations, consider the [calibrated Yule model](../../CalibratedYuleModel/) instead.

