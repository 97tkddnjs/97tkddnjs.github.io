---
title: "pandas의 Object 데이터 생성 및 접근"
permalink: /categories/Pandas/

toc: true
toc_sticky: true
toc_label: 목차


layout: category
author_profile: true
taxonomy: Pandas


---
## 판다스 object 데이터 생성하기 
 먼저 Pandas를 사용하기 위해서는 pandas모듈과 numpy를 import해야 한다.

 ```python
import pandas as pd
import numpy as np 
 ```

## Pandas의 자료구조 Series, DataFrame
판다스는 <strong>Series</strong>와 <strong>DataFrame</strong> 이라는 2가지 중요한 객체를 가지고 있다!

* Series는 일련의 데이터 열을 즉, 1차원 배열을 생각하면 쉽다.
* DataFrame은 행렬을 구성한다고 생각하면 쉽다.

### Series

Series는 <strong>순차적으로 나열된 1차원 배열의 형태</strong>를 갖는다.<br>
또한 Series는 <strong>index와 value값이 일대일 대응</strong>을 이룬다<br>
이러한 점에서 python의 dictionary와 유사한 점을 보인다.<br>
또한 Series는 본질적으로 DataFrame의 단일 열이라고 볼수 있다.

![Series](/assets/images/pandas/Series.PNG)

### Series 생성하기

리스트와 튜플로 Series 생성하기
``` py
data =[1,3,5,7,9]  #list
s = pd.Series(data) #index없을 시 default로 0부터 자동할당
s = pd.Series(data, index=['a','b','c','d','e'],
                name ="First Series")
#이렇게 index와 Series 전체이름을 줄 수 있다.
#한편 name != 열 이름 
'''
두번째  s의 결과 값
a    1
b    3
c    5
d    7
e    9
Name: First Series, dtype: int64
'''
data =(1,2,3,4,5) #tuple
s = pd.Series(data) #index없을 시 0부터 자동할당
s = pd.Series(data, index=['a','b','c','d','e'],
                name ="First Series")

'''
a    1
b    2
c    3
d    4
e    5
Name: First Series, dtype: int64
'''
```

딕셔너리로 Series 생성하기

```py
data ={'a':1,'b':3,'c':5,'d':7,'e':9}
s =pd.Series(data)
'''
s의 결과값
a    1
b    3
c    5
d    7
e    9
dtype: int64
'''
```
### Series data에 접근하기
데이터 값을 읽기 위해서는 인덱스에 대해 알아야 한다.<br>
인덱스는 <strong>위치인덱스</strong>와 <strong>인덱스명</strong> 2가지로 분리된다.<br>

![SeriesIdx](/assets/images/pandas/Series_idx.PNG)

그래서 접근을 할때는 인덱스명이 존재하지 않을 때는 위치 인덱스로
인덱스명이 존재할 때는 위치인덱스 혹은 인덱스명으로 접근한다!

<strong>접근방법</strong>
<br><strong>위치 인덱스</strong>는 <strong>[]안에 숫자를 넣어</strong> data에 접근하고
<strong>인덱스명은 []안에 이름을 넣어</strong> data에 접근한다.

```py
alphabet ={'a':10, 'b':20 ,'c':30,'d':40,'e':50,'f':60}
data = pd.Series(alphabet)
print(data[0] , data['a']) #결과값은 둘다 10으로 동일
```
```py
#다중 접근
#대괄호([])안에 리스트 형태로 입력시 짝을 이루는 데이터 모두 반환
>>> data[[0,3]]
'''
a    10
d    40
dtype: int64
'''
>>> data[0:3] #위치 인덱스 슬라이싱 하듯이 사용가능
a    10
b    20
c    30
dtype: int64

# 인덱스명인 경우
>>> data[['a','c']]
a    10
c    30
dtype: int64
>>> data['a':'c']
a    10
b    20
c    30
dtype: int64
```

## DataFrame
