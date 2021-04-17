---
title:  "iterable object iterator object"
excerpt: "iterator pattern에  대해 알아보겠다!"

toc: true
toc_sticky: true
toc_label: 목차

comments : true

categories:
  - Python
  
last_modified_at: 2021-04-17
---

## iterable 이란?

[파이썬 용어집](https://docs.python.org/ko/3/glossary.html)에 따르면 iterable이란

**iterable**

```
An object capable of returning its members one at a time. Examples of iterables   
include all sequence types (such as list, str, and tuple) and some non-sequence   
types like dict, file objects, and objects of any classes you define with an   
 __iter__() method or with a __getitem__() method that implements Sequence   
 semantics.

Iterables can be used in a for loop and in many other places where a sequence is   
needed (zip(), map(), …). When an iterable object is passed as an argument to the   
built-in function iter(), it returns an iterator for the object. This iterator is   
good for one pass over the set of values. When using iterables, it is usually not   
necessary to call iter() or deal with iterator objects yourself. The for statement   
does that automatically for you, creating a temporary unnamed variable to hold the   
iterator for the duration of the loop. See also iterator, sequence, and generator.   

```

위의 설명에서 볼 수 있듯이 **iterable object**는 member를   
**한 번에 하나씩 반환** 할 수 있는 시퀀스형들이거나 **dict같은 비시퀀스 형**들
혹은 **_iter_ ()**  나 시퀀스 개념을 구현하는 **_ _getitem_ _() 메서드**를 써서 정의한 모든 클래스의 객체들 혹은 파일 객체들을 말한다.

어떤 객체가 iterable 객체인지 확인하는 가장 쉬운 방법은 **iter()**에 전달을 하는 것이다.
* iterable object는 **iter()** 함수에 의해 **인수**로 전달되면 해당 개체에 대해 **iterator를 반환**한다.


```py
>>> f = open("c:\\ubuntu\\text.txt",'a')
>>> f.write('def')
3

>>> tmp = iter(f)       #file도 iterable임을 알 수 있다.
>>> type(tmp)
<class '_io.TextIOWrapper'>
```
```py
>>> st= "hello"
>>> iter(st)
<str_iterator object at 0x000001F74F6F6CD0>

>>> next(iter(st))
'h'
```

한편 **iterable 객체라 하더라도 반드시 iterator객체인 것은 아닌데**  iterator 설명을 하면서 해당 내용에 대해 설명하도록 하겠다.

## iterator 이란?

```
An object representing a stream of data. Repeated calls to the iterator’s __next__()   
method (or passing it to the built-in function next()) return successive items in the   
stream. When no more data are available a StopIteration exception is raised instead.   
At this point, the iterator object is exhausted and any further calls to its __next__()   
method just raise StopIteration again. Iterators are required to have an __iter__() method   
that returns the iterator object itself so every iterator is also iterable and may be used   
in most places where other iterables are accepted. One notable exception is code which   
attempts multiple iteration passes. A container object (such as a list) produces a fresh   
new iterator each time you pass it to the iter() function or use it in a for loop.   
Attempting this with an iterator will just return the same exhausted iterator object used   
in the previous iteration pass, making it appear like an empty container.

```
즉, iterator는 데이터의 스트림을 표현하는 객체이다. __next__() 메서드를 반복적으로 호출하면(혹은 내장함수 next()로 전달 ) 스트림에 있는 항목들을 차례대로 돌려준다. 더 이상의 데이터가 없을 시는 
StopIteration 예외를 일으킨다.


**iterable 객체라 하더라도 반드시 iterator객체인 것은 아니다**에 대해서 설명하도록 하겠다.
우리가 아는 list는 iterable한 객체이다. 그렇다면 list자체는 iterator일까?

```py
>>> li=[1,2,3,4,5]
>>> next(li)
'''
Traceback (most recent call last):
  File "<pyshell#39>", line 1, in <module>
    next(li)
TypeError: 'list' object is not an iterator
'''

```
위의 코드에서 볼 수 있듯이 list 자료형은 iterable 객체임에도 불구하고 next()를 실행할 수 없음을
알 수 있다 이를 통해서 알 수 있는 것은

* 모든 iterable은 항상 iterator가 되는 것은 아니다.
* <strong>"모든 iterator은 항상 iterable하다"이다.</strong>

iterator 관련 몇 가지 코드를 더 살펴 보도록 하겠다.   

* * *
우리가 흔히 사용하는 for 문장도 내부적으로는 iterator를 통해 구동을 한다.
밑에 보이는 코드가 그 예이다.

```py
>>> iterator = iter([1,2,3,4,5])
>>> while True:
	try:
		i = next(iterator)
		print(i, end = ' ')
	except StopIteration:
		print("StopIteration Occur")
		break

1 2 3 4 5 StopIteration Occur           #iter이 완료되면 exception을 발생

>>> while True:
	try:
		i = next(iterator)
		print(i, end = ' ')
	except StopIteration:
		print("StopIteration Occur")
		break

StopIteration Occur                     #내부적으로 더 꺼낼게 없다는 것

```

또한 iterator객체인지 파악하는 가장 좋은 방법은 iter 함수가 있는 지 확인하는 것이다

```py
>>> hasattr([1,2],'__iter__')
True
```