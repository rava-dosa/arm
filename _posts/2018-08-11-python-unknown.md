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

{% highlight python linenos %}
import collections

a = {1: 10, 2: 20}
b = {3: 30, 4: 40, 2:200}

m1 = collections.ChainMap(a, b)
m2 = collections.ChainMap(b, a)
print(m1[2],end=" ")
print(m2[2],end="\n")
print(list(m1.keys()))
print(list(m1.values()))
for k, v in m1.items():
    print('{} = {}'.format(k, v))
m1.maps = list(reversed(m1.maps))
print('m1 = {}'.format(m1[2]))
a[5]=50
print(m1[5])
m3 = m1.new_child()
m3[2] = 2000
m3[10] = 209
{% endhighlight %}
