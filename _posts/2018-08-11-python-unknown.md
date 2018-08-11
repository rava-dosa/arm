---
layout: post
title: Monologue on python
subtitle: The python you might not know
tags: [software, python]
---

![Python](https://www.python.org/static/community_logos/python-logo-master-v3-TM.png){:class="img-responsive"}

### Different type of python
Some notable mention wrt linux:  
* Cpython -> CPython is the original Python implementation
* PyPy -> A fast python implementation with a JIT compiler
* Jython -> Python running on the Java Virtual Machine
### Some less known data structure
#### ChainMap
The ChainMap class manages a sequence of dictionaries, and searches through them in the order they are given to find values associated with keys

```python
import collections

a = {'a': 'A', 'c': 'C'}
b = {'b': 'B', 'c': 'D'}

m = collections.ChainMap(a, b)
```
