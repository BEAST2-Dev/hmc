---
layout: site
title: BEAST 2 Help Me Choose Trace log -- sanitise headers
tags: []
---

## Trace log -- sanitise headers

BEAUti introduces some clutter in parameter names to identify whether parameters are part of the site model, clock model or tree model (of the form `param.s:partition`, `param.c:partition`, and `param.t:partiation` respectively).
When `sanitiseHeaders` is set to true for trace logs, this removes that clutter from the header of a log file.
The parameter names in shown in [Tracer](https://github.com/beast-dev/tracer/releases/) will look a bit nicer  when `sanitiseHeaders` is set to true, so this is recommended for trace logs.


See also [tree log sanitise headers](../treelog/sanitiseHeaders/), [screen log sanitise headers](../screenlog/sanitiseHeaders/).