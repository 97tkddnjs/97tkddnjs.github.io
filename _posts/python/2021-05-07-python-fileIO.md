---
title:  "Python File I/O"
excerpt: "파이썬의 파일 입출력!"

toc: true
toc_sticky: true
toc_label: 목차

comments : true

categories:
  - Python
  
last_modified_at: 2021-05-07
---

# 파일 입출력.

이번에는 파일을 통한 입출력에 대해서 알아보도록 하겠다.

## 1. 파일 열고 쓰기
파일을 생성하기 위해서는 파이썬 내장 함수 open을 사용한다.
open을 통해서 파이썬은 파일 핸들러를 만들어 준다.
<strong>open("파일 이름", "파일 열기 모드")</strong> 함수는 이와 같이 사용한다.

## 파일 생성하기

```py

# 구체적 경로 지정했을 시
f1 = open("C:/~구체적 경로~~/text.txt" 'w')
f1.close()

# 구체적 경로 지정 안했을 시 파이썬이 저장된 폴더에 저장 
f2 = open("text.txt",'w')   
f2.close()  #파일 객체를 닫아주는 역할
```
파일 열기 모드는  다음과 같다

<table>
    <tr>
        <td><strong> r </strong></td>
        <td><strong> 읽기 모드. 스트림은 파일의 시작 부분  </strong></td>
    </tr>
     <tr>
        <td><strong> r+ </strong></td>
        <td><strong> 읽기 및 쓰기 모드. 스트림은 파일의 시작 부분 </strong></td>
    </tr>
     <tr>
        <td><strong> w </strong></td>
        <td><strong> 쓰기 모드  파일의 길이를 0으로 줄이거나 없으면 만들음 스트림은 파일의 시작부분에 위치</strong></td>
    </tr>
      <tr>
        <td><strong> w+ </strong></td>
        <td><strong> 쓰기 모드  파일이 없으면 만들음 파일이 존재할 시 기존 파일 제거 스트림은 파일의 시작부분에 위치</strong></td>
    </tr>
     <tr>
        <td><strong> a </strong></td>
        <td><strong> 쓰기 모드, 파일이 없으면 생성된다. 스트림은 파일의 끝에 위치 쓰기는 항상 현재 파일의 끝에서 발생</strong></td>
    </tr>
        <tr>
        <td><strong> a+ </strong></td>
        <td><strong> 읽기 및 쓰기 모드 파일이 없으면 생성된다. 스트림은 파일의 끝에 위치 쓰기는 항상 현재 파일의 끝에서 발생</strong></td>
    </tr>
</table>

한편 <strong>close()</strong>는 열려 있는 파일 객체를 닫아 주는 역할을 한다. 파이썬은 프로그램을 종료할 때 열려 있는 파일의 객체를
자동으로 닫아주지만 <strong>close()</strong>를 통해 닫는 것이 안정성 측면에서 좋다.

## 파일 쓰기 모드

파일 쓰기는 위에서 보인 봐와 같이 w모드 혹은 a 모드를 이용해서 파일로 데이터를 읽어 들인 후
<strong>write()</strong>함수를 통해 쓰게 된다. 그리고 데이터들은 문자열들을 입력하게 된다.

```py 
>>> f= open("NewCsv.csv",'w')
>>> a=['1','2','3','4','5']
>>> for data in a:
	f.write(data)

	
1
1
1
1
1
>>> f.close()

>>> a=['1\n','2\n','3\n','4\n','5\n']
>>> f = open("NewCsv.csv",'a+')
>>> for i in a:
	f.write(i)

	
2
2
2
2
2
>>> f.close()

#이렇게 writelines(문자열 리스트)를 통해 
# 개행을 통해 파일을 가져올 수도 있다.
lines = ['안녕\n', 'Hello\n', 'Hi~\n']  #개행 필수

# hello.txt 파일을 쓰기 모드(w)로 열기
with open('hello.txt', 'w') as file:  
    file.writelines(lines)


#hello.txt
안녕
Hello
Hi~
```

# 파일 읽어들이기!

텍스트 파일 핸들러는 TextIOWrapper 클래스의 인스턴스로 파일 입출력을 담당하는 API를 제공한다.
파일을 읽기 위한 메소드는 다음과 같다.

1. read / read(n) : 파일의 전체 내용 읽어 들이기 / n개의 내용만 읽어들이기
2. readline() : 파일에서 한 줄만 읽어들인다.
3. readlines() : 파일 전체의 내용을 읽은 후 각 행으로 나뉘어진 리스트를 반환한다.















