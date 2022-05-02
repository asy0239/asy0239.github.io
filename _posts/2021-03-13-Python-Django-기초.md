---
title: Python + Django 기초
author: asy
date: 2021-03-13 17:32:00 -0500
categories: [python, django]
tags: [Web]

---

> 이번 포스팅은 Django 의 기초를 정리해봅니다.

## 1. django 기초 및 설치

- django 를 설치하면서 기초적인 내용을 정리합니다.
- django 는 python 을 기초로 하기 때문에 python 을 미리 설치하고 진행해야합니다.
- 이번 포스팅은 python 이 설치되어 있다는 것을 전제로 진행합니다.

### 1. 1 django 설치

```cmd
python -m pip install Django
```

### 1.2 프로젝트 만들기

- 하나의 앱을 만들기 위한 폴더를 생성한다고 생각할 수 있습니다.
- 명령어를 입력하면 기본적인 세팅 파일들이 생성됩니다.
- 명령어는 cmd 창에서 현재 위치한 곳에 폴더가 생성됩니다.

```cmd
django-admin startproject 폴더명(프로젝트명)
```

### 1.3 생성된 파일 정리

- manage.py : django 의 서버를 운영하는 중심적인 역할, main 클래스
- setting.py : django 의 다양한 설정을 코드화하여 보여줍니다. SECRET_KEY, TEMPLATES, DB 정보 등 여러 설정들을 관리 및 저장합니다.
- url.py : url 관련된 모든 활동을 정리합니다. 예를 들면 어느 Url 이 들어왔을 때 어디로 보내주는지 정리해놓습니다.

## 2. 프로젝트 실행하기

- 위에서 설치한 내용으로 프로젝트를 실행할 수 있습니다.

```cmd
python manage.pu runserver
```

- 기본적인 설치만 진행 후 runserver 하면 django 화면이 뜨면 성공적으로 장고가 설치되었습니다.

출처 : https://www.djangoproject.com/start/