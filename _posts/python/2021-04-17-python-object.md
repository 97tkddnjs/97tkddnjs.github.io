---
title:  "Python object"
excerpt: "파이썬의 모든 것은 객체이다!"

toc: true
toc_sticky: true
toc_label: 목차

comments : true

categories:
  - Python
  
last_modified_at: 2021-04-17
---
<style>
    .tt {
        font-size : 30px;
        color : blue;
    }
</style>

## 객체(object)란 무엇일까?

[파이썬 용어집](https://docs.python.org/ko/3/glossary.html)에 따르면 객체란   

**Object**

```
Any data with state (attributes or value) and defined behavior (methods).    
Also the ultimate base class of any new-style class.
```

즉, 파이썬의 모든 것들(자료형 함수 ,...)은 **여러 속성**과 **행동**을   
가지고 있는 데이터라는 것이다.

몇 가지 코드를 한 번 확인해보겠다.
```py
>>> data = 3
>>> type(data)
#<class 'int'>

>>> dir(data)	#객체 안의 이름들을 모두 보여라
['__abs__', '__add__', '__and__', '__bool__', '__ceil__', '__class__', '__delattr__', '__dir__', '__divmod__', '__doc__', '__eq__', '__float__', '__floor__', '__floordiv__', '__format__', '__ge__', '__getattribute__', '__getnewargs__', '__gt__', '__hash__', '__index__', '__init__', '__init_subclass__', '__int__', '__invert__', '__le__', '__lshift__', '__lt__', '__mod__', '__mul__', '__ne__', '__neg__', '__new__', '__or__', '__pos__', '__pow__', '__radd__', '__rand__', '__rdivmod__', '__reduce__', '__reduce_ex__', '__repr__', '__rfloordiv__', '__rlshift__', '__rmod__', '__rmul__', '__ror__', '__round__', '__rpow__', '__rrshift__', '__rshift__', '__rsub__', '__rtruediv__', '__rxor__', '__setattr__', '__sizeof__', '__str__', '__sub__', '__subclasshook__', '__truediv__', '__trunc__', '__xor__', 'as_integer_ratio', 'bit_length', 'conjugate', 'denominator', 'from_bytes', 'imag', 'numerator', 'real', 'to_bytes']

>>> data = 'str'
>>> type(data)
#<class 'str'>
>>> dir(data)
['__add__', '__class__', '__contains__', '__delattr__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__getnewargs__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__iter__', '__le__', '__len__', '__lt__', '__mod__', '__mul__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__rmod__', '__rmul__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', 'capitalize', 'casefold', 'center', 'count', 'encode', 'endswith', 'expandtabs', 'find', 'format', 'format_map', 'index', 'isalnum', 'isalpha', 'isascii', 'isdecimal', 'isdigit', 'isidentifier', 'islower', 'isnumeric', 'isprintable', 'isspace', 'istitle', 'isupper', 'join', 'ljust', 'lower', 'lstrip', 'maketrans', 'partition', 'replace', 'rfind', 'rindex', 'rjust', 'rpartition', 'rsplit', 'rstrip', 'split', 'splitlines', 'startswith', 'strip', 'swapcase', 'title', 'translate', 'upper', 'zfill']


>>> def func():
	pass

>>> type(func)
#<class 'function'>
>>> dir(func)
['__annotations__', '__call__', '__class__', '__closure__', '__code__', '__defaults__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__get__', '__getattribute__', '__globals__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__kwdefaults__', '__le__', '__lt__', '__module__', '__name__', '__ne__', '__new__', '__qualname__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__']

```
이 코드들을 통해 우리가 파이썬의 모든 것은 객체임을 알 수 있다. 심지어 함수조차도 파이썬에서는  하나의 객체로 취급을 한다.

## 객체 지향 프로그래밍

