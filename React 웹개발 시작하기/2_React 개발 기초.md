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
  - `JSX 문법으로 작성한 요소는 결과적으로 자바스크립트 객체가 됩니다.`
  - `이런 객체를 리액트 엘리먼트라고 부르는데요.`

2. 리엑트 컴포넌트
  - `한가지 주의해야 할 부분은, 리액트 컴포넌트의 이름은 반드시 첫 글자를 대문자로 작성해야 한다는 것입니다.`
  - `컴포넌트 이름의 첫 글자가 소문자라면 오류가 발생하니깐 꼭 주의해 주세요!`

## 16. Props
1. 컴포넌트에 속성을 지정하는 방법
  - 리액트에서 JSX 문법으로 html 태그를 작성할 때, 속성을 지정할 수 있고, 
  - 이 속성에 자바스크립트 코드가 필요하다면, **중괄호**를 활용하면 된다.
  - 그런데 html 태그 뿐만 아니라, <Dice /> 와 같은 리액트 컴포넌트에도 **속성**을 다양하게 지정할 수 있는데요.
  - `<Dice color="blue" />`
  - 오류 없음 > Elements에는 color 안보이고, Components에 color가 보인다.

2. 프롭스
  - 개발자 도구를 열어서 html 구조를 확인해 보면, color 라는 속성을 어디에서도 찾아 볼 수 없습니다.
  - 왜냐하면 우리가 작성한 color 속성은 html 태그가 아니라, `리액트 컴포넌트`에 지정해준 `속성`인데요.
  - 그래서, **리액트 개발자 도구**의 `Components` 탭에서 `Dice 컴포넌트`를 클릭해 보면, 
  - `프롭스(props)` 라는 곳에 color라는 속성에 blue라는 값이 잘 지정되어 있는 것을 확인할 수 있습니다.
  - 리액트에서는 컴포넌트에 지정한 속성을 `프롭스`라고 부르는데요.
  - 프롭스는 `프로퍼티스`의 줄임말이라고 생각하면 된다.
  - 프롭스는 컴포넌트에 전달된 속성을 모두 가르키기 때문에, 각각의 속성은 `프롭`이라고 부른다는 점도 참고해 주시기 바랍니다.
  - **앞으로 컴포넌트의 속성 대신에 프롭 이라고 부를 것이다**

3. 컴포넌트 내에서 사용
  - 컴포넌트에 지정해 둔 속성은 `하나의 객체` 형태로 컴포넌트 함수의 `첫번째 파라미터`로 전달됩니다.
  - Dice 컴포넌트 함수의 첫번째 파라미터를 props로 한다.
  - **props라는 의미를 보다 명확하게 하기 위해서 일반적으로 props를 사용한다.**
  - 리액트 개발자 도구에서 봤던 props 부분이 `바로 이 객체` 인 것입니다.

4. 빨간 주사위
```
function Dice(props) {
  const diceImg = props.color == 'red' ? diceRed01 : diceBlue01;
}
```

5. 배열로 지정
  - `템플릿 리터럴 (백틱)`을 사용하면 문자열 안에 변수를 쉽게 삽입할 수 있다. 
```js
function Dice(props) {
    const src = DICE_IMAGES[props.color][props.num-1];
    const alt = `${props.color} ${props.num}`;
    return <img src={src} alt="{alt}" />;
}
```
6. `디스츠럭팅 문법 (destructuring) 구조 분해`
  - 그런데, props 라는 값을 어쩔 수 없이 반복적으로 많이 사용하게 되었죠?
  - 이럴 땐, props를 `디스츠럭팅 문법`을 활용해서, 코드를 깔끔하게 정리할 수 있다.
  - props를 실수로 생략할 수도 있으니, 각 prop에 기본값을 지정해 줄 건데요.
```
function Dice({color="blue", num=1}) {
  const src = DICE_IMAGE[color][num -1];
  const alt = `${color} ${alt}`;
  return <img src={src} alt={alt} />;
}
```

7. App.js에서 color와 num `프롭스`를 적용
  - `<Dice color="red" num=2>`
  - 2에서 에러가 나느데, 자바스크립트의 숫자 2를 표현하려면, 그냥 쓰면 안되고, 반드시 `중괄호`로 감싸줘야만 합니다.
  - **num={2} 중괄호로 감싸줘야 한다.**


## 17. 가위바위보 - HandIcon (2)
1. value prop 추가 (destructuring: 구조 분해)
```
function HandIcon({ value }) {
  return <img src={rockImg} alt="rock" />;
}
```

2. 이미지 설정
```
const IMAGES = {
  rock: rockImg,
  scissor: scissorImg,
  paper: paperImg,
};
const src = IMAGES[value];
```

## 18. 가위바위보 - HandButton
1. button 안에 HandIcon을 배치합니다.
```
return (
  <button>
    <HandIcon/>
  </button>
);
```

2. 버튼을 클릭했을 때 handleClick을 실행하도록 button의 onClick 에다가 지정합니다.
```
const handleClick = () => onClick(value);
return (
  <button onClick={handleClick}>
    <HandIcon />
  </button>
);
```

3. value를 내려줍니다.
```
const handleClick = () => onClick(value);
return (
  <button onClick={handleClick}>
    <HandIcon value={value} />
  </button>
);
```

4. App.js에서 onClick을 실행한다.
```
const handleClick = (value) => console.log(value);
<HandButton value="rock" onClick={handleClick}/>
```

## 19. children
1. children 
  - 직접 만든 프롭 말고도, 기본적으로 존재하는 프롭이 있습니다.
  - `children`이라는 프롭이다.
  - `children`은 컴포넌트의 자식들을 값으로 갖는 프롭입니다.

3. Button.js
```
function Button({text}) {
  return <button>{text}</button>;
}
```

4. App.js
  - Button 컴포넌트에서는 text라는 prop를 사용하고 있으니까, 
```
<Button text="던지기" />
<Button text="처음부터" />
```

5. children으로 변경
  - 그런데, 리엑트에서 단순히 바로 보여지기만 하는 값을 다룰 땐,
  - 지금처럼 어떤 프롭을 만드는 것 보다는 `children`프롭을 활용하는 것이
  - 코드를 좀 더 직관적으로 구성하는데 도움이 됩니다.

6. children 프롭 확용
```
function Button({children}) {
  return <button>{children}</button>;
}

<Button>던지기</Button>
<Button>처음부터</Button>
```

## 20. 가위바위보 - 초기화 버튼
1. 샐프 채점
  - 버튼에 '처음부터'라는 텍스트가 잘 보인다.
  - App 컴포넌트에서 '처음부터'라는 문자열을 `Button 태그`로 감쌌다.

2. Button.js
```js
function Button({name, onClick}) {
  return <button onClick={onClick}>{name}</button>
}
```

3. App.js
```js
function App(){
  const handleClearClick = (value) => console.log('처음부터');

  return (
    <>
      <Button name="처음부터 onClick={handleClearClick} />
    </>
  )
}
```

4. children 수정
```js
function Button({children, onClick}) {
  return <button onClick={onClick}>{children}</button>
}

<Button onClick={handleClearClick}>처음부터</Button>
```

## 21. Props 정리하기
1. Props
  - JSX 문법에서 컴포넌트를 작성할 때 컴포넌트에도 속성을 지정할 수 있는데요.
  - 리액트에서 이렇게 컴포넌트에 지정한 속성들을 `Props`라고 부릅니다.
  - `Props`는 Properties의 약자인데요.
  - 컴포넌트에 속성을 지정해주면 각 속성이 하나의 객체로 모여서 컴포넌트를 정의한 함수의 `첫번째 파라미터`로 전달됩니다.
```js
<Dice color="blue" />

function Dice(props) {
  return <img src={diceBlue01} alt="주사위" />;
}
```

2. 속성값을 다양하게 전달
```js
<Dice color="red" num={2} />

function Dice(props) {
  const src = DICE_IMAGES[props.color][props.num - 1];
}

```

3. Destructuring 문법을 활용
```js
function Dice({color='blue', num=1}) {
  const src = DICE_IMAGES[color][num -1];
}
```

4. Children
  - `props`에는 `children`이라는 조금 특별한 프로퍼티(prop, 프롭)가 있습니다.
  - JSX 문법으로 컴포넌트를 작성할 때 컴포넌트를 단일 태그가 아니라 
  - `여는 태그`와 `닫는 태그`의 형태로 작성하면, 그 안에 작성된 코드가 바로 이 `children` 값에 담기게 됩니다.
```js
function Button({children}) {
  return <button>{children}</button>;
}

<Button>던지기</Button>
```

5. Children 활용
  - 참고로 이 children을 활용하면 단순히 텍스트만 작성하는 걸 넘어서 `컴포넌트 안에 컴포넌트`를 작성할 수도 있습니다.

## 22. Props 퀴즈
1. props를 올바르게 활용하는 코드
  - `function Profile(props)`

2. Menu 컴포넌트 안에 작성된 텍스트
  - `props.children`

## 23. State
1. 지금까지
  - 리액트 컴포넌트를 만들고, `Props`로 컴포넌트의 모습을 다양하게 변경하는 방법에 대해서 살펴봤습니다.

2. 던지기 버튼 만들기
  - 리액트 없이 html로만 구현한다면, 주사위 마다 html 페이지를 만들고 이동시키거나,
  - 또는 자바스크립트로 html 요소 노드의 속성만 새롭게 바꿀 수 있다.

3. 리액트
  - 하지만 리액트에서는 이런 경우에 사용하는 핵심기능이 있습니다.
  - 바로 `State`입니다. 
  - `State`는 변수 같은 건데, State를 바꾸면, 리액트가 알아서 `화면을 새로 랜더링` 해 주는 것입니다.

4. State 사용
  - `import {useState} from 'react';`
  - 리액트 패키지에서 useState라는 함수를 불러 와야 한다.
  - 불러온 useState()는 일반적으로 이렇게 작성합니다.
  - `const [num, setNum] = useState(1);`
  - useState 함수는 파라미터로 초기값을 전달 받고, 이 함수가 실행된 다음에는 `배열의 형태`로 요소 2개를 리턴한다.
  - 배열의 `디스스트럭팅` 으로 작성합니다.
  - 배열의 두 요소 중에서, 첫번째 요소 `num`은 스태이트 값이다. 현재 변수의 값을 나타내는 변수입니다.
  - 처음에는 초기값을 가지고 있다.
  - 두번째 요소는 `setter 함수`인데요. 이 함수(setNum)를 호출할 때, 파라미터로 전달하는 값으로 State 값이 변경이 되는 겁니다.
  - State를 사용할 때는, `num 변수`에 새로운 값을 할당 하면서 변경하는 것이 아니라, 
  - 반드시 이 `setter 함수` (setNum)를 통해서만 변경해야 하는데요.
  - 그렇기 때문에 변수에 `const 키워드`로 선언하고, setter 함수의 이름도 (어떠한 이름을 지어줘도 상관 없지만)
  - 일반적으로 State 이름 앞에 set을 붙인 형태로 짓는 겁니다.

3. 간단한 주사위 기능 버전
  - `<Dice color="red" num={num} />`
  - `handleRollClick`
```js
const handleRollClick = () => {
  setNum(3);
}
```
  - 이 함수를 던지기 컴포넌트에 onClick Props로 전달해준 다음에, 
  - `이 Button에 대해서는 onClick의 Props에 대한 처리가 없다`
  - 그러니까 Button 컴포넌트로 돌아가서, onClick Props를 받은 다음에, 
  - `onClick 이벤트`에 `onClick Prop`을 등록해 주도록 하겠습니다.
```js
function Button({children, onClick}) {
  return <button onClick={onClick}>{children}</button>;
}
```

4. Random하게 바꾼다.
```js
function random(n) {
  return Math.ceil(Math.random() * n);
}
```
  - 이 함수는 파라미터 n으로 숫자값을 전달 받아서, 1~n까지 숫자를 랜덤하게 반환하는 함수입니다.
  - `const nextNum = random(6);`

5. handleClearClick 함수
```js
const handleClearClick = () => {
  setNum(1);
}
```

5. 정리
  - State는 리액트에서 화면을 변경할 때 활용하는 굉장히 핵심적인 개념입니다.
  - 리액트에서는 `State값`이 변경될 때마다, 화면을 새롭게 랜더하기 때문인데요.
  - 컴포넌트에서 State를 사용하려면 useState를 불러와야 한다.
  - 이 함수는 State와 setter 함수를 `배열 형태`로 리턴하는데요. 
  - 그렇기 때문에 `디스츠럭팅`으로 작성한다는 것도 배웠다.

## 24. 가위바위보 - 패 고르기
1. state 추가하기
  - `const [hand, setHand] = useState('rock');`
  - `const [otherHand, setOtherHand] = useState('rock');`

2. state 값 변경하기
  - hand의 값을 nextHand로 바꿔 주세요.
  - otherHand의 값을 generateRandomHand()의 리턴 값으로 바꿔주세요.
```js
const handleButtonClick = (nextHand) => {
  setHand(nextHand);
  setOtherHand(generateRandomHand());
}
const handleClearClick = () => {
  setHand('rock');
  setOtherHand('rock');
}
```

3. INIT_VALUE라는 상수로 지정
  - `const comparison = compareHand(me, other);`

## 25. 참조형 State
1. 총점을 계산하는 기능, 매번 점수를 기록하는 기능
  - `배열`이나 `객체` 같은 참조형 State를 다룰 때, 주의해야 할 점에 대해서 알아 보겠습니다.

2. 총점
  - `const [sum, setSum] = useState(0);`
  - setSum(sum + nextNum);
  - setSum(0);
  - {sum}

3. 기록
  - 배열로 만들면 된다.
  - `const [gameHistory, setGameHistory] = useState([]);`
  - gameHistory.push(nextNum);
  - setGameHistory(gameHistory)
  - setGameHistory([]);
  - {gameHistory.join(',')}
  - **사실 이것은 잘못된 방법입니다.**

4. 자바스크립트의 기본형과 참조형
  - 배열은 기본형이 아니라, 참조형입니다.
  - gameHistory 변수는 기록들을 가진 배열 자체의 값을 가지는 것이 아니라, 
  - 그 배열을 가리키고 있는 주소값을 가지고 있는 것이죠.
  - method를 이용해서 배열의 새로운 값을 넣더라도, gameHistory에서 가지고 있는 `배열의 주소값`은 전혀 변하지 않는 것입니다.
  - `배열의 요소가 바뀌긴 했지만, 변수들이 가지는 주소값`은 그대로이기 때문에, 이런 현상이 발생한 것입니다.
  - 리액트의 입장에서도 State 값이 바뀌어야 새롭게 화면을 랜더하게 되는데요.
  - **그래서 배열이나 객체 같은 참조형 타입을 변경할 때는 아애 전체를 새로 만든다고 생각하는 것이 좋다.**

5. 새로운 값으로 만들기
  - 가장 간단한 방법은 `스프레드 문법`을 활용하는 것입니다. 
  - `setGameHistory([...gameHistory, nextNm])`
  - 빈배열 안에서 gameHistory State를 펼쳐주고, 새로 추가할 요소를 붙여주면, `간단하게 새로운 배열`을 만들 수 있다.
  
## 26. 가위바위보 - 승부 기록
1. 기록을 배열로 만든다.
  - `const [gameHistory, setGameHistory] = useState([]);`

2. 새로운 기록 저장
  - `const nextHistoryItem = getResult(nextHand, nextOtherHand);`

3. 새로운 값 만들기
  - `setGameHistory([...gameHistory, nextHistoryItem]);`

4. 배열 표현
  - `<p>승부기록: {gameHistory.join(',')}</p>`

## 27. 가위바위보 - 배점
1. `e.target.value`
  - 이벤트 핸들러에서 input의 value 속성을 참조하려면 `e.target.value`와 같이 가져올 수 있는데요.

2. Number 생성자를 써서 숫자형으로 변환해 줘야 합니다.
  - `const num = Number(e.target.value)`

3. 1~9 사이만 받아 드리는 방법
  - `let num = Number(e.target.value);`
```js
const handleBetChange = (e) => {
  let num = Number(e.target.value);
  if (num > 9) num %= 10;
  if (num < 1) num = 1;
  num = Math.floor(num);
  setBet(num);
}
```

## 28. State 정리하기
1. State
  - `상태가 바뀔 때마다 화면을 새롭게 그려내는 방식`

2. useState라는 함수를 활용
  - `import { useState} from 'react';`

3. Destructing 문법으로 작성
  - `const [num, setNum] = useState(1);`
  - 첫 번째 요소가 바로 state
  - 두 번째 요소가 이 state를 바꾸는 setter 함수

4. 이벤트 핸들러를 등록
  - 그래서 아래 코드처럼 setter 함수를 활용해서 이벤트 핸들러를 등록해 두면,
  - `이벤트가 발생할 때마다` 상태가 변하면서 화면이 새로 그려지는 것이죠!

5. 참조형 State
  - Spread 문법(...)
  - `setGameHistory([...gameHistory, nextNum]);`

## 29. State 퀴즈
1. state를 만들때 활용하는 함수
  - 리액트에서 state를 만들기 위해서는 useState라는 함수를 활용해야 합니다.

2. state에 대한 설명으로 올바르지 않은 것은?
  - let 키워드로 state를 선언하면 직접 state값을 변경할 수 있다. (X)
  - 반드시 setter 함수로 변경해야 한다.

3. addMember 함수는 state가 제대로 변경되지 않는 오류가 있다. 이를 해결하라
```
const addMember = (name) => {
  setMembers([name, ...members]);
};
```
  - 참조형 state를 활용할 때는 반드시 새로운 참조형 값을 만들어 state를 변경해야 하는데요.
  - 가장 간단한 방법은 `Spread 문법(...)`을 활용하는 겁니다!

## 30. 컴포넌트가 좋은 이유
1. 리액트 개발은 곧 컴포넌트 개발이다.

2. 웹페이지를 부품으로 나눈다.
  - 네비게이션 바
  - 동영상 뷰어
  - 동영상 설명
  - 댓글 창
  - 관련 영상 목록

3. 컴포넌트의 장점
  - 반복적인 개발이 줄어든다.
  - 오류를 고치기 쉽다.
  - 일을 쉽게 나눌 수 있다.

## 31. 컴포넌트 재사용하기
1. `Board.js`
  - App.js를 그대로 붙인다.
  - App() -> F2 -> Board()

2. name과 color 라는 props를 만들어준다.
  - `function Board({name, color})`
  - 나 > {name}
  - color='blue' => color={color}

3. App.js
  - `<Board name="나" color="blue">`
  - `<Board name="상대" color="blue">`

4. `스테이트 리프팅`
  - `하나의 이벤트`로 `두 컴포넌트`를 다뤄야 하니까,
  - 각 컴포넌트의 데이터도 한 곳에서 관리하는 것이 좋을 것 같죠?
  - Board 컴포넌트의 State들을 부모 컴포넌트인 App 컴포넌트로 가져와야 합니다.
  - 상대 주시위도 만들어 줘야 한다.
  - 참고로, 자식 컴포넌트의 State를 부모 컴포넌트로 올려 주는 것을 `State 리프팅`이라고 하는데요.

5. `이벤트 핸들러도 가지고 온다.`
  - handleRollClick
  - handleClearClick
  - nextOtherNum으로 수정

6. Board 컴포넌트에 State로 전달
  - State들을 각 Board 컴포넌트에 적절한 프로브로 전달해 주면 마무리가 된다.
  - `<Board name="나" color="blue" num={num} sum={sum} gameHistory={gameHistory} />`

## 32. 코드 정리하기
1. 주사위를 던진 기록만 있으면, 총점에나 현재 주사위의 값은 충분히 구할 수 있는 값들입니다.
  - myHistory / otherHistory
  - myNum

2. num과 sum 계산
  - `const num = gameHistory[gameHistory.length - 1] || 1;`
  - `const sum = gameHistory.reduce((a,b) => a + b, 0);`

## 33. 리액트가 렌더링하는 방식
1. 리액트의 랜더링
  - 리액트 컴포넌트는 props와 state를 써서, 데이터마다 다른 화면을 보여 줄 수 있었는데요.
  - state가 바뀔 때 랜더링 하는 방식을 알아보겠습니다.
  - 이렇게 여러 요소를 직접 변경하는 것은 번거롭기도 하고, 실수라도 하면, 
  - 일부만 업데이트 되어서, 버그가 발생하기도 쉽습니다.
  - 그래서 리액트에서는 쉽고 단순한 방법을 사용한다.
  - `새로 랜더링 하는 겁니다.`

2. `Virtual DOM (가상 DOM)`
  - 던지기 버튼을 눌렀을 때, `직접 요소가 변경되는 것이 아니라 State 값`이 변경 되는데요.
  - 이때 리액트가 App 함수를 실행하면서, 새로운 `State 값`이 적용된 앨리먼트를 리턴하는 겁니다.
  - `어디가 변경되었는지 신경쓸 필요도 없이` 통채로 다시 랜더링 하는 것이죠.
  - 이렇게 랜더링 하면 문제가 한가지 있습니다.
  - `던지기 버튼`과 같이 아무 변화 없는 요소들도 매번 다시 랜더링 된다는 것인데요.
  - 이러한 문제점을 해결하기 위해서, 리액트에서는 `Virtual DOM`이라는 것을 활용합니다.

3. DOM 트리
  - window(전쳑객체) > document > html > head와 body
  - 기본적으로 html 요소들은 `DOM 트리`라는 자료 구조로 되어 있는데요.
  - 마찬가지로 `리액트 내부`에서는 `DOM 트리`를 본 따서 만든 `Virtual DOM`이라는 자료구조를 사용합니다.
  - 그래서 앨리먼트를 새로 랜더링할 때, 리액트는 그 모습을 `실제 DOM 트리`에 바로 반영하는 것이 아니라,
  - 일단은 `Virtual DOM`에다가 적용합니다.
  - #root > App > div > button, p, p
  - App 컴포넌트 아래의 트리를 모두 지우고, `App 컴포넌트`를 새로 랜더링 하는 것입니다.
  - 중요한 것은 실제 `DOM 트리`에 바로 반영하는 것이 아니다.
  - 화면을 바꿀 준비만 하고, 실제로는 반영하지 않았다.
  - 리액트가 State 변경 전의 `Virtual DOM`과 State 변경 후의 `Virtual DOM`을 비교하는 것입니다.
  - 바뀐 부분만 찾아낸 다음에, 각각에 해당하는 `DOM 노드`를 변경하는 것이지요.

4. 장점
  - 개발자가 `DOM 노드`를 직접 신경쓸 필요가 없다.
  - 단순하고 깔끔한 코드를 작성할 수 있다.
  - 리액트 컴포넌트를 작성할 때는, 무슨 데이터를 어떻게 보여줄 것인지만을 신경쓰면 되는 것입니다.
  - 두번째는 변경 사항들을 리액트가 적당히 모아서 처리할 수 있다.
  - 리액트는 `Virtual DOM`이 바뀔 때마다 브라우저에 바로 전달하지 않고, 
  - 변경사항을 모아 뒀다가 일감을 적당히 나눠서 `브라우저`에 전달합니다.
  - 변경사항들을 효육적으로 처리할 수 있다.

## 34. 인라인 스타일
1. `style 속성`
  - <button style=''>
  - html 스타일 속성처럼 리액트에서도 인라인 스타일은 `style 속성`을 지정해 주면 됩니다.
  - 그런데, 리액트에서는 html에서와는 다르게 문자열이 아니라 `객체`로 스타일 속성값을 지정해 줘야 하는데요.
  - 객체 형태의 스타일 변수로 만들어 봤습니다.
```
const style = {
  속성: '값',
  background-color:'pink'; (X)
  -> backgroundColor: 'pink'; (O)
};
```
  - `style = {style}`

2. 인라인 스타일
  - 변수에 담지 않고, 바로 객체 형태의 값을 속성값으로 작성할 수 있다.
  - `하지만 추천안함`
```
<button style={{backgroundColor:'yellow'}}>
```

3. `style 만들기 (스프레드 문법)`
  - baseButtonStyle
  - blueButtonStyle = {...baseButtonStyle,}
  - redButtonStyle = {...baseButtonStyle,}

4. color 받기
  - `const style = color === 'red' ? redButtonStyle : blueButtonStyle;`

## 35. 가위바위보- HandButton 인라인 스타일
1. style prop으로 객체를 넣어주면 된다.
  - 인라인 스타일을 지정하려면, `style prop`으로 객체를 넣어주면 되는데요.
  - 프로퍼티 이름을 CSS 속성명으로, 프로퍼티 값을 CSS 속성값으로 하면 된다.
  - 카멜 케이스로 쓴다.
  - `이미지 주소는 import 구문을 통해서` 가져온 값을 템플릿 문자열로 넣어주면 된다.
  - `import backgroundImg from './assets/purple.svg';`
  - backgroundImage: `url('${backgroundImg}')`,

## 36. CSS 클래스네임
1. CSS 임포트
  - CSS 클래스를 사용해서, 컴포넌트에 디자인을 입히는 방법을 살펴 보겠습니다.
  - 우리가 생성한 프로젝트에는 유용한 기능하나가 있는데요.
  - `자바스크립트 파일`에서 `CSS 파일을 임포트` 하는 기능입니다.

2. index.css
  - index.css 만들기
```
body {
  background-color: #191f2c;
  color:#fff;
}
```

3. 자바스크립트에서 부르기
  - index.js 에서 
  - `import './index.css';`
  - 임포트 다음에 바로 파일 경로를 붙여준다.

4. Button.css
  - ./Button.css를 만들고,
  - CSS 코드를 작성한다.
  - .Button: 기본적인 버튼 스타일은 버튼 클래스로 작성하고, 
  - .Button.blue : 색깔 부분은 블루와 레드로 작성한다.
  - .Button.red

5. CSS 임포트
  - `import './Button.css';`

6. **클래스 네임값**
  - 컴포넌트 함수 내부에서는 `컬러 프룹`에 따라서 
  - `스타일 객체값`이 바뀌는 것이 아니라, `클래스네임값`이 달라지게 해야 한다.
  - const style = color === 'red' ? redButtonStyle : blueButtonStyle;
  - `const classNames = 'Button ${color}';` 으로 바꿔줘야 한다.
  - 클래스 네임을 추가할 때, `빈공백`이 필요하다. 
  - 공백이 없으면 하나의 클래스로 인식한다.
  - <button에도 `스타일 속성`이 아니라 `클래스 네임 속성`의 classNames를 지정해 줘야 한다.
  - style={style} => `className={classNames}`

7. color의 기본값 
  - color='blue'

8. 꿀팁
  - className을 사용할 때 유용한 꿀팁
  - 스타일을 보면, CSS 스타일 속성 중에는 여백을 주는 margin과 같은 요소 내부 보다는 외부에 영향을 주는 속성들이 있습니다.
  - 이런 속성은 컴포넌트 내부 보다는 `외부에서 정리`를 하는 것이 좋은데요.

9. Button({className = ''}) 추가
  - `const classNames = 'Button ${color} ${className}';`
  - 이렇게 하면 컴포넌트 태그를 작성할 때, 전달한 className이라는 프룹이 
  - 마치 `html 태그의 className을 사용`하는 듯한 결과로 이어진다.

10. App.css를 만들고,
  - `button의 margin 지정`
```css
.App .App-button {
  margin: 6px;
}
```

11. App.js에서 CSS파일 불러온다.
  - import './App.css';
  - <div className="App">
  - `className이라는 프룹`을 통해서, Button에 `App-button` 클래스가 생기고, 
  - 버튼간의 여백이 잘 생겨난다.
  - 한가지 의문이 생긴다.
  - Button 스타일은 Button 컴포넌트에서 다루는 것이 좋을 것 같은데, 왜 굳이 `부모 컴포넌트`에서 지정해 주는 걸까요?
  - 자식 요소들 간에 여백을 조정할 수 있으니까, 훨씬 더 직관적으로 스타일을 다룰 수가 있게 되는 것입니다.
  - 버튼의 내부적인 스타일은 당연히 버튼 내부에서 다루는 것이 훨씬 더 좋겠지만,
  - 마진과 같이 `요소의 외부적으로 영향을 끼칠만한 스타일 속성`은 요소 주변에 어떤 요소들이 더 배치될지
  - 훨씬 더 잘 아는 App 컴포넌트에서 다루는 것이 더 좋다는 의미인 것이죠.
  - className 속성과 props를 잘 활용하면, 컴포넌트를 재사용하고, 디자인을 입히는데도, 도움이 된다는 점

## 37. 가위바위보 - HandButton 클래스네임 적용
1. `HandButton.css 생성`

2. `HandIcon에 className props 보내기`

## 38. 디자인 적용하는 방법과 팁
1. 이미지 불러오기
  - `<img src={diceImg} alt="주사위 이미지">;`

2. 인라인 스타일
 - 리액트에서 `인라인 스타일`은 문자열이 아닌 객체형으로 사용합니다.
 - 프로퍼티 이름은 CSS속성 이름으로, 프로퍼티 값은 CSS 속성 값으로 쓰는데요,
 - 이때 프로퍼티 이름은 아래의 boarderRadius 처럼 대시 기호 없이 카멜케이스로 써야 한다는 점도 꼭 기억해 두세요.

3. CSS 파일 불러오기
  - `import 구문으로 파일을 불러올 수 있는데요, 이때 from 키워드 없이 쓰면 됩니다.`
  - `import './Dice.css';`

4. 클래스네임 사용하기
  - CSS 파일에 정의된 클래스명을 className prop에 문자열로 넣어주면 됩니다.

5. `classnames` 라이브러리

## 39. 디자인 적용 퀴즈
1. 컴포넌트에 이미지 파일을 제대로 불러온 코드
  - `import logLight from './assets/logo-light.png';`
  - `import logDart from './assets/logo-dark.png';`
  - const logoUrl = mode === light ? logoLight : logoDark;
  - return <img src={logoUrl} alt="logo" />

2. 인라인 스타일 방식
  - `리액트에서 인라인 스타일은 문자열이 아닌 객체형으로 사용해야 합니다.`

3. CSS파일 불러오기
  - 리액트에서는 import 구문으로 CSS파일을 불러올 수 있는데요. 이때 from 키워드는 생략할 수 있습니다.
  - props에서 `className prop을 전달`받을 수 있도록 하면 재사용성이 훨씬 더 높아진다는 점
  