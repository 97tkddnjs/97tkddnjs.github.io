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

객체(object)란 데이터와 기능이 묶인 것을 이야기한다. 이러한 객체를 이용하여 프로그래밍하는 것을 객체 지향 프로그래밍이라고 한다. 객체 지향 프로그래밍은 컴퓨터 프로그램을 객체 단위로 파악하고 각각의 객체들은 메시지를 주고받고 데이터를 처리하게 된다. 이러한 것이 기본적인 객체지향 프로그래밍의 정의이다.

```py
class Simple:
  def __init__(self):
    self.val =0
    print("hello class")

>>> sc =Simple()
hello class
>>> sc.val
0
```
보통 <strong>class</strong>라는 키워드를 통해 객체를 위한 설계도(틀)를 먼저 만든다.
그리고 객체는 이러한 설계도를 통해 만들어진 <strong>실체를 객체</strong>라고 부른다.


## 파이썬 객체의 특성

파이썬은 다른 객체 지향 프로그래밍과 다르게 독특한 특성이 하나 있다. 바로 변수와 메소드를 붙였다가 뗄 수 있다는 것이다.

```py
#간단한 class

class Simple:
  def getter(self):
    return self.val

>>> sc = Simple()
>>> sc.val =10
>>> sc.getter()
10

#class 변수
>>> Simple.n=3
>>> Simple.n
3


>>> type(Simple)
<class 'type'>

```

변수의 초기화는 보통 우리가 아는 __init__을 통해 미리 정의 시키고 초기화 하는 것을 생각할 수가 있다.
하지만 <strong>python은 위에 보이는 코드처럼 새로운 변수를 생성해서 넣을 수도 있다.</strong> 이는 우리가 아는 보통의 객체 지향 프로그래밍과
다른 독특한 특징이므로 반드시 알아둬야 한다! 또한 클래스에도 변수를 추가할 수 있다. 이는 <strong>우리가 만든 클래스 자체도 type이라는
클래스의 객체이기 때문이다.</strong> type은 메타 클래스라고 하는 것인데 이것은 굉장히 심오한 개념이라 넘어가겠다...

```py
>>> def deco(func):
    def f():
        print("==========")
        func()
        print("==========")
    return f

>>> def hiFunc():
    print("hi~")

>>> sc.hellof=hiFunc
>>> sc.hellof()
==========
hi~
==========

```

함수 역시 추가 할 수 있다!

```py
#다음과 같은 del을 이용하여 삭제도 가능하다~

del sc.val

del sc.hellof

```