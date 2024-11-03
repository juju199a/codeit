# 2. Django 구조 이해하기
## 01. Django 강의 설명서
1. 처음부터 디테일을 추구하지 마세요

2. 조금 어렵게 느껴지는 것이 당연합니다

3. 기술에 대한 경험과 적응력 키우기

## 02. Django 프로젝트(Project) 생성하기
1. codeit-django 디렉토리 생성
  - `mkdir codeit-django`
  - `cd codeit-django`

2. 이 디렉토리에 가상환경을 제공해 준다.
  - `pyenv versions`
  - pyenv로 생성한 파이썬 환경 목록 보기
  - 우리가 만들어 둔 가상환경의 목록이 나오게 된다.
  - `pyenv local django-envs`
  - 우리는 django-envs라는 가상환경을 앞에서 생성했으니까
  - 이 명령어를 하면 로컬 가상 환경이 적용됩니다.
  - `pyenv local {가상 환경 이름}
  - 특정 디렉토리에 로컬 가상 환경 적용

3. 설치된 장고 버전 확인
  - `django-admin --version`
  - 설치된 장고 버전 확인

4. 프로젝트 생성
  - `django-admin startproject costaurant`
  - ls

5. django 개발 서버 실행
  - cd costaurant
  - code .
  - `python manage.py runserver`
  - django 개발 서버 실행

## 03. 코드잇 실행기에서 장고 실습을 한다면?
1. settings.py의 Allowed hosts 항목에 '*'을 추가해 주어야 하고
2. django의 개발 서버를 실행할 때 python manage.py runserver 뒤에 0.0.0.0:8000을 인자로 전달해 주어야 합니다.

## 04. runserver의 비밀
1. runserver

2. 왜 '개발 서버' 일까?

3. 숨어있는 IP와 Port
  - `django-admin runserver {ip:port}`
  - `python manage.py runserver {ip:port}`

## 05. Django 프로젝트 구조
1. 밖에 있는 Costaurant (프로젝트 명)
  - `Project Root`
  - django 프로젝트의 모든 파일이 담겨 있는 최상위 디렉토리
  - `이름을 마음대로 바꿔도 됨`

2. 안쪽에 있는 Costaurant (하나의 앱)
  - `Project App`
  - 하나의 장고 프로젝트는 여러개의 앱으로 구성되어 있다.
  - 그중에서 가장 중심이 되는 App 이 Project App 입니다.
  - 이름을 바꾸면 많은 수정을 해야 함

3. manage.py
  - 우리 프로젝트의 매니저
  - Django 프로젝트 관리를 위한 `명령어를 지원`
  - 새로운 앱을 만들거나, 데이터베이스를 건들거나, 개발 서버 실행하는 등의
  - 여러 기능들을 할 수 있습니다.

4. db.sqlite3 
  - 우리 프로젝트에서 사용하는 데이터베이스 파일

5. `__init__.py`
  - 장고의 앱은 하나의 파이썬 패키지라고 할 수 있는데요.
  - 지금 보이는 프로젝트 앱 디렉토리도 하나의 앱입니다.
  - 이 디렉토리가 하나의 `파이썬 패키지`로 인정되기 위해서는 init 파일이 있어야 한다.
    - 내가 있는 디렉토리는 **Python 패키지**!
    - 사실 Python 3.3 버전 이상 부터는 이 파일이 없어도 정상 작동을 한다.
    - `하위 버전 호환`을 위해서 만들어 준다.

6. settings.py
  - 프로젝트의 시간대 설정,
  - 데이터베이스 설정
  - 여러 경로 설정 등 

7. `urls.py`
  - URL을 보고 알맞은 페이지로 연결해 주는 역할
  - 소개 요청 URL -> 소개 페이지
    - http://codeit.kr/`about` ~
  - 로그인 요청 URL -> 로그인 페이지
    - http://codeit.kr/`login` ~

8. `wsgi.py`
  - 위스키 점 파이 파일 (WebServer Gateway Interface, WSGI)
  - 웹 서버와 Python 어플리케이션인 Django가 소통하는데 필요한 일종의 `프로토콜`

## 06. Django 프로젝트 구조 정리하기
1. Django 프로젝트 생성하기
  - `django-admin startproject {프로젝트명}`
  - `django-admin startproject codeit-proj`

2. Django 프로젝트 구조
  - Project Root
  - manage.py
  - ProjectApp (Django Root)
  - __ init__.py
  - settings.py

## 07. Django 프로젝트 구조 익히기
1. `프론트엔드, 백엔드`
  - 웹 개발은 크게 보이는 화면을 담당하는 프론트엔드(Front-end)
  - 화면 뒤에서 데이터와 로직을 담당하는 백엔드(Back-end)

2. `manage.py`
  - manage.py는 Django 프로젝트를 생성하면 자동으로 생성됩니다.

3. `__init.py`
  - __init.py` 파일은 해당 파일이 있는 디렉토리가 파이썬 패키지임을 명시해주는 기능을 합니다.

4. `django-admin startproject codeit`
  - django 프로젝트 새로 만들려고 할 때 명령어
  









