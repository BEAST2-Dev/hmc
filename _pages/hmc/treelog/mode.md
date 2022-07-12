---
layout: site
title: BEAST 2 Help Me Choose Tree log -- mode
tags: []
---

## Tree log -- mode

Logging mode, one of `autodetect`, `compound`, `tree`. For tree logs, `tree` is most appropriate.

* `autodetect` = automatically detect whether to use `compound` or `tree` mode. If there is only 1 entry and it is a tree, `tree` mode is set, otherwise `compound` mode is set.
* `compound` = compound logger that produces a tab delimited file that can be interpreted by [Tracer](https://github.com/beast-dev/tracer/releases/).
* `tree` = tree logger that produces a NEXUS tree file that can be read by DensiTree, TreeAnnotator, etc. Logging a tree in `compound` mode just logs the tree height.

See also [trace log mode](../tracelog/mode/), [screen log mode](../screenlog/mode/).