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



