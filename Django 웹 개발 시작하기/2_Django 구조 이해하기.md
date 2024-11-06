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
  
## 08. Django 앱(App)
1. Django 앱(app)
  - 저번레슨 -> django 프로젝트(Project) 생성
  - 이번레슨 -> django 앱(App) 생성

2. 앱생성
  - `cd costaurant`
  - `python manage.py startapp foods`
  - ls

3. `__init__.py`
  - 각 장고 앱은 하나의 파이썬 패키지인데, 파이썬 패키지로 인식하기 위해 필요한 파일입니다.

4. `admin.py`
  - 이 foods 앱을 django 관리자와 연동하기 위해 필요한 설정 파일

5. `apps.py`
  - 앱에 대한 설정을 넣어 두는 파일이구요.

6. `models.py`
  - 이 앱에서 사용할 데이터 모델, 데이터 베이스 연동과 관련된 파일

7. `views.py`
  - 서버에 어떠한 요청이 들어 왔을 때, 어떻게 처리해야 할지에 대한 로직이 들어가는 파일

8. **models.py와 views.py**
  - django에서 가장 핵심이 되는 요소이기 때문에, 뒤에서 깊게 공부함

9. `test.py`
  - 프로젝트의 테스트 코드를 작성하기 위한 곳
  - 우리가 만든 웹사이트에 오류가 있는지 검사하기 위해 테스트 코드를 작성해 두는 곳입니다.

10. `migrations`
  - 데이터베이스와 연관된 것
  - 데이터베이스 구조가 계속 바뀐다.
  - 변경 사항이 생길 때 마다 히스토리가 누적이 됩니다.

11. `필수`
  - 새로운 앱을 만들었다면 장고에게 새로운 앱을 만들었다는 사실을 알려 줘야 함!
  - `costaurant/settings.py`
  - costaurant는 프로젝트 앱
  - 프로젝트 앱 안에 있는 setting.py
```
INSTALLED_APPS = [
  ...
  'foods'
]
```

## 09. Django 앱(App) 구조
1. Project와 App의 차이

2. App 생성하기
  - `python manage.py startapp foods`

3. Django App 구조
  - `admin.py`: 관리자 기능
  - `apps.py`: 각각의 App마다 추가적인 기능 및 설정
  - `migrations 디렉토리`: Djang 앱의 데이터 구조에 대한 변경 사항인 migration 파일이 저장되는 디렉토리
  - `models.py` : 데이터 구조를 정의. 데이터베이스와의 소통을 담당
  - `tests.py`: 테스트 코드
  - `views.py` : 앱에서 어떤 기능을 할지에 대한 메인 로직을 담당하는 파일

## 10. 코스토랑 프로젝트 #01 프로젝트 생성
1. 프로젝트 생성하기
  - django-admin startproject costaurant

2. 앱 생성하기
  - python manage.py startapp menu

3. 앱 등록하기
  - settings.py
```
'menu',
```
```
ALLOWED_HOSTS = ['*']
```

4. 서버 실행하기
  - python manage.py runserver
  - python manage.py runserver 0.0.0.0:8000

5. 셀프 채점
  - costaurant 프로젝트가 잘 생성되었나요?
  - costaurant 프로젝트 안에 menu앱이 생성되었나요?
  - 개발 서버를 실행하고 접속하면 Django 기본 페이지가 잘 나오나요?

## 11. Django 앱의 철학 'Reusable App'
1. 재사용성이 있는 App
  - App은 하나의 기능 단위이며, 
  - 하나의 프로젝트는 여러개의 App을 만들 수 있다.
  - Reusable한 App을 만드는 방법

2. Django 컨퍼런스
  - 한 가지 앱은 한 가지 기능을 하고, 그 기능을 잘 수행해야 한다.
  - 장고 개발자는 프로젝트를 많은 앱으로 구성한다는 것을 두려워하면 안된다.
  - 각각의 앱을 유연하게 작성해야 한다.
  - 다른 사람에게 배포가 가능하도록 만들어야 한다.
  - 우리는 앱을 나누지 않고, 앱 하나로만 쭉 연습을 할 것입니다.

## 12. Django 앱 구조 익히기
1. `python manage.py startapp coffee`

2. `틀린 것은?`
  - Django 프로젝트는 재사용성을 고려한 기능 단위이다.
  - 재사용성을 고려한 기능 단위는 앱(App)이며 하나의 프로젝는여러개의 앱으로 구성

3. `reusable`
  - reusable App: Django App이 추구해야 하는 방향성으로 재사용성을 지향해야 한다.

4. `admin`
  - 앱을 생성하면 admin.py가 자동으로 생성되며 관리자 기능을 사용하기 위한 여러가지 설정을 할 수 있습니다.

5. `models.py 옳은 것은?`
  - 데이터베이스 구조를 정의하고 데이터베이스와 소통하는데 필요한 파일

6. `view.py`
  - view.py는 앱(App)의 로직을 담당하는 파일입니다.
  - URL의 분기를 담당하는 것은 **urls.py**입니다.
  - 데이터베이스 구조를 담당하는 것은 **models.py**입니다.
  - 프로젝트와 앱의 연결은 **settings.py**에서 할 수 있습니다.

  
## 13. Hello, Django!
1. urls.py
  - USER가 URL을 입력하면, dj는 urls.py에 적혀있는 파일을 보고, 어떤 처리를 할지 결정합니다.
  - urlpatterns 라는 항목에서 URL을 어떻게 처리할 지 써 놓는 곳
  - admin 이라고 있으면, admin.site.urls 로 가라
  - codeit.kr/admin
  - `python manage.py runserver` 로 개발 서버를 켜 준다.

2. 새로운 URL처리
```py
path('foods/', include('foods.urls'))
```
  - foods 앱 안의 urls.py 파일을 살펴 봐라.
  - foods 앱 안에 urls.py 파일이 없다.
  - 그대로 복사해서, 
```py
urlpatterns = [
  path('index/', views.index)
]
```
  - foods 앱 안의 views 파일을 살펴 봐라.
  - `views 모듈`을 쓰기 위해서는 불러와야 한다.
  - `from . import views`
  - . 은 같은 디렉토리를 의미합니다.
  - `views 모듈`에서 `index 함수` 가져와라
  - 실제로 views 모듈을 보면, index 함수를 정의해 준적이 없다.
  - 우리가 만들어줘야 한다.
```py
from django.http import HttpResponse

def index(request):
  return HttpResponse("<h2>Hello, Django!</h2>")
```
  - python manage.py runserver
  - http://127.0.0.1:8000/admin

## 14. 클라이언트와 서버란?
1. URL
  - 클라이언트 -> 서버
  - bakey.codeit.kr : 도메인 (Domain)
  - /foods/index : 경로 (Path)

## 15. URL은 어떻게 연결될까?
1. dj가 가장 먼저 보는 파일은 `프로젝트 앱` 안에 있는 `urls.py`입니다.
  - 왜 그런지는 settings.py를 보면 알 수가 있다.
  - `ROOT_URLCOF = 'costaurant.urls`
  - 장고가 URL을 보고 가장 먼저 어떤 파일을 봐야 할지 설정하는 부분
  - `cosaurant 프로젝트 앱 안`에 있는 urls 를 보라고 명시되어 있습니다.

2. domain/foods/index
  - path('foods/', include('foods.urls'))
  - foods까지만 매칭이 되고, 뒤의 index는 그대로 남아 있다.
  - 뒷부분에 대해서 처리를 해 주기 위해서, 그 다음의 `foods 앱 안에 있는 urls 파일`을 봐라

3. foods/index
  - path('index/', views.index)
  - 매칭이 되면, views 모듈의 index를 가리키고 있다.

4. view.py
  - index 함수
  - 응답을 리턴한다.
  - F11 (Chrome) / F12 (Edge)

## 16. Django와 URL
1. Client와 Server의 틀린 설명
  - Django는 클라이언트-서버 구조에서 서버에 속합니다.
  - 서버는 웹페이지 뿐만 아니라 이미지나 동영상 등 여러가지 형태의 자원(Resource)를 클라이언트에게 제공할 수 있습니다.

2. url, domain
  - URL(Uniform Resource Locator)는 네트워크 상의 자원(Resource)의 위치를 나타내는 문자열 입니다.
  - Domain은 서버를 의미합니다.

3. `urls.py`
  - urls.py는 클라이언트의 요청인 URL을 보고 알맞은 로직을 제공 하기 위해 계층적으로 구성됩니다.
  - 모든 URL에 대해 분기가 끝나면 알맞은 view를 호출하여 로직을 처리합니다.

## 17. URL 연결하기
1. 변경해야 하는 파일
  - django_proj/django_proj/urls.py
  - django_proj/greetings/urls.py

2. 프로젝트 앱(django_proj)의 urls.py
```py
from django.contrib import admin
from django.urls import path,include

urlpatterns = [
  path('admin/', admin.site.urls),
  path('greetins/', include('greetings.urls'))
]
```
  - [A:greetings/] : /(경로 구분 기호)를 기준으로 URL의 앞부분인 'greeings/'와 매칭되면
  - [B:greetings.urls] : 나머지 뒤쪽 URL(hello)은 다른 URLConf 모듈인 greetings 앱의 urls에서 처리하도록 넘겨 줍니다.
3. greetings 앱의 urls.py
```py
from django.contrib import admin
from django.urls import path
from . import views

urlpatterns = [
  path('hello/', views.helloView)
]
```
  - [C:hello/]: 남아 있는 URL인 hello와 매칭되면
  - [D:views.helloView]: URL 매칭이 모두 끝났으므로 다른 urls로 연결하는 것이 아닌 view를 호출 하면 되는데, 
  - 이때 greeings 앱의 views를 보면 helloView가 정의되어 있으므로 helloView를 호출합니다.

## 18. URL 작성이 헷깔려요!
1. urls.py에 적는 URL 패턴은 슬래시(/)를 붙여서 작성합니다.

2. 다른 URL로 이동하기 위한 URL을 적을 때 앞에 슬래시(/)가 있으면 도메인으로 부터의 경로를 의미합니다.
  - <a href="/banana/">이동하기</a>
  - codeit.kr/food/banana/ 가 아닌 `code.kr/banana/`로 이동하게 됩니다.

3. 다른 URL로 이동하기 위한 URL을 적을 때 앞에 슬패시(/)가 없으면 현재 URL 뒤에 이동하는 URL이 연결된 경로가 됩니다.
  - <a href="banana/">이동하기</a>
  - codeit.kr/food/banana 로 이동하게 됩니다.

## 19. Hola!
1. /greeings/hello/
  - path('greetings/', include('greetings.urls)),
  - path('hello/', views.hello_view),

## 20. 메인페이지가 에러페이지?
1. 프로젝트 앱 아래의 urls.py
  - path('', include('foods.urls'))

## 21. Django 템플릿과 렌더링
1. 더 많은 HTML을 리턴하고 싶다면?
  - HTML 같이 화면 구성을 담당하는 것을 `Template`이라고 부르는데요.
  - 우리는 foods 앱을 작업중이니까, foods 앱 디렉토리 안에 **Template 파일들을 넣어줄 디렉토리**를 하나 만들도록 하겠습니다.
  - foods/templates 폴더를 만든다.
  - foods/templates/foods 만든다.
  - index.html : `index 템플릿`
```html
<h2>Hello, Django!</h2>
<p>Just Codeit ! </p>
<p>Just Codeit ! </p>
<p>Just Codeit ! </p>
<p>Just Codeit ! </p>
```
2. `Template을 Render 한다`
  - Template을 유저에게 보여준다.
  - render 함수를 써주고, 첫번째 파라미터로 `request`를 넘깁니다.
  - 그리고 두번째 파라미터로는 `우리가 원하는 템플릿의 경로`를 써줘야 하는데, 
  - 방금 만들어준 HTML 경로를 적으면, `foods/index.html`
  - 이 render 함수는 우리가 이렇게 넘겨준 정보와 템플릿을 토대로 **하나의 응답**
  - 즉 하나의 `HttpResponse 객체`를 만들어서 리턴해 줍니다.
```py
def index(request):
  return render(request, 'foods/index.html')

```
  - 화면 구성을 담당하는 부분: `Template`
  - Rendering(렌더링)이라는 과정을 통해서,
  - 클라이언트에게 응답으로 돌려줄 최종 형태인 `HttpResponse 객체`로 변환한다는 것을 배웠습니다.
  - 이제 우리는 유저에게 보여줄 HTML 코드를 템플릿으로 깔끔하게 정리할 수 있습니다.

## 22. render() 함수에 대해 알아보자
1. render()
  - render(request, template_name, context=None, content_type=None, status=None, using=None)

2. 필수 인자
  - request와 template_name
  - request를 넘겨주는 이유는 요청에 대한 정보에 접근해서 `user, session 등 여러 가지 기능을 구현하기 위해서`
  - template_name은 렌더링에 사용할 대상 템플릿을 명시

3. 선택 인자
  - `context`는 템플릿에 추가할 값들이 들어 있는 사전형 인자
  - `context_type`은 결과로 만들어 내는 문서의 유형을 말하며 기본값은 `text/html` 즉 HTML 웹 페이지 입니다.
  - `status`는 상태 코드(Status Code)값이며 기본값은 200(성공)입니다.
  - `using`은 템플릿을 렌더하는 템플릿 엔진을 지정할 수 있는 인자입니다.

4. 두 개의 render
  - Django Template Language를 써서 작성한 코드
  - HTML 파일을 브라우저가 읽어서 우리가 실제로 보는 이쁜 웹 페이지로 바꿔주는 과정


## 23. Django MVT 아키텍처
1. Model, View, Template

2. Model
  - 데이터 구조를 담당
  - 데이터베이스와 소통

3. Template
  - 웹 사이트의 화면 구성 담당
  - HTML, CSS, JS 로 구성한다.
  - `Template Language` : 매번 변화하는 데이터에 따라서 화면을 다르게 구성할 수 있습니다.
  - django 템플릿은 기본적인 틀은 HTML로 작성하고, 
  - 세부내용은 Template Language를 사용해서, 구현하게 됩니다.

4. View
  - 웹 사이트의 로직을 담당하는 파트
  - Model과 Template 사이를 연결하는 역할을 합니다.


5. 정리
  - URL 요청(Request)이 들어오면, URL에 가리키는 **View**를 호출합니다.
  - 호출된 View에서는 필요하다면 **Model**을 통해서 데이터베이스와 소통하며, 데이터 처리를 합니다.
  - View에서 알맞은 로직에 맞춰서 데이터를 가공한 후에
  - 이를 **Template**으로 보내고, Template에서는 데이터를 받아서, 화면을 구성하고, 
  - View에서 만들어진 화면을 클라이언트에게 응답(Response)한다.

## 24. MVC와 MVT
1. MVC 패턴
  - Model: 데이터를 저장, 보관
  - View: 사용자에게 보여지는 부분을 담당
  - Controller: 사용자의 입력을 받아서 내부 로직을 처리

2. MVC 아키텍처와 MVT 아키텍처
  - Model: 데이터베이스와 소통
  - View: 로직은 담당
  - Template: 화면 구성을 담당
  - Model -> Model
  - View -> Template
  - Controller -> View

## 25. 한 번에 이해하는 Django
1. 프론트엔드,백엔드,풀스텍

2. 클라이언트, 서버, URL

3. url,view,model,template,mvt

## 26. 코스토랑 프로젝트 #02 URL 연결하기
1. costaurant/urls.py 수정
```py
path('menus/', include('menus.urls')),
```

2. menus/urls.py 수정
```py
from django.urls import path
from . import views

urlpatterns = [
    path('index/', views.index_view)
]
```

3. menus/view.py 수정
```py
from django.shortcuts import render
from django.http import HttpResponse

def index_view(request):
    return HttpResponse("<h2>코스토랑 오픈!</h2>")
```
