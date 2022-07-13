---
layout: site
title: BEAST 2 Help Me Choose EBSP logger -- file name
tags: []
---

## EBSP logger -- file name

Name of the file, or stdout if left blank.
File names can be parameterised, and there are a few build-in parameters: 

* `$(filebase)` is replaced by the XML file name minus `.xml`
* `$(seed)` is replaced by the random number seed

So, if you set the file name to `$(filebase)-$(seed).log` and use a file `beast.xml` with seed `123` it saves the trace log in `beast-123.log`.

You can also define your own parameters, and run BEAST with the `-D` option to define the parameter.
For instance, setting the file name to `$(filebase)-$(run).log` and running BEAST with 

```
beast -D run=7 beast.xml
```

results in the trace file being written in `beast-7.log`.

See also [tree file name](../../treelog/fileName/).
