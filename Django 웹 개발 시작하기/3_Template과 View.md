# 3. Template과 View
## 01. 템플릿(Template) 적용하기
1. 템플릿 파일을 장고프로젝트로 옮겨 보겠습니다.
  - foods/templates/foods
  - css, fonts, images, index.html을 넣는다.

## 02. 정적(static)파일 관리하기
1. 정적 파일 (static files)
  - 웹 페이지를 렌더링(Rendering) 하는 과정에서 필요한 추가적인 파일
  - css
  - fonts
  - images

2. foods/static/foods 폴더 생성
  - 그 폴더 속에 css, fonts, images 생성
  - css, fonts, images 이동
  - templates/foods 속에는 index.html만 남는다.

3. index.html 속의 경로 수정
  - href={% static 'foods/css/styles.css' %}
  - src={% static 'foods/images/chicken.jpg' %}

4. 정리
  - 정적 파일이 무엇인지에 대해서 배우고, 
  - Django에서 정적 파일을 넣어주는 디렉토리 구조에 대해 알아 보았습니다.
  - 정적 파일을 사용하기 위한 **템플릿 태그**인 `load static`에 대해서 배우고, 
  - 정적 파일의 경로를 이용하는 방법에 대해서 알아 보았습니다.

## 03. 신메뉴 출시!
1. {% static 'foods/images/banana.jpg' %} 추가

2. {% static 'foods/images/croquette.jpg' %} 추가

3. {% static 'foods/images/pumpkin_soup.jpg' %} 추가

4. 파일 위치
  - foods앱 속에 static/foods/images/banana.jpg

5. 샐프 채점
  - 새로 추가한 모든 음식의 사진이 잘 나오나요?
  - 모든 이미지의 경로에 템플릿 태그 static을 사용했나요?
  - CSS가 잘 적용되어 나오나요?

6. 해설
  - `템플릿 태그를 명시`
  - {% load static %}
  - `템플릿 태그를 사용`
  - {% static 'foods/css/styles.css' %}
  - {% static 'foods/images/image_file' %}

## 04. Template과 static의 폴더 구조
1. Template 만드는 법
  - App 디렉토리 아래 templates 아래 foods 아래에 우리가 원하는 템플릿 파일을 넣었습니다.

2. 정적파일도 비슷함

3. 샌드위치 구조
  - 폴더 구조가 샌드위치 구조가 아닐 시 문제 발생!
  - A/templates/index.html
  - B/templates/index.html
```
path('A/', include('A.urls')),
path('B/', include('B.urls'))
```

4. settings.py에서 APP_DIRS 항목이 True로 설정되어 있으면,
  - `APP_DIRS: True` : 각각의 앱에 templates 디렉토리가 있으니까,
  - templates를 찾을 때, 거기서 찾아라
```
TEMPLATES = [
  {
    'APP_DIRS': True,
  }
]
```

4. settings.py 에서 INSTALLED_APPS
  - `등록된 앱의 순서대로 index 탬플릿을 찾게 됩니다.`
  - 그런데 index 탬플릿은 A 앱에도 있고, B 앱에도 있다.
  - 이때 장고는 앱이 등록된 순서대로 살펴 보면서, 일치하는 템플릿을 가져온다.
  - 항상 A 구조 안의 index.html 을 가져온다.
  - 이렇게 이름이 겹치는 문제를 해결하기 위해서 샌드위치 구조를 쓰는 건데요.
  - templates 안에 바로 index를 두는 것이 아니라, 
  - 이 사이에 앱 이름을 둠으로써 A에서는 A안의 index 탬플릿을 가져와라
```py
return render(request, 'A/index.html')
```

5. images 같은 것은 개발할 때는 문제가 없는데, 배포할 때 문제가 생긴다.
  - `배포 환경`에서는 모든 정적 파일들을 **하나의 디렉토리**로 모아서 사용하게 되는데요
  - 이때 같은 이름의 파일이 있으면, 충돌이 나게 됩니다.
  - 그런데 이 파일들을 각각의 앱이름의 폴더에 넣어두면, 하나의 디렉토리로 모았을 때도 문제 없이 사용할 수 있습니다.
  - 이와 같은 이유로 `앱 이름의 디렉토리`를 추가적으로 만들어서 샌드위치 구조를 사용하는 것입니다.

## 05. Template Language 이해하기
1. 템플릿 언어
  - `템플릿 변수`: 우리가 지정한 데이터로 변환
  - `템플릿 태그`: 템플릿 작성에 로직을 사용
  - `템플릿 필터`: 템플릿 변수를 특정 형식으로 변환
  - `템플릿 주석`: 템플릿 언어의 주석처리를 담당

2. `템플릿 변수`
  - {{변수명}}
  - 중괄호 두개로 사용한다.
  - 우리가 지정한 데이터로 변환
  - `view`에서 `template`으로 원하는 데이터를 전달하고, 
  - `template`은 이 `템플릿 변수`를 이용해서 전달 받은 데이터를 사용합니다.
  - 즉 `템플릿 변수`는 view에서 template으로 넘겨준 데이터로 해석되서 변환됩니다.
  - `점 연산자`: 템플릿 변수는 `점 연산자`를 지원하는데, 템플릿 내부 속성에 접근할 때 사용합니다.
```
codeit = {
  title: 'django',
  version: 1.0
}
{{ codeit.title }}
```

4. `템플릿 필터`
  - {{ 변수명 | 필터}}
  - 파이프 연산자를 사용. 
  - 템플릿 변수를 특정 형식으로 변환하기 위해서 사용
```
{{codeit|upper}}
```
  - codeit이라는 `템플릿 변수`에 upper `필터`를 적용시켜서 모두 대문자로 바꿔줍니다.

5. `템플릿 태그`
  - {% 태그 %} {% end태그 %}
  - `템플릿 태그`는 탬플릿을 작성할 때, 로직을 함께 넣어서 템플릿을 편하게 작성할 수 있도록 해 주는데요.
```
반복:
{% for %}
{% endfor %}
조건:
{% if %}
{% else %}
{% endif %}
상속:
{% block %}
{% endblock %}
```

6. `템플릿 주석`
  - {# 주석 #}
  - 템플릿 언어에서 주석 처리를 하기 위한 것

7. 정리
  - view에서 넘겨주는 데이터를 template에서 사용할 수 있게 해 주는 `템플릿 변수`
  - 템플릿 변수를 특정한 형식으로 변환해 주는 `템플릿 필터`
  - 템플릿에 로직을 넣어주는 `템플릿 태그`
  - 주석을 위한 `템플릿 주석`

## 06. Template Language 한 걸음 더
1. 점 연산자
  - 변수를 사전형(dict)으로 생각하고 점(.) 연산자로 Key값 조회
  - 변수를 객체로 생각하고 내부 속성값 조회 또는 함수 호출
  - 변수를 리스트(list)로 생각하고 점(.) 연산자로 Index 조회

2. 템플릿 필터
  - `{{ variable|default:"coffee"}}`
    - 변수가 비어 있거나 False면 **coffee**라는 텍스트로 대체 됩니다.
  - `{{ variable|capfirst}}`
    - 맨 첫글자를 대문자로 바꿔 줍니다.
  - `{{ variable|random}}`
    - 반복 가능한 템플릿 변수에 대해 무작위로 하나를 추출해 변환합니다.
  - `{{ variable|upper}}, {{variable|lower}}`
    - 템플릿 변수를 대문자 또는 소문자로 변환합니다.
  - `{{ variable|ljust:"length"}}, {{ variable|rjust:"length"}}`
    - 주어진 길이 내에서 공백을 넣어 왼쪽 정렬(ljust) 또는 오른쪽 정렬을 한 문자열로 변환합니다.
```
variable = 'codeit'
{{variable|ljust:"10"}} --> codeit____
```

3. 템플릿 태그 (Template Tag)
  - `{% tag %} ~ {% endtag %}`
  - `{% for obj in values %} ~ {% endfor %}`
```
{% for food in foods %}
  <li> {{ food.name }} </li>
{% endfor %}
```
  - 아래는 역순으로 반복
```
{% for food in foods reversed %}
  <li> {{ food.name }} </li>
{% endfor %}
```
  - 반복 가능한 객체가 비어 있거나 존재하지 않을 때는 아래와 같이 사용할 수 있습니다.
```
{% for food in foods %}
  <li> {{food.name}} </li>
{%empty%}
  <li> There is no food.</li>
```
  - `if`
```
{% if value1 %} ~ {%elif value2 %} ~ {% else %} ~ {% endif %}
```
  - `with`: 복잡한 변수가 있을 때 '별명'을 붙이기 위해 사용합니다.
```
{% with value1=value2 %} ~ {% endwith %}
```

## 07. 코스토랑 프로젝트 #03 메인 페이지
1. 정적파일과 템플릿의 디렉토리 구조
  - <앱 이름>/templates/<앱 이름>/template files
  - <앱 이름>/static/<앱 이름>/static files

2. view 작성하기
  - render 함수의 두번째 인자로 menus/index.html 경로를 전달합니다.
```
def index(request):
  return render(request, 'menus/index.html')
```

3. index template 작성하기
```
<% load static %>
```

4. 정적 파일 경로 설정하기
```
<link rel="stylesheet" href="{% static 'menus/css/styles.css' %}">
<img src="{% static 'menus/images/logo-color.svg' %}">
<img src="{% static 'menus/images/header-txt.svg' %}" style="width=330; height=89;">
<img src="{% static 'menus/images/chicken.jpg' %}"/>
<img src="{% static 'menus/images/logo-gray.svg' %}"/>
```

## 08. 중복되는 템플릿 코드 없애기
1. 템플릿 상속
  - 반복적인 것은 템플릿 상속으로 해결한다.
  - 공통적인 부분을 부모파일로 만들어 주고,
  - 부모파일로 부터 상속 받고, 달라지는 부분만 작성하는 것을 말합니다.

2. 템플릿 상속은
  - 템플릿 태그인 `{% block %}`과 `{% extends %}`를 사용해서 구현합니다.

3. 부모 템플릿
  - base.html 모두 복사 
  - food-container 삭제
  - {% block food-container %}
  - {% endblock food-container %}

4. 또 하나
  - {% block date-block %}
  - {% endblock date-block %}

5. 자식 템플릿
  - {% extends './base.html' %}
  - {% load static %}
```
{% block date-block %}
  <div>12 Aug, 2020</div>
{% endblock date-block %}
{% block food-container %}
 ...
{% endblock food-container %}
```

6. 자식 템플릿에서 구현하지 않으면 
  - 부모 템플릿의 내용이 들어감

## 09. 여행 사이트 템플릿 중복 제거하기
1. base.html 생성하기

2. 부모 템플릿에 block 지정하기

3. 자식 템플릿에서 부모 템플릿 상속하기


## 10. 계속 변하는 동적 웹 페이지 만들기
1. MVT에서는 View에서 로직을 담당한다.
  - URL > `View` > `함수 호출` > `Model` > 데이터베이스 > `View` > `Tempalte` > 화면

2. 넘겨주는 데이터는 사전형에 담아서 보내줘야 한다.
  - `context = {"date":today}`
  - return render(request, 'foods/index.html', context=context)

3. View에서 넘겨 받은 값으로 변환
  - `템플릿 변수`
  - 템플릿 언어 중에서 View에서 템플릿으로 넘긴 데이터로 변환 되는 것이 무엇이었는지 기억하시나요?
  - 템플릿 변수를 사용해서 View에서 넘겨준 데이터를 사용하면 됩니다.
  - `{{date}}`

## 11. 파이썬 함수 사용 팁
1. 매개변수와 반환 값이 없는 형태

2. 매개변수는 없지만 반환 값은 있는 형태

3. 매개변수는 있지만 반환 값이 없는 형태

4. 매개변수와 반환 값이 모두 있는 형태

5. 인자를 전달하는 두가지 방법
  - 위치 전달 인자 (Positional Arguments)
  - 키워드 전달 인자 (Keyword Arguments)

## 12. 코스토랑 프로젝트 #04 날짜 바꾸기
1. `views.py`의 index view에서 datetime 모듈을 통해 날짜 데이터를 가져옵니다.

2. `today`를 Key로 하고 today를 value로 하는 사전형 데이터를 만들어서 context 변수에 담아 주세요.

3. `render()` 함수의 세 번째 인자로 context 데이터를 템플릿으로 전달합니다.