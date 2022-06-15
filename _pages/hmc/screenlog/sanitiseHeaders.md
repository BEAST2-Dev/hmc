---
layout: site
title: BEAST 2 Help Me Choose screenlog sanitise headers
tags: []
---

## Screen log sanitise headers


BEAUti introduces some clutter in parameter names to identify whether parameters are part of the site model, clock model or tree model (of the form `param.s:partition`, `param.c:partition`, and `param.t:partiation` respectively).
When `sanitiseHeaders` is set to true this clutter is removed from the header of the log.
Since screen logs usually do not contain parameters with partition information it usually does not have much impact whether it is set to true or not.

See also [trace log sanitise headers](../tracelog/sanitiseHeaders/), [tree log sanitise headers](../treelog/sanitiseHeaders/).