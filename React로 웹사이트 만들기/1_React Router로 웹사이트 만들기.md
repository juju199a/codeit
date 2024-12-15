# 1. React Router로 웹사이트 만들기
## 01. 리액트로 웹사이트 만들기
1. React Router
  - Single Page Application
  - Client-side Rendering
  - Server-side Rendering

## 02. 함께 만들 프로젝트 소개
1. 코드댓
  - Main.js
  - **참고자료** Adding a CSS Modules Stylesheet | Create React App

## 03. 리액트 라우터 v6 소개
1. React Router
  - 리액트 컴포넌트로 페이지를 나누는 라이브러리

2. 페이지를 나눌때
```
<Routes>
  <Route path="/" element={<HomePage />} />
  <Route path="courses" element={<CourseListPage />} />
  <Route path="courses/1" element={<CoursePage />} />
  <Route path="*" elemen={<NotFoundPage />} />
</Routes>
```

3. 이동할 때
```
<Link to="/">홈페이지</Link>
<Link to="/courses">수업 탐색</Link>
<Link to="/questions">커뮤니티</Link>
```

4. 핵심 컴포넌트들
  - Router
  - Routes
  - Route
  - Link

5. Router
  - 리액트 라우터에서 사용하는 데이터들을 모두 갖고 있는 녀석입니다.
  - 현재 주소라던지 페이지 기록 같은 데이터를 가지고 있는데요.
  - 이게 없으면 리액트 라우터를 쓸 수 없어요.
  - 전에 배웠던 Context라는 개념 기억나시나요?
  - Context는 Props를 거치지 않고, 자손 컴포넌트에 데이터를 넘겨줄 때 사용하는데요.
  - **데이터를 내려줄 범위를 `Context Provider`라는 컴포넌트로 지정했습니다.**
  - Router 컴포넌트도 내부적으로는 `Context Provider` 인데요.
  - 그래서 React Router에서 제공하는 기능을 사용하려면
  - 반드시 Router 컴포넌트 안에서 사용해야 합니다.
  - 보통은 이런 식으로 최상위 컴포넌트에서 Router를 감싸고 사용하는데요.
  - 이렇게 하면 프로젝트 전체에서 `리액트 라우터`를 쓸 수 있기 때문이죠.
```
import { BrowserRouter } from 'react-router-dom';

function Main() {
  return <BrowserRouter>...</BrowserRouter>;
}

export default Main;
```

6. Routes, Route
  - 이 두 컴포넌트는 주로 같이 사용하는데요.
  - 자바스크립트에서 switch case문 같은 거라고 이해하면 쉽습니다.
  - Routes 컴포넌트 안에서 페이지의 경로랑 보여줄 컴포넌트를 지정하는 건데요.
  - url에 맞는 컴포넌트를 보여줍니다.

7. Link 컴포넌트
  - a 태그 대신 사용

## 04. 리액트 라우터 설치하기
1. 패키지란?
  - `react`와 `react-dom`이라는 패키지로 사용하고 있습니다.

2. 패키지 설치하기
  - `npm install react-router-dom@6`
  - package.json파일에서 dependencies 아래에 react-router-dom이란 게 추가 되었는지 확인

3. react-router-dom 패키지를 사용할 때 주의할 점
  - react-router (X)
  - react-router-dom (O)

4. 라우터 컴포넌트 감싸기
  - `import { BrowserRouter } from 'react-router-dom';`
  - <BrowserRouter><App></App></BrowserRouter>
  - 사실 라우터에는 여러 종류가 있지만, 우리는 브라우저의 기본적인 방식으로 사용할 거니까 `BrowserRouter`라는 걸 사용할게요.
  
## 05. Routes로 페이지 나누기
1. Main.js
  - 우선 Main.js 파일에서 `각 페이지`에 해당하는 컴포넌트를 배치할 건데요.
  - `Routes`와 `Route`를 import 한 다음에
  - <Routes>를 감싸고
  - <Route> 컴포넌트를 배치해 볼께요.
  - `/`로 들어 오면, `HomePage라는 컴포넌트`를 보여주도록 지정했습니다.
  - Route 컴포넌트의 path Prop으로 경로를 지정하고, element Prop으로 보여줄 컴포넌틀르 지정할 수 있는데요.
  - 이때 element Prop은 `컴포넌트 함수`가 아니라 `JSX`를 넘겨 준다는 점도 눈여겨 봐주세요.
  - `<Route path="/" element={<HomePage />}>`

2. Routes와 Route
  - 참고로 Routes랑 Route 컴포넌트는 실제로 div태그 같은 걸 렌더링 하지 않는데요.
  - `React.Fragment`처럼 리액트 상에서만 존재하는 컴포넌트입니다.

## 06. Link로 이동하기
1. Nav.js
  - `Link 라는 컴포넌트`를 불러와서, 로고 이미지와 카탈로그 메뉴를 감싸줄께요.
  - Link 컴포넌트에서는 `to`라는 Prop를 사용하는데요.
  - 이렇게 이동할 경로를 지정하면 됩니다.
  - `/`를 제일 앞에 붙이는 것은 절대 경로라는 의미인데요.
  - 만약 `/`를 안붙이면, 현재 주소의 맨 뒤에다가 웹 브라우저가 /courses를 붙여서 이동하게 됩니다.
  - `a` 태그와 마찬가지로 동작한다고 보시면 됩니다.

2. UserMenu.js
  - `WishList`

3. CourseListPage.js > CourseItem.js
  - 이번엔 템플릿 문자열을 추가할 겁니다.
  - **<Link to={`/courses/${slug}`}>**
  - `slug`는 각 데이터를 구분하는 `고유한 문자열`이라고 생각하시면 됩니다.
  - 웹 개발에서는 ID보다 좀더 의미있는 주소를 만들때, 주로 사용합니다.

4. Main.js

5. **참고자료**
  - 배열 렌더링하기 - map으로 배열 렌더링하기
  - **반드시** 중괄호를 쓰면 return을 해야 한다.
```
items.map((item) => {
  return (
    <li>
      <ReviewListItem item={item}>
    </li>
  )
})
```
```
courses.map((course) => (
  <CourseItem key={course.id} course={course} />
))
```

## 07. 커뮤니티 페이지 추가하기
1. Routes 컴포넌트 안에 Route 컴포넌트를 배치
  - <Route path="/questions" element={<QuestionListPage />} />
  - <Route path="/questions/616825" element={<QuestionPage />}>

2. Nav.js
  - <Link to="/questions">커뮤니티</Link>

## 08. NavLink로 네이게이션 구현하기
1. NavLink 사용
  - 네브링크는 `네이게이션 링크`. 
  - 즉, `메뉴에서 사용하는 링크`라는 뜻인데요.
  - NavLink는 Link랑 마찬가지로 사용할 수 있지만,
  - 한가지 다른 점은 `style`이라는 Prop로 함수를 지정해 줄 수 있다는 점입니다.
  - 여기에다가 `getLinkStyle`이라는 함수를 내려 줄건데요.
  - 파라미터로는 객체로 받는데, 객체의 프로퍼티는 `isActive`라는 Boolan형이 있습니다.
  - 현재 페이지의 경로가 `네이게이션의 링크`에 해당하면, 이 값이 참이 됩니다.
  - 이 함수에서는 리액트 인라인 스타일 객체를 리턴하면 되는데요.

2. **참고자료**
  - React 개발 기초 - 인라인 스타일


## 09. 하위 페이지 나누기
1. Route
  - 앞에서 Routes와 Route로 페이지를 나눠봤는데요.
  - path가 길어지고 복잡해지면, 하나의 Routes 안에서 다루기에는 너무 복잡하겠죠?
  - 그래서 리액트 라우터에서는 Route를 중첩해서 사용할 수 있게 해줍니다.

2. index
  - CourseListPage와 CoursePage를 하위 Route로 만들어 볼께요.
  - 우선 Course라는 경로를 갖는 Route들만 따로 Route 컴포넌트로 감싸 줄께요.
  - 그리고 여기에 path Prop로 `courses`를 지정한 다음에, 안에 있는 Route에는 `courses`를 지워줍니다.
  - 이때 `index`에 해당하는 Route에는 path Prop 대신에 `index`를 지정해 주면 됩니다.
  - 감싼 Route의 path값이 courses니까 index Route 컴포넌트의 path는 courses가 되고, 
  - `react-frontedn-development`의 path는 `courses/react-frontedn-development`가 됩니다.

3. `/`와 index
  - Route를 중첩해서 만들 때 간혹 특정 path 안에서는 공통된 디자인을 보여주고 싶을 수 있습니다.
  - 최상위 경로를 Route로 감싸면서, 어떻게 하는지 살펴보겠습니다.
  - path Prop으로는 `/`를 내려주고, 홈페이지를 렌더링하던 Route에는 `index` Prop로 지정해 줄께요.
  - 여기서 보시면 App 컴포넌트가 전체를 감싸고 있는데요.
  - **`App 컴포넌트`는 공통 레이아웃을 렌더링하는 컴포넌트입니다.**
  - children Prop를 받아서, 안에다가 렌더링하고 있죠.
  
4. `Outlet`
  - 그런데, 이 `App 컴포넌트`를 path가 `/`인 Route 안쪽에 감싸면 어떻게 될까요?
  - **오류**
  - **`Routes`안에는 반드시 `Route`나 `Freagment`만 배치할 수 있다고 하네요.**
  - 이럴 때 리액트 Route에는 `아울렛(Outlet)`이라는 컴포넌트를 활용해야 하는데요.
  - 감쌌던 App 컴포넌트는 지워주고, element Prop로 내려준 다음에, 
  - App 컴포넌트에서는 children Prop 대신에 `<Outlet>`이라는 컴포넌트를 넣어주겠습니다.
  - 이렇게 하면 `Route`안에서 렌더링 되는 부분은 `Outlet 컴포넌트`가 있는 부분에 렌더링됩니다.

## 10. 커뮤니티 페이지 분리하기
1. Main.js 수정
  - <Route path="/questions"> 로 감싸준다.
  - index로 설정

## 11. useParams로 동적인 경로 만들기
1. Main.js 에서 :courseSlug로 적어준다.
  - `react-frontend-development` 대신에 `:courseSlug`라고 적어줄게요.
  - 이렇게 하면 courseSlug라는 변수로 페이지의 경로를 받아 올 수 있는데요.
  - 이런 것을 리액트 라우터에서는 `파라미터`라고 부릅니다.

2. CoursePage 컴포넌트
  - `useParams()` 라는 리액트 라우터에서 제공하는 `커스텀 Hook`을 사용할게요.
  - useParams가 리턴하는 객체에는 `현재 경로의 파라미터`들이 저장되어 있는데요.
  - 이 객체에 우리가 정의한 `courseSlug`라는 값도 저장되어 있습니다.
  - 이렇게 `디스트럭쳐링`으로 courseSlug 값을 가져올게요.
  - 그리고 기존에 사용하던, `react-frontend-development`라는 값을 `courseSlug`라는 변수로 바꿔줄께요.
  - 아 컴포넌트에 있는 나머지 코드들은 `courseSlug`라는 값에 따라서 알맞은 course 데이터 값을 가져오고, 렌더링하는 코드입니다.

3. 정리
  - 동적인 경로를 만들어봤는데요.
  - `경로`에서 사용하는 `동적인 값`을 `파라미터`라고 부르고, 
  - 이런 파라미터를 모아 놓은 걸 `Params`라고 부릅니다.
  - 그래서 이렇게 useParams라는 Hook으로 params 객체를 가져올 수 있었죠.
  - 경로 파라미터를 지정하려면, Route 컴포넌트의 path Prop에서 `:`뒤에 원하는 이름을 적어주면 됩니다.
  - 이렇게 하면 페이지 경로가 달라질 때마다 `파라미터의 값`이 달라지니까, 같은 컴포넌트라도 `파라미터의 값`에 따라서 데이터만 다르게 보여줄 수가 있죠.

## 12. 커뮤니티 글 보여주기
1. Main.js
  - `:questionId`

2. QuestionPage.js
  - `const {questionId} = useParams();`

## 13. 없는 페이지 처리하기 
1. <Route path="*">
  - 모든 경로를 경로를 포함하는 `Route`를 추가하면 되는데요.
  - 엘리먼트로는 <NotFoundPage> 컴포넌트를 넣어줄게요.

2. **NotFoundPage**
  - <Link to="/"><Button>홈으로 가기

## 14. Navigate로 리다이렉트 하기
1. 리다이렉트 (Redirect)

2. CoursePage.js
  - 코스에서 값을 가져올 때 오류인데,
  - course가 `undefined`: slug에 해당하는 course를 가져올 수 없어서 생긴 오류 같습니다.
  - 코스 목록 페이지로 리다이렉트 하도록 만들어 볼께요.
  - 즉 course의 값이 없으면, <Navigate> 라는 컴포넌트를 리턴해 주겠습니다.
  - `to라는 Prop`로는 `/courses`라는 경로를 넣어 줄 건데요.
  - 이 컴포넌트를 렌더링하면 리액트 라우터는 `to Prop`에 지정된 경로로 이동시켜줍니다.

## 15. 없는 질문 처리하기
1. QuestionPage.js
  - questionsId 검사 후, 없으면
  - <Navigate to="/questions">

## 16. useSearchParams로 쿼리 사용하기
1. `쿼리 스트링`
  - ?keyword=react

2. CourseListPage.js
  - 맨위에 검색창이 있는데요.
  - input 태그에는 name값을 keyword라고 지정해 두었습니다.
  - handleKeywordChange라는 함수가 있어서, 
  - 값을 입력할 때마다 keyword 스테이트의 값이 함께 변경됩니다.
  - 이 form 태그의 기본 동작은 Enter나 Submit 버튼을 누르면, 
  - 쿼리와 함께 페이지를 이동하는 건데요.
  - 우리는 이것을 수정해서 검색 결과를 보여줄 겁니다.

3. api/index.js
  - 여기 getCourses()라는 함수를 보면, 검색어에 해당하는 키워드를 파라미터로 받는데요.
  - CourseListPage 컴포넌트에서 주소창에 있는 쿼리 파라미터를 가져와서
  - getCourses() 함수로 넘겨 주면, 검색 결과를 보여줄 수 있을 것 같습니다.

4. useSearchParams()
  - `useSearchParams()`라고 하는 리액트 라우터에서 제공하는 커스텀 Hook을 사용할 건데요.
  - 리액트 라우터에서는 `쿼리 파라미터값`을 가져오고 싶을 때, `useSearchParams()`라는 Hook을 사용할 수 있습니다.
  - `const [searchParams, setSearchParams] = useSearchParams();`
  - useState랑 사용하는 형태가 비슷하죠.
  - 차이점이 있다면, State값에 해당하는 부분은 `searchParams`라는 객체라는 점입니다.
  - `searchParams 객체`에서는 get() 함수를 통해서 안에 있는 값을 가져올 수 있는데요.

5. initKeyword
  - keyword 쿼리 파라미터의 값을 `initKeyword` 라는 변수에 집어 넣고,
  - keyword 스테이트의 초깃값과 getCourses()의 파라미터로 넘겨주겠습니다.
  - keyword 스테이트는 input에다가 밸류로 내려줄 것이기 때문에, 반드시 문자열이어야 하는데요.
  - `useState(initKeyword || '')`

6. form 태그에서 onSubmit
  - 입력 form을 submit 했을 때, 주소창에 있는 쿼리 스트링을 바꿔 볼께요.
  - form 태그에서 onSubmit라는 Prop로 구현하면 되는데요.
  - onSubmit에 handleSubmit라는 함수를 내려주고, handleSubmit 함수에서는 이벤트 객체를 받아서,
  - 일단 `preventDefault()`라는 함수를 실행해 줍니다.
  - 이렇게 하면 Submit을 했을 때, 웹 브라우저가 저절로 페이지를 이동하지 않습니다.
  - **이렇게 기본 동작 대신에, `리액트 라우터`를 통해서 `쿼리 파라미터`를 변경하는 이유는 뒤에서 자세히 설명 드릴께요.
  
7.   
  - setSearchParams()를 실행하는데, 이 함수는 파라미터로 `객체`를 받습니다.
  - 여기다가 원하는 `쿼리 파라미터`를 객체의 프로퍼티로 넘겨주면 됩니다.
  - keyword라는 `쿼리 파리미터`의 값이 지정됩니다.
  - 그런데 keyword에 값이 없으면 `쿼리 파라미터`로 `null값` 같은 것이 지정되면 안되니까
  - keyword 스테이트 값에 따라서 keyword 스테이트 값이 없으면, 빈 객체로 넘겨 줄게요.

8. Warning
  - 조건 연산자로 courses의 개수가 하나도 없을 때, 
  - 경고 메시지를 보여주는데요.
  - 경고 메시지를 읽어보면, 검색 결과가 없다는 걸 알려주는 메시지니까
  - 여기 `검색어가 있을 때`라는 조건을 추가해 주는 게 좋겠죠.
  - `{initKeyword && courses.length === 0 }`

9. **참고자료**
  - 웹 개발 기초 지식 - URL
  - 입력 폼 다루기 - 입력 폼 뽀개기

## 17. 질문 검색창 만들기
1. **useSearchParams**
  - 리액트 라우터에서 쿼리 값을 가져오려면 `useSearchParams`라는 커스텀 Hook을 사용할 수 있습니다.
  - 이 Hook 함수는 searchParams와 세터 함수를 배열형으로 리턴하는데요.
  - 여기서 `searchParams`에서는 `get()`이라는 함수로 값을 가져올 수 있습니다.
  - `keyword`라는 쿼리 값을 `initKeyword`라는 변수에다가 지정해 주려면 아래처럼 하면 됩니다.

2. **setSearchParams({ keyword: 'react' });**
  - 그리고 세터 함수인 `setSearchParams()`에 값을 지정하려면, 객체를 넘겨주면 되는데요.
  - 예를 들어서 아래처럼하면 주소창의 쿼리 값이 `?keyword=react`로 변경됩니다.

3. QuestionListPage.js
  - 우선 `keyword`라는 쿼리 값을 `initKeyword`라는 변수에 담고, 이를 `keyword` State의 초기값과 `getQuestions()`라는 함수의 파라미터로 넘겨줬습니다.
  - 이렇게 하면 `QuestionListPage`에서는 쿼리 값에 따라서 검색된 결과를 보여 주겠죠?

4. handleSubmit()
  - 여기서는 폼태그의 기본 동작을 막은 다음에, 
  - setSearchParams()라는 세터 함수를 이용해서 쿼리 값을 변경합니다.
  - 객체의 프로퍼티로 원하는 쿼리 값을 지정할 수 있는데요.
  - `keyword` state 값으로 객체를 만들어서 넘겨줍니다.
  - 이때 값이 없으면 쿼리를 지정하면 안된까, 조건 연산자를 사용해서 값이 없는 경우에는 빈 객체를 넘겨줍니다.
  - 이 함수를 폼 태그의 onSubmit prop으로 내려주면 됩니다.

5. 경고 메시지
  - 추가로 경고 메시지를 보여 주는 조건도 initKeyword && questions.length === 0 일 때 보여 주도록 수정하면 더 좋겠네요.

## 18. useNabigate로 페이지 이동하기
1. 버튼 눌렀을 때, 페이지 이동하기
  - handleAddWishlistClick
  - 코스 담기 할 때 실행할 함수입니다.

2. useNagivate()
  - addWishlist(course?.slug)
  - 이렇게 위시리스트에 추가한 다음에
  - 여기서 코드로 페이지를 이동시키면 되겠죠.
  - 이럴 때 React Route에는 useNavigate 라는 커스텀 Hook을 사용합니다.
  - `const navigate = useNavigate();`
  - `navigate('/wishlist');`
  - 이런 식으로 이동할 경로를 파라미터로 넘겨주고 실행하면 됩니다.

## 19. 리액트 라우터 정리
1. 리액트스러운 방법

2. 라우터
  - 리액트 라우터를 사용하려면 반드시 라우터라는 컴포넌트가 필요한데요.
  - 우리는 그 중에서도 `BrowserRouter` 라는 걸 사용했습니다.
  - 이 컴포넌트를 최상위 컴포넌트에서 감싸주면 모든 곳에서 사용할 수 있습니다.
```
import { BrowserRouter } from 'react-router-dom';

function App() {
  return <BrowserRouter> ... </BrowserRouter>;
}
```

3. 페이지 나누는 방법
  - `Routes` 컴포넌트 안에다가 `Route` 컴포넌트를 배치해서 각 페이지를 나눠줄 수 있습니다.
  - 이 때 `Routes` 안에서는 위에서부터 차례대로 `Route`를 검사하는데요.
  - 현재 경로와 `path` prop이 일치하는 `Route`를 찾습니다.
```
<Routes>
  <Route path="/" element={<HomePage />} />
  <Route path="posts" element={<PostListPage />} />
  <Route path="posts/1" element={<PostPage />} />
</Routes>
```

4. 링크
  - 리액트 라우터에서는 `<a>` 태그 대신에 `Link` 컴포넌트를 사용합니다.
  - `to`라는 prop으로 이동할 경로를 정해주면 됩니다.
```
<Link to="/posts">블로그</Link>
```

5. 하위 페이지 나누기
  - `Route` 컴포넌트 안에다가 `Route` 컴포넌트를 배치하면 됩니다.
  - 이때 하위 페이지에서 최상위 경로에 해당하는 경로는 `path` prop이 아니라
  - `index`라는 prop을 사용하면 됩니다.
```
<Routes>
  <Route> path="/"><HomePage /></Route>
  <Route path="posts" element={<PostLayout />}>
    <Route index element={<PostListPage />} />
    <Route path="1" element={<PostPage />} />
  </Route>  
</Routes>
```
  - 이때 부모 `Route` 컴포넌트에 `element`를 지정하고,
  - 이때처럼 `Outlet` 이라는 컴포넌트를 활용하면 공통된 레이아웃을 지정해 줄 수 있었죠.
```
import { Outlet } from 'react-router-dom';

function PostLayout() {
  return (
    <div>
      <h1>블로그</h1>
      <hr />
      <Outlet />
    </div>
  )
}

export default PostLayout;
```

6. 동적인 경로 다루기
  - 콜론(:)으로 시작하는 문자열을 사용하면 경로에 파라미터를 지정할 수 있었습니다.
  - 예를 들어서 아래처럼 `/posts/:postId` 라는 경로는 `/posts/123`이라던지
  - `/posts/abc`라는 주소로 접속하면 `123` 이나 `abc` 라는 값을 `postId` 라는 파라미터로 받습니다.
```
<Routes>
  <Route path="/"><HomePage /></Route>
  <Route path="posts" element={<PostLayout />}>
    <Route index element={<PostListPage />} />
    <Route path=":postId" element={<PostPage />} />
  </Route>
</Routes>
```
  - 경로 파라미터를 사용하려면 `useParams`라는 훅을 사용하면 됩니다.
```
function PostPage() {
  const { postId } = useParams();
  // ...
}
```

7. 쿼리 사용하기
  - `useSearchParams`라는 Custom hook으로 `SearchParams` 객체를 받아올 수 있는데요.
  - 이 hook은 `SearchParams` 객체와 Setter 함수를 배열형으로 리턴합니다.
  - 이때 쿼리 값은 `SearchParams`의 `get`함수로 가져옵니다.
```
import { useSearchParams } from 'react-router-dom';

function PostListPage() {
  const [searchParams, setSearchParams] = useSearchParams();
  const filterQuery = searchParams.get('filter');
}
```
  - 만약 쿼리 값을 변경하고 주소를 이동하고 싶다면 Setter 함수에 객체를 넘겨주면 됩니다.
  - 이때 객체의 프로퍼티로 쿼리 값을 지정할 수 있습니다.
  - 아래 예시는 `?filter=react`라는 쿼리로 이동하는 예시입니다.
```
setSearchParams({
  filter: 'react',
})
```

8. 페이지 이동하기
  - **Navigate 컴포넌트**
  - 리턴값으로 `Navigate` 컴포넌트를 리턴하면 `to` prop으로 지정한 경로로 이동합니다.
```
function PostPage() {
  // ...

  const post = getPost(postId);

  // post가 없는 경우 /posts 페이지로 이동
  if (!post) {
    return <Navigate to="/posts" />;
  }

  // ...
}
```
  - **useNavigate Hook**
  - `useNavigate`라는 hook으로 `navigate`함수를 가져오면 이 함수를 통해 페이지를 이동할 수 있습니다.
```
const navigate = useNavigate();

const hadleClick = () => {
  // ... 어떤 작업을 한 다음에 페이지를 이동
  navigate('/wishlist');
}
```

9. Link, Navigate, useNavigate는 언제 쓰는게 좋을까?
  - 세 가지 모두 다 페이지를 이동할 때 쓸 수 있다는 점에서 비슷한데요.
  - 이것들을 언제 사용하면 좋을지 예시랑 같이 한번 살펴 봅시다.

10. **Link**
  - **사용자가 클릭해서 페이지를 이동할 때** 사용하면 됩니다.
  - 하이퍼링크 텍스트나 페이지를 이동하는 버튼, 이미지 등에 사용하면 되겠죠?
  - 대부분의 경우 `Link` 만으로도 충분합니다.

11. **Navigate**
  - 특정 경로에서 **렌더링 시점에 다른 페이지로 이동시키고 싶을 때** 사용하면 됩니다.
  - 쇼핑몰의 회원 전용 페이지에 로그인없이 들어와서 로그인 페이지로 리다이렉트 하는 경우
  - 쇼핑몰의 상품 상세 페이지에서 제품이 품절되었거나 삭제되어서 다른 페이지로 이동시키는 경우

12. **useNavigate**
  - **특정한 코드의 실행이 끝나고 나서 페이지를 이동시키고 싶을 때** 사용하면 됩니다.
  - 쇼핑몰에서 장바구니에 담기를 눌렀을 때 리퀘스트를 보내고 장바구니 페이지로 이동시키는 경우
  - 리다이렉트된 로그인 페이지에서 로그인을 완료한 후에 처음 진입했던 페이지로 돌아가는 경우

## 20. 선택 레슨: react-helmet으로 페이지 제목 설정하기
1. `아쉬운 점`
  - 각 페잊에 들어갔을 때 페이지 제목이 바뀌지 않는다는 건데요.

2. `document.title`
  - document.title = 'Codethat - 커뮤니티';
  - 리액트스럽지 않다.

3. `react-helmet`
```
import { Helmet } from 'react-helmet';

function HomePage() {
  return (
    <>
      <Helmet>
        <title>Codethat - 코딩이 처음이라면, 코드댓</title>
      </Helmet>
    </>
  )
}
```

## 21. 싱글 페이지 애플리케이션(SPA) 이해하기
1. Link 사용 이유
  - `a` 태그가 있는데도 Link를 사용하는 이유
  - 그건 바로 우리가 만든 게
  - 싱글페이지 애플리케이션 (Sigle Page Application) 이라는 것이기 때문입니다.

2. 
  - 개발자 도구 > 네트워크
  - Request URL: http://localhost:3000

3. 클라이언트사이드 렌더링 (Client-side Rendering)
  - `<div id="root"></div>`
  - 여기 id가 root인 div 태그 안에 HTML 노드들이 있죠.
  - 이건 전부 자바스크립트로 리액트가 생성한 HTML 입니다.
  - 여기서 `클라이언트`는 `웹브라우저`에 해당하고,
  - `렌더링`은 HTML 페이지를 만드는 걸 말합니다.
  - **즉 웹 브라우저에서 자바스크립트로 HTML 페이지를 만든다는 뜻이죠.**

4. Link 컴포넌트
  - Link 컴포넌트에서는 웹 브라우저의 기본 동작 대신에 
  - 리액트 라우터를 통해서 경로에 맞는 리액트 컴포넌트를 렌더링하고
  - 주소창에 글자를 바꾸고, 웹 브라우저에 기록을 추가합니다.
  - 리퀘스트를 보내지 않고도 자바스크립트를 사용해서
  - 마치 다른 HTML 페이지를 받은 것처럼 흉내내는 거죠.
  - 이런 식의 웹사이트를 `싱글 페이지 애플리케이션`이라고 부르는데요.
  - 여기서 싱글 페이지는 하나의 HTML 문서를 말하고,
  - 애플리케이션은 마치 앱처럼 여러 페이지를 돌아다니는 사이트를 의미한다고 보시면 됩니다.
  - 즉 여러 경로의 HTML 문서를 돌아다니는 게 아니라
  - 하나의 HTML 문서 안에서 자바스크립트로 여러 페이지를 보여주는 사이트를 말하죠.

5. /courses
  - /courses라는 경로로 이동해 볼께요.
  - 리스폰스를 보면, 텅 빈 HTML을 보내주는데요.
  - 앞에서 localhost:3000으로 보낸 GET 리퀘스트랑 비교해 보면
  - 완전히 동일한 HTML 페이지 입니다.

6. root div
  - 일단은 root div에다가 클라이언트사이드 렌더링을 하는데
  - `리액트 라우터`가 주소창에 적힌 경로를 읽어서 
  - 경로에 일치하는 컴포넌트를 렌더링하는 방식입니다.

7. 개발 모드 그리고 `배포`
  - 참고로 개발 모드에서는 이런 게 알아서 설정이 되어 있었지만
  - 이렇게 클라이언트사이드 렌더링으로 리액트 라우터를 사용하는 경우에는 
  - 서버에 배포할 때 따로 설정을 해 줘야 합니다.

8. **참고자료** React 웹 개발 시작하기 - 웹 사이트 배포하기 (AWS S3)
  - 앞에서 잠깐 배웠던 배포 방식에서도 이런 설정을 해주고 있으니까
  - 혹시 다시 찾아보고 싶으시다면 영상 아래에 있는 링크를 참고해 주세요.

9. 정리
  - 클라이언트사이드 렌더링 (CSR)
  - **`웹 브라우저`에서 `자바스크립트`로 HTML 페이지를 만드는 것을 말하고,**
  - 싱글 페이지 애플리케이션 (SPA)
  - 하나의 HTML 문서 안에서 자바스크립트로 여러 페이지를 보여주는 사이트를 말합니다.

## 22. 리액트를 렌더링하는 방식
1. 대표적인 렌더링의 종류
  - 클라이언트사이드 렌더링 (Client-side Rendering)
  - 서버사이드 렌더링 (Server-side Rendering)
  - 정적 사이트 생성 (Static Site Generation)

2. 클라이언트사이드 렌더링
  - 리액트로 할 수 있는 가장 기본적인 방식의 렌더링입니다.
  - 리액트로 작성한 코드는 자바스크립트로 변환이 가능한데요.
  - 참고로 이런 변환을 `트랜스파일링`이라고 부릅니다.
  - 클라이언트사이드 렌더링은 **자바스크립트로 변환된 리액트 코드를 웹 브라우저에서 실행해서 HTML을 만드는** 걸 말합니다.

3. 서버사이드 렌더링
  - 서버에서 HTML을 만들고 리스폰스로 보내주는 것
  - 백엔드 서버에서 리퀘스트를 받으면 상황에맞는 HTML을 만들어서 리스폰스로 보내주는 방식을 `서버사이드 렌더링`이라고 합니다.
  - 서버에서 HTML을 만든다는 뜻이죠.
  - 훨씬 빨리 화면을 띄워줄 수 있고, 검색 엔진에서 좋은 점수를 받아서 검색했을 때 사이트가 잘 노출될 수 있다는 장점이 있습니다.
  - `서버에서 HTML을 만들어서 보내준다`

4. 정적 사이트 생성 
  - 미리 HTML 파일을 만들어서 서버를 배포하는 것

5. 렌더링을 활용한 리액트 기술 세 가지
  - Next.js
  - Getsby
    - 리액트로 만든 사이트를 빌드해서 손쉽게 HTML 파일로 만들 수 있습니다.
    - 회사 소개 사이트나 동아리 홈페이지 혹은 포트폴리오 사이트
  - React Native
    - 리액트로 작성한 코드를 모바일 앱으로 만들 수 있게 해 주는데요.
    - 리액트 코드로 개발하면 웹과 안드로이드와 iOS 앱에서 사용하는 공통적인 코드를 한 번에 개발할 수 있다는 장점이 있습니다.
    




