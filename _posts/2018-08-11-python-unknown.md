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
This part of the blog is taken from PyMotw
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

#### Counter
A Counter is a container that keeps track of how many times equivalent values are added.

{% highlight python linenos %}
import collections

c = collections.Counter()
print('Initial :', c)
c.update('apoorvakumarhseenvaramuk')
print('Sequence:', c)
c.update({'a': 1, 'd': 5})
print('Dict    :', c)
print('Most common:')
for letter, count in c.most_common(3):
    print('{}: {}'.format(letter, count))
c1 = collections.Counter('aaaaaaassddbcpoerqw')
print(c1 + c)
print(c1 - c)
print(c1 & c)
print(c1 | c2)

{% endhighlight %}

#### DefaultDict
The standard dictionary includes the method setdefault() for retrieving a value and establishing a default if the value does not exist. By contrast, defaultdict lets the caller specify the default up front when the container is initialized.

{% highlight python linenos %}
import collections


def default_factory():
    return 'default value'


d = collections.defaultdict(default_factory, foo='bar')
print('d:', d)
print('foo =>', d['foo'])
print('bar =>', d['bar'])

{% endhighlight %}

#### NamedTuple
The standard tuple uses numerical indexes to access its members. Similar to C structure.

{% highlight python linenos %}

import collections

Person = collections.namedtuple('Person', 'name age')

bob = Person(name='Bob', age=30)
print('\nRepresentation:', bob)

jane = Person(name='Jane', age=29)
print('\nField by name:', jane.name)

print('\nFields by index:')
for p in [bob, jane]:
    print('{} is {} years old'.format(*p))

{% endhighlight %}

It's immutable. 

{% highlight python linenos %}

import collections

Person = collections.namedtuple('Person', 'name age')

bob = Person(name='Bob', age=30)
print('Representation:', bob)
print('As Dictionary:', bob._asdict())

{% endhighlight %}

#### [Some more detail about collection](https://pymotw.com/3/collections/abc.html)
### Itertools

