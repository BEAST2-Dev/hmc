---
layout: site
title: BEAST 2 Help Me Choose Species tree logger -- file name
tags: []
---

## Species tree logger -- file name

Name of the file, or stdout if left blank.
File names can be parameterised, and there are a few build-in parameters: 

* `$(filebase)` is replaced by the XML file name minus `.xml`
* `$(seed)` is replaced by the random number seed

So, if you set the file name to `$(filebase)-$(seed).trees` and use a file `beast.xml` with seed `123` it saves the tree log in `beast-123.trees`.

You can also define your own parameters, and run BEAST with the `-D` option to define the parameter.
For instance, setting the file name to `$(filebase)-$(run).trees` and running BEAST with 

```
beast -D run=76 beast.xml
```

results in the tree file being written in `beast-76.trees`.

See also [trace file name](../tracefile/fileName/).
