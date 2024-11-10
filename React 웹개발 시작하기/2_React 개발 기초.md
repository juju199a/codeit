# 2. React 개발 기초
## 01. 프로젝트 소개
1. 주사위 게임

2. 가위 바위 보 게임

## 02. 리엑트 최신 버전에 대한 안내
1. 최신 버전의 리액트
  - `ReactDOM.render`가 아니라 `ReactDOM.createRoot`라는 함수를 사용
  - 경고 메시지
```
Warning: ReactDOM.render is no longer supported in React 18.
Use createRoot instead. 
Until you switch to the new API, your app will behave as if it it's running React 17.
```
  - `index.js`를 아래와 같이 수정
```
import ReactDOM from 'react-dom/client';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<h1>안녕 리액트!</h1>);
```

## 03. 프로젝트 셋팅
1. 폴더 생성
  - dicegame
  - VS Code에서 열기
  - `npm init react-app .`
  - 현재 디렉토리에 프로젝트를 생성한다.
  - `npm run start`

2. 당장 안쓰는 파일들 지우기
  - 웹사이트 개발에 자주 쓰이는 파일들이 미리 만들어집니다.
  - public 안에는 반드시 있어야 하는 index.html 파일만 남기고, 나머지는 지운다.
  - index.html도 사용할 것만 남기고 지운다.
  - `head 태그`는 **인코딩을 결정**하는 `meta 태그`와
  - `body 태그`는 **root ID**를 가진 `디브 태그`남기고 모두 지웠습니다.
  - `html 태그`에는 `lang 프로퍼티`를 **ko** 한국어로 바꿔주고, 
  - `title 태그`도 **주사위 게임** 이름을 바꿔준다.

3. src 폴더
  - `index.js`를 제외한 모든 파일들을 삭제 하겠습니다.
```
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <h1>안녕 리액트!</h1>
);
```

4. 실행
  - `npm run start`

## 04. 코드잇 리액트 실행기를 알아보자
1. 코딩창 열기
  - `npm init react-app .`
  - 파일 정리하기

2. 리액트 프로젝트 실행하기
  - `npm run start`
  - `npm start`

3. 파일 수정하기
  - Compiling...

4. 다운받은 프로젝트 실행하기
  - `node_modules`라는 폴더
    - 리액트 실행에 필요한 파일들
    - 보통 Node.js로 만든 프로젝트를 공유할 때는 node_modeules폴더를 제외하고 공유하느네요,
    - 용량이 많기도 하고, 다운 받은 사람이 직접 설치할 수 있기 때문입니다.
  - package.json
```
"dependencies": {
  "react":
  "react-dom":
  "react-scripts":
}
```
  - `npm install`
    - node_modeuls라는 폴더가 만들어짐
  - `npm start`

## 05. 인덱스 파일에서 하는 일
1. `index.html`
  - 최소한으로 웹페이지가 동작하게끔 필요한 코드는 생각보다 많이 없습니다.
  - 보통 html파일에 html 태그들을 사용해서 브라우저에 그려낼 화면들을 나타냈었지만,
  - 리액트는 그러한 방식을 사용하지 않는다.

2. `index.js`
  - index.html 이 열리고 나서 실행되는 파일인데, 
  - 리액트 코드들 중에서 `가장 먼저` 실행되는 파일입니다.
  - `react-dom`이라는 패키지에서 디폴트로 익스포트 하는 객체를 ReactDOM이라는 이름으로 import 해서 
  - 이 객체에 render라는 매소드를 실행하고 있다.
  - 여기서 `render`란 화면을 그린다 라는 뜻이다.
  - 리액트에서는 render 매소드로 html 태그를 만들어 주는 것입니다.
  - render 매소드를 호출할 때 전달하는, 첫번째 아규먼트 값이 <h1> 태그이다.
  - 아규먼트 값이 문자열과 같은 값이 아니라 `html 태그를 그대로 작성했다`는 것입니다.
  - 사실 이 부분은 순수 자바스크립트 코드는 아니고, `리액트에서 지원`하는 `JSX라는 문법`입니다.
  - 실제로 이 태그는 h1 태그를 만드는 코드입니다.

4. `document.getElementById('root')`
  - DOM 요소들 중에서 root라는 ID 요소를 가져온다는 것
  - 새로운 html 요소를 만들고, 그 요소를 두번째 아규먼트 값에다가 집어 넣는 방식으로 동작합니다.
  - root 디브 태그 안에 h1 태그가 있는 것을 확인할 수 있다.

5. ReactDOM.render 메소드
  - 참고로, ReactDOM의 render 메소드는 보통 index.js 파일에서 `한번만 실행`하게 된다.

## 06. JSX
1. JSX 문법
  - 자바스크립트와 html을 섞어서 쓸 수 있는 자바스크립트의 확장된 문법이라고 생각하면 된다.
  - html 태그를 그대로 쓸 수 있다.
  - JSX는 자바스크립트 확장 문법이기 때문에, 사실 html 문법을 완전히 그대로 사용할 수는 없습니다.
  - 대표적으로 `class` 와 `for`가 있는데요.
  - html에서는 css에 class를 적용하는 속성이지만, 자바스크립트에서는 객체지향의 개념으로 클래스를 선언할 때, 
  - `class`라는 키워드를 사용하기 때문에, JSX에서 클래스 속성을 사용하려면, `className=`이라는 속성을 사용해 줘야 합니다.
  - html에서 `for`라는 속성은 라벨 태그에서 input 태그와 함께 사용되는 속성입니다.
  - 자바스크립트에서는 반복문에 사용하죠.
  - 그래서 JSX문법으로 html의 for를 사용하기 위해서는 `htmlFor=`라고 작성해 줘야 합니다.

2. **카멜 케이스**
  - 이벤트 핸들러의 이름도 조금씩 다른데요.
  - html에서 `onblur="" onfocus="" onmousedown=""` 모두 소문자로 작성했던 이벤트 핸들러들은
  - JSX 문법으로 작성할 때는 두번째 단어 부터 첫글자를 대문자로 작성해줘야 합니다.
  - `onBlur="" onFocus="" onMouseDown=""`
  - JSX는 자바스크립트에서 html 문법을 편리하게 활용할 수 있는 문법입니다.
  - 자바스크립트의 확장 문법이다 보니, 몇 가지만 주의하면 된다.

## 07. 프래그먼트
1. 꼭 지켜야 할 규칙
  - 하나로 감싸진 태그로 작성해야 한다.
  - <Fragment></Fragment>
  - 굳이 div로 감싸고 싶지 않을 때,
  - 불필요한 div 사용하지 않아도 된다.
  - `<></>` 이름 없는 축약형 
  - Fragment를 불러오지 않아도 된다.
  - 코드도 훨씬 깔끔하게 작성할 수 있다.

## 08. 가위바위보 - 간단 버전(1)
1. h1 태그의 id 속성을 id="title"로 작성했다.

2. button 태그의 class속성을 className="hand"로 작성했다.

3. 실행했을 때 불필요한 태그 없이 <div id="root">바로 아래에 h1과 button 태그가 들어 있다.

## 09. JSX에서 자바스크립트 사용하기
1. 사실 JSX는 실제로 실행될 때, 자바스크립트 코드로 `변환`되어서 실행됩니다.
  - 그래서 당연히 html 코드 뿐만 아니라 자바스크립트 코드도 함께 작성될 수도 있는데요.
  - `JSX를 자바스크립트로 변환하는 방법`에 대해선 나중에 살펴 보도록 하고, 
  - JSX에서 `html 코드와 자바스크립트 코드`를 함께 사용할 수 있는 방법에 대해서 배워 보겠습니다.

2. product 라는 변수를 만들고,
  - `const product = '맥북'`
  - 중괄호를 연 다음에, `변수 이름`을 작성해 주는 것입니다.
  - `<h1>나만의 {product} 주문하기</h1>`
  - 템플릿 문자열과 비슷할 것 같지만, $ 기호가 없다.
  - JSX 문법에서 `자바스크립트 코드`를 활용하려면, 이렇게 중괄호로 감싸주면 됩니다.
  - 중괄호 안에는 변수를 그대로 쓸 수 있을 뿐만 아니라, 자바스크립트로 된 표현식은 뭐든지 사용할 수 있습니다.
  - {product.toUpperCase()}
  - {product + model}
  - 가능하면 JSX 문법 속에서는 읽기 편하게 작성하는 것이 좋다.

3. imageUrl
  - `const imageUrl = 'https://~'`
  - `<img src={imageUrl} alt="제품 사진">`
  - 이때 {imageUrl}은 따옴표가 아니라 중괄호로 감싼다.

4. button 태그  
  - `<button>확인</button>`
```js
function handleClick() {
  alert('곧 도착합니다!');
}
```
  - <button onClick=""> (X): 따옴표가 아니라
  - <button onClick={}> (O): 중괄호를 열어서 이벤트 등록을 해 주면 됩니다.
  - <button onClick={handleClick}>

5. 중괄호
  - 중괄호 안에는 자바스크립트 표현식만 사용할 수 있기 때문에,
  - if 문이나, for 문, 함수 선언과 같은 `자바스크립트의 문장은 사용할 수 없다`는 점 꼭 기억해 주세요.


## 10. 가위바위보 - 간단 버전 (2)
1. '승리' 텍스트가 `h2`태그로 보인다.

2. 버튼을 클릭했을 때 콘솔에 `가위바위보!`가 출력된다.

## 11. JSX 문법
1. 속성명은 카멜 케이스로 작성하기
  - `onClick, onBlur, onFocus, onMouseDown, onMouseOver, tabIndex`
  - `data-*`속성은 카멜 케이스가 아니라 기존의 HTML 문법 그대로 작성해야 합니다.
```
<butto className="btn" data-status="대기중">대기중</button>
```

2. 자바스크립트 예약어와 같은 속성명은 사용할 수 없다!
  - for나 class처럼 자바스크립트의 문법에 해당하는 예약어와 똑같은 이름의 속성명은 사용할 수 없다.
  - for는 `htmlFor`
  - class는 `className` 으로 사용

3. 반드시 하나의 요소로 감싸기 - Fragment

4. 자바스크립트 표현식 넣기
  - JSX 문법에서 중괄호({})를 활용하면 자바스크립트 표현식을 넣을 수 있습니다.
  - JSX 문법에서 중괄호는 자바스크립트 표현식을 다룰 때 활용하기 때문에, 중괄호 안에서 for, if문 등의 문장은 다룰 수 없다는 점은 꼭 기억해 주세요.
  - 그런데도 만약 JSX 문법을 활용할 때 조건문이 꼭 필요하다면 `조건 연산자`를, 반복문이 꼭 필요하다면 `배열의 반복 메소드`를 활용해 볼 수는 있겠죠?

## 12. JSX 퀴즈
1. JSX 문법
  - class 속성은 `className`

2. JSX문법에서 자바스크립트 표현식
  - <img src={logoUrl}>

## 13. 컴포넌트
1. JSX를 변수에 담아서 활용
  - ReactDOM의 render 함수의 첫번 째 아규먼트 `JSX 문법으로 작성한 코드`를 바로 사용했지만,
  - 잘라내서 변수에 담아서 활용해도 잘된다.

2. 콘솔에 출력하면, 
  - `자바스크립트 객체`가 출력되는 모습을 확인할 수 있습니다.
  - 리액트에서는 이 객체를 `리엑트 엘리먼트`라고 부르는데요.
  - 리액트 엘리먼트를 `ReactDOM의 render 함수`로 전달하게 되면, 
  - 리액트가 이 객체를 해석해서, `html로 랜더링` 하는 것이다.
  - 결과적으로 `리액트 엘리먼트`는 리액트로 화면을 구성하는데 있어서 가장 기본적이면서도, 핵심적인 요소인 것입니다.
```js
const element = <h1>안녕 리액트!</h1>
console.log(element)
```

3. 커스텀 태그
  - 리액트 엘리먼트를 **함수 형태**로 만들어 내면, JSX 문법을 작성할 때, `커스텀 태그`처럼 활용 할 수도 있다.
  - 리액트 엘리먼트를 리턴하는 `Hello 라는 함수`를 만들면, element 변수에서 JSX 코드를 작성할 때,
  - `함수 이름을 가진 태그`를 사용할 수 있다는 것입니다.
  - 당연히 <Hello /> 는 Hello 함수가 리턴하는 리액트 엘리먼트를 의미하게 된다.

```js
function Hello() {
  return <h1>안녕 리액트</h1>
}

const element = {
  <>
    <Hello />
    <Hello />
    <Hello />
  </>
}

```

4. 리액트 컴포넌트
  - 이때 사용한 Hello 함수를 `리액트 컴포넌트`라고 부른다.
  - 본격적으로 리액트 개발할 때는 리액트 엘리먼트를 `리액트 컴포넌트`로 만들어서 활용하는데요.
  - 함수 이름의 첫글자를 꼭 대문자로 써야 하고,
  - 반드시 JSX 문법으로 만든 `리액트 엘리먼트`를 리턴해 줘야 한다.

5. App.js
  - 앱이라는 컴포넌트를 만든다.
  - 이 컴포넌트를 다른 파일에서도 활용할 수 있도록 마지막 줄에서는 `디폴트로 익스포트` 해 줄께요.
```js
function App() {
    return <div>App 컴포넌트!</div>
}

export default App;
```

6. index.js
  - App 컴포넌트를 브라우저에 출력해 봅시다.
  - App 컴포넌트를 불러온 다음에 `컴포넌트 태그` 형태로 넣어두도록 하겠습니다.
  - App 컴포넌트가 잘 출력되는지 확인할 수 있다.
```
import App from './App';

root.rennder(<App />)
```

7. 주사위 컴포넌트
  - assets/이미지
  - Dice.js
  - 리액트에서 이미지를 사용하기 위해서는 import 문으로 이미지 파일 이름을 정해서, 
  - 해당 경로의 이미지를 불러온 다음에, 이것을 `image 태그의 src 속성`으로 넣어 줘야 합니다.
```
import diceBlue01 from './assets/dice-blue-1.svg';

function Dice() {
    return <img src={diceBlue01} alt="주사위" />;
}

export default Dice;
```

8. Dice 컴포넌트 가져오기
  - `import Dice from './Dice';`
  - 리턴 부분을 소괄호로 감싸 주게 되면, 여러 줄에 걸쳐서 작성할 수 있게 됩니다.
  - 이렇게 하면 JSX 코드를 보다 가독성 있게 할 수 있다.

9. 이미지 안보임
  - 참고로 Dice 컴포넌트로 돌아가서,
  - html 작성하듯이 src 속성에 파일 경로를 바로 작성하게 되면, 브라우저에서 확인했을 때, 
  - **이미지를 불러 올 수 없다.**
```
function Dice() {
  return <img src='./assets/dice-blue-1.svg' alt="주사위" />;
}
```

## 14. 가위바위보-HandIcon
1. HandIcon.js
```js
import rockImg from './assets/rock.svg';
 
function HandIcon() {
  return <img src={rockImg} alt="rock" />;
}

export default HandIcon;
```

2. App.js
```js
import HandIcon from './HandIcon';

function App() {
  return (
    <div>
      <HandIcon />
    </div>
  );
}

export default App;
```

## 15. 컴포넌트 문법
1. 리액트 엘리먼트



