# 3. Selenium 웹 스크래핑
## 01. Selenium으로 웹 스크래핑하기
1. 3개의 요소
  - `find_element()`
  - `click()`
  - `send_keys()`

2. CSS 선택자 활용
  - BeautifulSoup : `soup.select_one()`, `seoup.select()`
  - Selenium: `driver.find_element()`, `driver.find_elements()`

3. HTML 태그
  - BeautifulSoup: `Tag`
  - Selenium: `WebElement`
  - 우리가 생각하는 HTML Tag를 
  - Beautiful Soup에서는 그냥 Tag라고 불렀지만,
  - Selenium에서는 WebElement, 즉 `웹 요소`라고 합니다.
  - BeautifulSeoup을 사용할 때는 단순히 HTML Tag의 내용만 봤지만
  - Selenium을 사용할 때는 `HTML Tag`에 매칭되는 실제 `웹 요소`와 `상호작용`이 있기 때문이죠.
  - **Tag를 클릭한다거나 Tag에 무언가를 입력한다고 하면 이상하겠죠?**

4. 웹 요소 찾기
  - BeautifulSoup: `tag.select()`
  - Selenium: `web_element.find_elements()`
  - BeautifulSoup의 select 메소드를 Tag에도 쓸 수 있듯이 find_elements도 `웹 요소`에 쓸 수 있습니다.
  - `웹 요소` 안에서 다른 요소들을 찾는 거죠.

5. 텍스트 가져오기
  - BeautifulSoup: `tag.get_text()`
  - Selenium: `web_element.text`
  - Tag 안에 있는 텍스트를 모두 가져오는 건 get_text()를 썼었죠?
  - Selenium에서는 그냥 `.text`를 씁니다.

6. 문자열 리스트 가져오기 
  - BeautifulSoup: `tag.strings()`, `tag.stripped_strings()`
  - Selenium: `없음`
  - Tag 안에 있는 문자열을 하나씩 리스트로 가져오는 `strings` 또는 `stripped_strings` 메소드가 있었는데
  - Selenium에는 그런 메소드가 없습니다.

7. Tag의 속성 가져오기
  - BeautifulSoup: `tag['attr']`
  - Selenium: `web_element.get_attribute('attr')`
  - Tag의 속성을 가져오려면 BeautifulSoup에서는 네모 괄호 안에 속성 이름을 써 줬는데요.
  - Selenium에서는 get_attribute라는 메소드 안에 속성 이름을 써 줍니다.

8. BeautifulSoup에서 Selenium으로 변경
  - for tag in soup.select('ul.popular__order li')
  - `for element in driver.find_elements(by=By.CSS_SELECTOR, value='ul.popular__order li')`
  - tag.get_text().strip()
  - `element.text.strip()`

## 02. 오렌지 보틀 커피
1. **매우 중요** 정리된 Selenium 메소드들입니다.
  - soup.select_one() / driver.find_element()
  - soup.select() / driver.find_elements()
  - Tag / WebElement
  - tag.select() / web_element.find_elements()
  - tag.get_text() / web_element.text
  - tag.strings() / -
  - tag.stripped_strings() / -
  - tag['attr'] / web_element.get_attribute('attr')

2. `from selenium import webdriver`
  - 주어진 코드를 한 줄 씩 Selenium 코드로 바꿔 볼게요.
  - 먼저 import 문을 바꿔 줘야 합니다.
  - `requests`와 `BeautifulSoup` 대신 `selenium`에서 `webdriver`를 가져옵니다.
  
3. `driver = webdriver.Chrome()`
  - 이전에는 `requests`로 요청을 보내고, 응답으로 돌아오 HTML 코드를 BeautifulSoup을 통해 정리 했다면,
  - Selenium에서는 웹드라이버를 생성하고, 웹 드라이버로 요청을 보내면 됩니다.

4. `driver.find_elements()`
  - 이제 모든 지점에 대한 태그를 가져오면 되는데,
  - soup.select()는 driver.find_elements()로 대체할 수 있습니다.

5. `.find_element()`, `.text`
  - 그리고 Selenium에서는 보통 '태그' 대신 '웹 요소'라는 용어를 사용하기 때문에, 코드의 동작에는 상관이 없지만
  - 변수 이름을 약간 바꿔 줬습니다.

6. `driver.quit()`
  - 웹 드라이버 종료

## 03. Selenium으로 JavaScript 사용하기
1. JavaScript를 쉽게 실행할 수 있는 방법
  - 개발자 도구 > Console

2. `window.scrollTo(0, 200)`
  - 이 코드는 오른쪽 방향으로 0만큼 
  - 아래쪽 방향으로 200만큼 스크롤을 이동시킨다는 자바스크립트 코드입니다.
  - window.scrollTo(0,400) 더 많이 내려간다.

3. `document.body.scrollHeight`
  - 이건 웹페이지 전체의 세로 길이 입니다.

4. **매우 중요** `execute script`
  - Selenium은 자바스크립트를 실행할 수 있는 기능을 제공해 줍니다.
  - `execute script`라는 함수인데요.
  - `driver.execute_script('window.scrollTo(0,200);')`

5. 스크롤
  - JavaScript의 리턴값을 받아 올 수 있다.
  - `scroll_height = driver.execute_script('return document.body.scrollHeight')`
  - print(scroll_height)

6. 끝까지 스크롤
  - scrollHeight까지 스크롤
  - 새로운 내용 로딩될때까지 기다림
  - 새로운 내용 로딩됐는지 확인
```
while True:
    driver.execute_script('window.scrollTo(0, 200);')
    new_height = driver.execute_script('return document.body.scrollHeight;')
    sleep(0.5)
    if new_height == last_height:
        break
    last_height = new_height
```

7. HTML에서 window와 document의 차이점

8. `window` 객체체
  - 브라우저 창 또는 탭 자체를 나타냅니다.
  - 브라우저의 최상위 객체(전역 객체)입니다.
  - 전역 함수와 변수도 `window`객체의 속성이 됩니다.
  - (주요특징)
  - 브라우저 전체를 제어: 창 크기, 스크롤 위치, 브라우저 히스토리, 타이머, 경고 대화 상자 등 브라우저와 관련된 작업을 수행합니다.
  - 모든 전역 변수와 함수는 `window`의 소성으로 자동으로 추가됩니다.
  - (주요 메소드와 속성)
  - window.aler(): 알림 창 띄우기
  - window.open(): 새 창 열기
  - window.scrollTo(x, y): 특정 위치로 스크롤
  - window.location: 현재 페이지 URL 정보
  - window.innerWidth, window.innerHeight: 창의 너비와 높이

9. `document` 객체
  - 웹 페이지의 콘텐츠(HTML 문서)를 나타냅니다.
  - DOM(Document Object Model)을 통해 HTML 요소를 조작하고, 이벤트를 추가하거나, 데이터를 읽을 수 있습니다.
  - (주요특징)
  - 웹 페이지의 구조와 내용을 제어하고 접근 할 수 있습니다.
  - DOM 트리의 루트로, HTML 요소를 탐색하고 조작할 수 있습니다.
  - (주요 메소드)
  - document.getElementById(), document.querySelector(): 특정 요소 선택.
  - document.createElement(): 새로운 HTML 요소 생성.
  - document.body : `<body>` 요소에 접근
  - document.title : 현재 문서의 제목
  - document.cookie : 쿠키를 읽고 쓰기

10. `비유`
  - `window`는 집입니다.
  - 집 자체(문, 창문, 벽 등)를 제어합니다.
  - 집의 크기, 위치, 보안 시스템 같은 것들을 관리합니다.
  - `document`는 집 안의 물건들입니다.
  - 집 안의 가구나 물건(소파, 테이블, 책)을 제어합니다.
  - 가구를 추가하거나, 제어하거나, 재배치합니다.

## 04. 플레이리스트 정보 스크래핑
1. `.find_elements`
  - playlists = driver.find_elements(by=By.CSS_SELECTOR, value='div.playlist__meta')

2. `.text`
  - title = playlist.find_element(by=By.CSS_SELECTOR, value='h3.title').text

## 05. Selenium 과 BeautifulSoup
1. Selenium과 BeautifulSoup
  - Selenium: 동적인 페이지
  - BeautifulSoup: 복잡한 페이지

2. `music_page = driver.page_source`
  - `드라이버 페이지 소스`로 현재 웹 페이지의 HTML 코드를 가져옵니다.

3. `soup = BeautifulSoup(music_page, 'html.parser')`
  - 가져온 HTML 코드로 BeautifulSoup을 만들고요.
  - BeautifulSoup으로 데이터를 추출했습니다.

4. 정리
  - 이런 식으로 `브라우저 동작`이 필요한 부분에만 `Selenium`을 활용하고
  - `데이터 추출`은 `BeautifulSoup`을 한 번 활용해 보세요.

## 06. Selenium과 웹 스크래핑 정리 노트
1. BeautifulSoup과 Selenium

2. 웹 요소 가져 오기

3. 웹 요소에서 데이터 추출하기

4. Selenium과 JavaScript




