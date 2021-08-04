---
title : "django 시작"
excerpt: "django로 웹사이트 만드릭 시작!"

toc: true
toc_sticky: true
toc_label: 목차


comments: true

categories :
    -djnago
tags:
    -django
last_modified_at: 2021-07-22
---

1.장고 웹사이트 실행하면 그 웹사이트의 config/url ->에서 부터 정보를 찾기 시작함
2.장고 새로운 앱을 만들게 되면 config/setting.py의 INSTALLED_APPS항목에 해당 app추가 필요(ex. pybo/apps.py)<-없으면 테이블 못 만듬...
3.django의 모델은 앱에 종속 -> 즉, 장고에 앱을 등록해야 테이블 작업 진행 가능!

4.모델이 생성 변경되면(속성이 변경되는 경우를 말함!)
python manage.py makemigrations(장고가 테이블 작업을 수행하기 위한 파일들을 생성) 후 
python manage.py migrate 명령(실제 테이블 생성 명령!)


장고는 모델로 데이터를 관리한다.
(보통 sql에 대한 학습이 필요하지만 장고는 필요X ORM이란 것을 통해서 파이썬으로 작업을 하게 해줌!)



