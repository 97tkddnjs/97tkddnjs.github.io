---
title:  "Python decorator"
excerpt: "파이썬의 decorator"

toc: true
toc_sticky: true
toc_label: 목차

comments : true

categories:
  - Python
  
last_modified_at: 2021-05-15
---
## 데코레이터란?

파이썬은 데코레이터라는 기능을 제공하는 데
데코레이터는 꾸며주는(덧붙여주는) 역할을 하는 함수 또는 클래스이다.
즉, <strong>함수에 추가 기능을 구현할 때 사용</strong>을 하게 된다.

```py
#데코레이터 간단한 예제

def deco(func):
    def f():
        print("==========")
        func()
        print("==========")
    return f


def hiFunc():
    print("hi~")


>>> deco(hiFunc)()
'''결과 값
==========
hi~
==========
'''
```
## @을 이용한 데코레이터
데코레이터는 보통 <strong>@wrapper 문법</strong>을 사용한 함수 변환으로 적용된다.

```py
# 위의 예제를 간단히 바꿔보면

def deco(func):
    def f():
        print("==========")
        func()
        print("==========")
    return f

@deco   #단순히 이 코드 한줄로 데코레이터를 실현한다.
def hiFunc():
    print("hi~")

>>> hiFunc()
'''결과 값
==========
hi~
==========
'''
```

## 매개변수가 있는 데코레이터

매개변수가 있는 데코레이터를 살펴보기 전에 <strong>매개변수와 반환값을 가진
함수의 데코레이터</strong> 방법부터 살펴보도록 하겠다.

```py
def add_deco(func):
    def f(*args): #함수 선언시 매개변수에 * -> 튜플로 묶겠다.(패킹)
        print(*args, sep='+',end='') #함수 호출시 인자에 * ->언패킹
        print('={0}'.format(func(*args)))
    return f

@add_deco
def add(a, b):
    return a+b

>>> add(4,5)
4+5=9
```

매개변수가 있는 데코레이터를 만드는 방법은 다음과 같다.
```py
def mul_add_deco(val):
    def add_deco(func):
        def f(*args): #함수 선언시 매개변수에 *->튜플로 묶겠다.(패킹)
            res =(func(*args))*val
            print(val,"*",end='')
            print('(',end='')
            print(*args,sep='+',end='')
            print(') =',res)
        return f
    return add_deco

@mul_add_deco(4)
def add(a, b):
    return a+b

>>> add(4,5)
4 *(4+5) = 160
```

## static method를 만드는 데코레이터
static 메소드느 인스턴스 메소드와 다르게 첫번째 인자로 self를 전달받지 않는다.
```py

```