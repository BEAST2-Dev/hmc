---
layout: site
title: BEAST 2 Help Me Choose Operator schedule -- auto optimize
tags: []
---

## Operator schedule -- auto optimize

Whether to automatically optimise operator settings.
Many operators have a coercible parameter that changes the behaviour of the operator.
For example, the Bactrian scale operator has a scale factor that when making larger increases the boldness of proposals, but decreases acceptance probability.
Decreasing the scale factor will increase acceptance probability but may result in proposals that do not make a lot change of the state space.

Every operator has a level that balances the boldness and acceptance probability, and the operator schedule keeps track of acceptance probability of operators.
This information can be used to tune the coercible parameter when `auto optimize` is enabled.

It is recommended to keep `auto optimize` set to true.
