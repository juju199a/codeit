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
  


