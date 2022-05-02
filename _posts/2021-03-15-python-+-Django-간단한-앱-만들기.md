---
title: python + Django 간단한 앱 만들기
author: 안성윤
date: 2021-03-15 13:32:00 -0500
categories: [python, django]
tags: [Web]
---

> Django 를 이용하여 간단한 앱을 만듭니다.

## 1. 앱 만들기

- django 를 설치는 [여기]() 글 참고하여 설치합니다.

```cmd
python manage.py startapp 앱이름
```

- 위 명령어는 프로젝트안에 하나의 앱을 생성하는 명령어입니다.
- App 폴더엔 migrations 폴더와 init.py, admin.py, apps.py, models.py, tests.py, views.py 가 생성됩니다.

## 2. View 작성

- polls/views.py

 ```python
from django.http import HttpResponse

# Create your views here.

def index(request):
    return HttpResponse("Hello, world. You`re at the polls index.")
 ```

- polls/urls.py(polls 에 자동 생성안되어 추가)

```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.index, name='index')
]
```

```cmd
python manage.py runserver
```

- 127.0.0.1:8000/polls 로 들어가면 view 에서 작성한 내용을 확인 할 수 있습니다.



출처 : https://www.djangoproject.com/start/

