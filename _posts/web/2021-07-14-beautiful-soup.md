크롤링 2가지가 중요
1. 요청하는 것 코드단에서
2. 요청되어서 가지고 온 html들 중에서 내가 원하는 정보 작 속아내는 것!


```py
import requests
from bs4 import BeautifulSoup

# header 코드 단 기본적 요청 막아둔 사이트 많음 그래서 마치 브라우저에서 엔터 친것 같은 효과 줄 수 있게 함!
headers = {'User-Agent' : 'Mozilla/5.0 (Windows NT 10.0; Win64; x64)AppleWebKit/537.36 (KHTML, like Gecko) Chrome/73.0.3683.86 Safari/537.36'}

data = requests.get('https://movie.naver.com/movie/sdb/rank/rmovie.nhn?sel=pnt&date=20200303',headers=headers)

soup = BeautifulSoup(data.text, 'html.parser')

# 코딩 시작

# selector로 속아낸 것임!
# 한가지의 값만 보고 싶을 때는  select_one
title =soup.select_one('#old_content > table > tbody > tr:nth-child(2) > td.title > div > a')

print(title)
# 결과 값
# <a href="/movie/bi/mi/basic.nhn?code=171539" title="그린 북">그린 북</a>

print(title.text)
# 결과 값
# 그린 북

print(title['href']) #속성 가지고 오는 것!
#결과값
#/movie/bi/mi/basic.nhn?code=171539


# 여러개의 값 결과값 리스트로 나옴!
trs = soup.select('#old_content > table > tbody > tr')
# 뽑아내려는 것들의 공통점을 찾아서 넣기


for tr in trs:
    a_tag = tr.select_one('td.title > div > a')
    if a_tag is not None:   # 사이트 마다 다르므로 전략을 다르게 해야 함!
        title = a_tag.text
        print(title)

```
크롤링 하나 더 추가한 것~
meta태그 중에서 속성이 해당 하는 것을 가져와라~
meta['속성쓰기!!!']
![meta](/assets/images/metatag.PNG)

```py
import requests
from bs4 import BeautifulSoup

url = 'https://movie.naver.com/movie/bi/mi/basic.nhn?code=171539'

headers = {'User-Agent' : 'Mozilla/5.0 (Windows NT 10.0; Win64; x64)AppleWebKit/537.36 (KHTML, like Gecko) Chrome/73.0.3683.86 Safari/537.36'}
data = requests.get(url,headers=headers)

soup = BeautifulSoup(data.text, 'html.parser')

# 여기에 코딩을 해서 meta tag를 먼저 가져와보겠습니다.

title = soup.select_one('meta[property="og:title"]')['content']
image = soup.select_one('meta[property="og:image"]')['content']
desc = soup.select_one('meta[property="og:description"]')['content']

print(title, image, desc)





```