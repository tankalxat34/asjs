# asjs
Python module for implement object with syntax from JavaScript. Implementing access to keys by `obj.path.to.your.key` notation as in JavaScript

[![downloads](https://pepy.tech/badge/asjs)](https://pepy.tech/project/asjs)
[![downloads](https://pepy.tech/badge/asjs/month)](https://pepy.tech/project/asjs)
[![downloads](https://pepy.tech/badge/asjs/week)](https://pepy.tech/project/asjs)
[![supported versions](https://img.shields.io/pypi/pyversions/asjs.svg)](https://pypi.org/project/asjs)
[![pypi](https://img.shields.io/pypi/v/asjs.svg?color=success)](https://pypi.org/project/asjs/)
[![pypi](https://img.shields.io/pypi/format/asjs)](https://pypi.org/project/asjs/)
![github top language](https://img.shields.io/github/languages/top/tankalxat34/asjs)
[![github last commit](https://img.shields.io/github/last-commit/tankalxat34/asjs)](https://github.com/tankalxat34/asjs/commits/main)
[![github release date](https://img.shields.io/github/release-date/tankalxat34/asjs)](https://github.com/tankalxat34/asjs/releases)
[![github repo stars](https://img.shields.io/github/stars/tankalxat34/asjs?style=social)](https://github.com/tankalxat34/asjs)

## Installing

```
pip install asjs
```

or like this:

```
curl https://github.com/tankalxat34/pyasjs/raw/main/asjs.py -o asjs.py
```

## Using

Recommended import statement:

```py
from asjs import ObjectNotation
```

### Creating new object

Using dictionary:

```py
obj = ObjectNotation({"key1": "value1", "key2": "value2", "key3": {"a": "b", "lst": [14, 5, 6, 12]}})
```

Using arguments:

```py
obj = ObjectNotation(key1="value1", key2="value2", key3={"a": "b", "lst": [14, 5, 6, 12]})
```
### Getting values by keys or indexes
```py
>>> obj[0]
value1
>>> obj.key2
value2
>>> obj["key3"]
[14, 5, 6, 12]
```

### Creating new keys in object
```py
obj.year = 2023
```

or:

```py
>>> year = 2023
>>> obj.set(year)
```

or:

```py
>>> obj["year"] = 2023
```

or using by unexpected keys-values:

```py
>>> obj[(3, 2)] = "string_value"
```

### Saving functions in object
```py
>>> obj.fibonachi = lambda n: 1 if n <= 2 else obj.fibonachi(n - 1) + obj.fibonachi(n - 2)

>>> obj.fibonachi(7)
13
```

### Removing keys by string-names or indexes

```py
>>> del obj.year
```
or:
```py    
>>> del obj[-1]
```
or:
```py
>>> del obj["year"]
```
### Changing value by key
```py
>>> obj.key1 = 123
```
or:
```py
>>> obj["key1"] = 123
```
### Cycle `for` by object

Indexes:
```py
>>> for i in range(len(obj)):
...     print(i)
0
1
2
```

Keys:
```py
>>> for k in obj:
...     print(k)
key1
key2
key3
fibonachi
```

Values:
```py
>>> for v in obj.values():
...     print(v)
123
value2
JSObject(a: 'b', lst: JSObject(0: 14, 1: 5, 2: 6, 3: 12))
<function <lambda> at 0x0000020189F19480>
```

### Boolean statements
```py
>>> "key3" in obj
True
>>> "fake_key" in obj
False
```
#### `isArray` function
```py
>>> obj.isArray()
False
>>> obj.key3.lst.isArray()
True
```

#### `toList` function
```py
>>> obj.toList()
Traceback (most recent call last):
  ...
TypeError: Object is not be able to convert to list
>>> obj.key3.lst.toList()
[14, 5, 6, 12]
```

#### Slices
```py
>>> obj[0:3]
('value1', 'value2', <asjs.ObjectNotation object at 0x000001D7195A1990>)
>>> obj.key3.lst[0:3]
(14, 5, 6)
```