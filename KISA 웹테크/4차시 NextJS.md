키발급관리
38822ae27494db7feee3341504461c69

### 1교시

서버사이드 랜더링 중에서 인기가 많다.
버쎌 - 독주하는 분위기
리엑트를 기반으로 한다.
리엑트를 할 건데, 시작을 Next.js 로 시작하는 분도 있다.
실제 사용 하는 것을 써 먹으면 된다.
node.js를 기반해서 
셋팅이 필요 한 것을 말씀 드린다.
StackBlitz : 웹프라우저 상에서 개발 도구를 소개 한다. 테스트 목적에서 사용한다.
웹 어셈블리리를 이용한다.
next.js 13.5.1
13버전 부터 서버 버전이 돌아간다.

# Next.js
## JSX
Javascript + XML
리엑트에서 사용하는 기본 문법/파일 형식
자바스크리브에서는 .js .jsx 사용 -> .js 로 통합
타입스크립트에서는 .tsx 만 사용

jsx 같은 경우에는 어렵다는 하는 경우가 많은데, javascript가 어렵다.
jsx에서만 사용하는 것만은 아니고, jsx만 두면 복잡한 것은 아니다.
jsx 
클래스 컴포넌트이거나
함수 컴포넌트 이다. (신규는 거의다 함수 컴포넌트이다.)
각각 라이프 사이클은 다르다.
자바스크립트 형태의 함수형태이다.
1. 자바스크리브 파트가 있고, 2. XML 파트가 있다.
JSX 노드라고 부르거나 
HTML과 CSS이다.
HTML 규칙과 다른 것이 있다. className - 자바스크립트의 class가 예약어이다.
XML의 특성인데, 단독 태그를 사용할 수 없다.
<br/> <input/> <img/> 닫는 태그와 같이 사용한다.
중괄호의 표현이 있다. { /* javascript */} 자바스크립트가 들어간다.
이유는 여러가지가 있지만, const key = 'key'; 중간에 값을 출력하고 싶을 때, { key } 
XML 안에 Javascript가 들어간다. 그래서 JSX이다.
{array.map( item ==> <div>{item}</div>)}
자바스크립트 문법이다.
계속 중첩된다.
자바스크립트에서 깊게 파면 된다.
리엑트, 리엑트 퍼블리싱, 프론트엔드 
XML안에서 돔 구조를 많이 터치한다.
스타일에 대한 부분 style = "text"
인라인으로 하는 것은 지원하지 않는다. 반드시 오프젝트 형테로 들어가야 한다.
style = {{tetDecoration:'underline}}
const inLineStyle = { textDecoration: 'underline'}; 인라인 스타일
JSX 특성을 가지고 있다.
XML 파트에 넣는다.

### 2교시
이유는 서버사이드 랜더링 때문에 사용한다.
리액트
소스코드를 보게 되면 프론트엔드 단에서 랜더링 된다.
내용이 하나도 반영이 이유는 검색의 내용에 반영이 하기 어려워진다.
head 아네 metadata 넣으면 
next.js 에서 기대 하는 것은 
html 서버단에서 랜더링을 하고 던진다.
서버사이드 랜더링
표준인 것처럼
서버사이드 별도로 구축하면 험난하다.
Next.js 가 알아서 
AppRoute 적용 전에도 
13버전 부터 리엑트 서버 컴포넌트
프론트 엔드 하는 
서버 컴포넌트와 

## RSC 리엑트 서버 컴포넌트
기존의 컴포넌트와 별도로 구분하지 않지만, 서버 컴포넌트, 기존 것은 클라이언트 컴포넌트로 부른다.
서버 컴포넌트는 서버에서만 작동하는 것이고, 

console.log( 'Home Compnent' );
서버가 실행되고 있는 터미널
웹브라우저의 개발자 콘솔

서버에서만 동작
클라이언트에서는 단순 html만 랜더링

NewComponent.tsx
'use client';

export function NewComponent() {
    console.log('New Component');
    return <>New Comonent Here</>
}

화면에 추가는 되는데, 개발자 로그에는 안찍힌다.
클라이언트 컴포넌트는 시작줄에 "use client" 선언으로 구분
Next 12 버전 이전은 
이전에는 구분이 명확하지 않았다.
서버 컴포넌트, 클라이언트 컴포넌트 양쪽에서 다 처리했다.
불필요한 연산을 많이 한다.
컴포넌트를 작성할 때, 클라이언트 
상태관리 카운트 
이미지 슬라이드를 하는 것은 
검색봇 javascript effect 서버단에서는 필요가 없다.
//document, window 웹 브라우저에서만 사용되는 객체들에 접근
웹브라우저에 접근 하는 코드는 예외 작업이 필요하다.
클라이언트 컴포넌트는 시작줄에 'use client' 를 선언
클라이언트 컴포넌트 이다 라고 선언
서버 컴포넌트, 클라이언트 컴포넌트 할 수 있는 것과 할 수 없는 것이 
서버 컴포넌트는 async function 을 선언 할 수 있지만, 
클라이언트 컴포넌트는 async function 선언할 수 없다.
서버 컴포넌트로 구분해서 동작한다.
서버 컴포넌트는 클라이언트 컴포넌트를 대체할 목적으로 나온 것은 아니다.
공식 홈페이지 > Docs > 
리엑트로 페이지 만들면 페이지 전체가 동적으로 만들 때가 있다. 웹어플리케이션으로 만들 때가 있다.
상단의 메뉴는 정적인 영역이다.
CSS horbor 
왼쪽 메뉴는 자바 스크립트
트리는 접었다 폈다 인터렉트이다.
리액트 이용해서 페이지 만들어진다.
로그인 페이지는 
정적인 페이지들은 클라이언트에서 동작할 필요가 없다.
자바 스크립트 
역할을 분리해서 서버 컴포넌트는 정적인 컨텐츠 담거나, 서버에서 수행해야 하는 작업들
클라이언트 컴포넌트 - 사용자 인터넥션이 필요한 내용을 담음
결국은 서버 컴포넌트 와 클라이언트 컴포넌트의 역할을 어떻게 나눌 것인가.
서버 컴포넌트와 클라이언트 컴포넌트 
react server components
React 스팩이다.
한번 읽어 보면 좋은 내용이 많다.
async 란 무엇인가.
유의하실 규칙 
1. 서버 컴포넌트 안에 클라이언트 컴포넌트가 들어갈 수 있음ㅁ
2. 클라이언트 컴포넌트 안에 서버 컴포넌트가 들어갈 수는 없음

- page.tsx : 페이지 표시를 위한 서버 컴포넌트
    - Form.tsx : 사용자 입력 폼을 처리하는 클라이언트 컴포넌트
        - ErrorView.tsx : 에러 출력을 위한 서버 컴포넌트 << 오류 발생한다.
    - UserInfo.tsx : 로그인 후 사용자 정보가 표시되는 서버 컴포넌트
        - EditButton.tsx: 사용자가 클릭할 수 있는 수정 모드 전환 클라이언트 컴포넌트 << 이것은 OK이다.

가능하면 단계가 복잡하면 안된다.
가능하면 데이터 핸들링을 위에서 해라. 규칙들이 필요하다.

컴포넌트 두개 만들어다.
접속 시각: { new Date().toISOString() }
<NewComponent />

서버에서 계산해서 나온 시각
클라이언트 컴포넌트에는 const [date, setDate] = useState(new Date());

import { useState, useEffect } from 'react';

useEffect() => {
    setInterval() => {
        setDate(new Date());
    } , 500);
}, []);
return <>현재 시각 : {date.toISOString()} </>;
}

## 주소

app > page-2 > page.tsx
디렉토리 구조가 주소가 되는 구나
주소로 사용하는 것은 아니지만 만드는 파일이 
page.tsx만 주소가 된다.
index.tsx 가 주소가 되지는 않는다.
page-2/AdditionalComponent.tsx 주소가 되지는 않는다.
page-2/page-2/depth-2/page.tsx
export default async
컴포넌트를 만들 때, components
app 밖은 routing 과 관련이 없다.
앱 안에 있는 주소만 활용이 된다.
page.tsx 약속된 파일이다. 대표 파일이다.
미리 약속되어 있는 파일이 있다.
layout.tsx template.tsx
layout.tsx 파일 열면 만들면 html 안에 body가 있다.
컨텐츠 안에 감싼다.
medadata는 있으면 좋지만, 비운다.
RootLayout 은 이름이 상관이 없다.
default function 이
children: React.ReactNode;
flex flex-col min-h-screen
<header></header>
<div> {children} </div>
<footer className="py-4 border-t"></footer>

모든 페이지만 모든 동일한 레이아웃을 보여주는 것은 아니고, 상하관계가 있을 수 있다.
로그인 페이지는 헤더랑 풋터랑 안붙는다.
sign-in page
export default async function Page() {
    sign-in
}
A side가 추가가 필요하다.
depth-2/layout.tsx
type Props = {
    children: React.ReactNode;
}

export default async function layout() {
    return <div>className='flext w-full'
        <aside className="w-">
        
    </div>
}

layout 중첩이 되다. 재정의가 된다.
export default async function Page() {
    return <>depth 3</>
}

초기에 결정하는 것이 좋다
특이한 패턴을 사용할 수 있다.
디렉토리 이름에 (header-footer-layout) page-2를 통채로 옮기면
실제 주소에는 반영이 되지 않는다. 라우터 그룹이다.
layout.tsx 
export default async function Rootlayout() {
    return <header>
    <div>
    <footer>
}

template 를 이야기 한다.
template.tsx
'use client';
import {usePathname} from 'next/navigation';

export default function Template({children}:{children:React.ReactNode}) {
    const pathname = usePathname(); // react hook 은 클라이언트에서만 사용됨 // react 19이후로는 달라질 수 있음
    return <>{children}</>;
}

layout은 서버 컴포넌트와 같은 역할 (보통 이것으로 작성함)
template은 클라이언트 컴포넌트이다.
layout으로 작업하다가 필요한 경우 template로 작성한다.
두개가 다 있으면, layout 밖으로 children이 template으로 들어간다.
실제 UI에 관한 것은 아무 것도 안넣는 것도 있다.
useEffect(() => {

} , []);
UI는 layout으로 남겨 두는 것이 좋다.
template은 안쓴다.


언인스톨 + 인스톨 반복 과정을 매니저 해준다. node manager

node -v 
v20.15.0

npx -v 
10.7.0

npm -v 
10.7.0

버전 확인

pnpm 을 사용 가능

코드 에디터는 Visual Studio
Web Storm 

메모장은 사용 금지
(특수 문자가 끼어 들 수도 있다.)

자동 설치 방법
매뉴얼로 하는 경우는 별로 없음

자동 설치 방식
npx 

프로젝그 이름
TypeScript를 사용할 거야?
> TypeScript 냐? Javascript 냐?
> 엄격하게 써야 한다.
ESLint?
> 코드 컨벤션, 어긋났을 때 알람을 띄어준다.
> 왠만하면 켜 준다.
Tailwind CSS?
> 취양되로 한다.
> Tailwind Next.js가 제일 앞에 있다.
> 많이 쓴다.
src를 사용할 것인가?
> 디렉토리 구조가 app/components /utils / ...
> src / app / components / utils / ...
> 정리하는 단계이다.
> 설정 변경이 필요하다.
> 선호의 문제이다.
App Router 사용할 거냐?
> 서버 컴포넌트 App Router (이전 버전은 Page Router냐)
import alias ?
> app / page-2 / depth-2
> import 할 때, 
import { ComponentName } from '../../components/atoms/Button.tsx';
//alias 사용
import { ComponentName } from '@/components/atoms/Button.tsx';
alias를 사용하는 경우 @을 사용 하는 것 말고 다른 것으로 사용한다.

npx create-next-app@latest

Yes
Yes
Yes
Yes
Yes
No


src/page.tsx를 변경

cd my-app
npm run dev

yarnpkg.com
yarn 은 무엇인가.
pnpM 은 무엇인가.
bun 은 무엇인가.

npM은 성능 개선이 안되었는데, Bun
타입스크립트 지원
node JS 가 성능 개선을 많이 했다.
next.js 서비스 들이 생겼으면 좋겠다.
패키지 매니저는 무엇인가.


pnpm create next-app@latest pnpm-demo

영화관리진흥원
https://www.kobis.or.kr/kobisopenapi/homepg/main/main.do

키발급관리
38822ae27494db7feee3341504461c69
(일 300회)
일별 박스 오피스

REST 방식

http://www.kobis.or.kr/kobisopenapi/webservice/rest/boxoffice/searchDailyBoxOfficeList.xml

현재 작업에서 어디에 있는지

package.json이 제일 중요하다.
경로를 주의를 해야 한다.

## 프로젝트 경로 관리
- / : 작업물을 모아놓은 상위 디렉토리
- /project-name
    - /package.json
- /first-project
    - /package.json
    - /second-project
        - /package.json 이 또 생긴다.
상위 디렉토리에도 package.json이 있고, 현재 디렉토리에 package.json이 또 생김
- /third-project
    - /package.json 관리를 해야 한다.

npx create-next-app@latest
movie
cd movie
npm run dev


layout.tsx 정리

page.txs
async 추가

JSON을 자바스크립트 관점에서 보면
const har = "a";
const chars = ["a", "b", "c"]; //string[] 배열이다.

<li>{json.boxOfficeResult.dailyBoxOfficeList[0].movieNm}</li>,
          <li>{json.boxOfficeResult.dailyBoxOfficeList[1].movieNm}</li>,
          <li>{json.boxOfficeResult.dailyBoxOfficeList[2].movieNm}</li>


하나씩 작성을 하는 것이 아니고, map 함수를 사용한다. for 사용하지 마라.

<ol>
          {
            json.boxOfficeResult.dailyBoxOfficeList.map((item: any) => (
              <li key={item.rank}>{item.rank}위 - {item.movieNm}</li>
            ))
          }
        </ol>


몇 가지 추가 하는 내용은 잠시 후에 한다.

날짜 관련한 라이브러리가 있다.

Day.js

npm install dayjs

//query string / search parmas 주소?key=value&key2=value2 (url encoded / encoded url)
//url params / 베테랑 / 베테랑(영화)
//localhost:300/?targetDt=20241009
//page
type 정의를 해 줘야 한다.

onClick 은 존재하지 않는다.
mouse 키보드는 포함되어 있지 않는다.

app 안에 모아 놓을 거야 라고 계획을 잡아도 된다.

## 클라이언트 컴포넌트의 위치
- /page-name
    - page.tsx
    - PrevButton.tsx
    - NextButton.tsx

- /app
    - /page-name
        - page.tsx
- /components
    - /ui

<a> 태그 보다 페이지 라우팅이 빨리 된다.

<Link>를 제공한다.


// [
          <button>이전</button>
            {dayjs(targetDt).format('YYYY년 MM월 DD일')}
          <button>다음</button>
        ] //


 type ItemType 을 만든다.

 any 대신에 ItemType을 변경해 준다.

 <span className="text-xs">({item.})</span>


 type ResponseType = {
    "
 }       


 true 나 false를 넣은 것이 화면에 표시가 안된다.

 item.rankOldAndNew === 'NEW'

 javascript에서 값을 할당 할 때,
 //자바스크립트 값 할당 팁
 // const key = condition || 'value'; //condition이 거짓일 때 'value'가 할당
 // const key = condition ? '1' : '2'; //삼항연산

 item.rankOldAndNew
 <span className="">

 react if 라이브러라가 있다.


<If condition={ item.rankOldAndNEw === 'NEW' }>
    <Then>N</Then>
</If>

Movie 코드

// /movie/20121234 : movieCd 에 대한 정보를 표시
동적으로 들어오는 데이터
다이나믹 라우터
movie 디렉토리 안에 movie/[movieCd]
안에 page.tsx를 만든다.

영화 이름을 걸어둔다.
Nextjs에서 제공하는 Link를 이용한다.

타입 지정 해 놓고, 하면 된다.


inline-block mr-2
javascript slice 함수 이용

<li>

Link 와 Router 와 다른 것 보다
Link 와 a 태그와 어떻게 다른 것인가.

Chrome 개발자 도구
화면에서 어느 부분에서 변경이 되었는지 
헤더 아래 부분
페이지가 풀로 로드 되는 것이 아니고, 새롭게 로드가 되면 초기화가 된다.
콘솔이 초기화
console.log(1)
Link 태그는 초기화가 안된다.
필요한 부분만 랜더링
Web Application 처럼 이동
a 태그로 로드를 하면 공통까지 풀로드한다.
서버의 리소스 보다도 빨리 느낀다.
<Link> 태그는 
next js 가 제공해 준다.
화면 갱신이 굉장히 빠르다.
서버 사이드 랜더링, Move는 싱글페이지 이동 하는 것처럼 보인다.

Next JS는 처음 접속 할 때와 두번째 접속 할 때는 다르다.
전체 0.6초
400m초
캐쉬를 받아 놓고 있다.
URL이 동일 한데 바뀌는 경우, revalidatePath
또는 caching 데이터 재검증
Revalidating
새로고침 할때는 Revalidating 하겠다. 도 가능하다.

Next JS 서버 컴포넌트가 도입되면서 논란이 되는 것이
서버 사이드 랜더링
Next JS에서 만든 리믹스
서버 컴포넌트 
리액스 서버 컴포넌트
서버 액션은 Next JS 스팩이다.
sign-in page
export default asyc function Page() {
    return <>

    </>
}


로그인은 클라이언트에서는 쓸 수 없고,
서버에서 처리해야 한다.
Route Handler

서버 사이드에서 실행 되는
로그인 처리
별도의 처리
API 작업을 하는 것이 고단한 작업이 될 것이 많다.


<form onSubmit=()> 말고 

서버 데이터 핸들링
최근에는 체크 클라이언트 컴포넌트로 넘어가는 경우가 많다.

SignInForm

export function SignInForm() {
    const
}

SignInForm.tsx를 만든다.
return 속에 로그인페이지를 만든다.

State에 데이터 바인딩 되는 것은 잘 된다.
서버에서 일치 하는지 안하는 지 검사하고 

signin.action.ts
use server 키워드로 시작하고, 만드시 async function 이 반환되어야 한다.
email: string, password: string
email == admin@admin.com, password 
reuturn success:true, messange:'인정 정보를 확인해 주세요.'

use server 로 만들어 놓은 것은 완전히 서버에서 동작을 한다.
client에서는 안찍힌다.
클라이언트에서 노출이 되지 않는다.
서버 사이드 레이어
onSubmit = async (event)
await signIn (email, password);
if (!email) {
    alert('이메일은 필 수 입력 사항입니다.);
    return;
}
if (!password) {
    alert('비밀 번호는 필수 입력입니다.)
    return
}

const response = await signIn(email, password);

POST 호출하기는 어렵다.
//CSRF 방어 처리가 기본으로 포함 - API를 외부에서 호출하기가 더 어려워진다.

결재는 웹푹으로 만든다.
외부에 공개를 해야 한다.
인터널하게 
서버액션을 한다.

폼작업이 많으면 
prisma, sequelize, drizzle ORM
ORM이 Node JS에서 
몇몇 기능만 
ORM을 공유해서 쓸 수 있다.
Next JS 에서 쓸 수 있는 
서버 컴포넌트를 만들고, 클라이언트 컴포넌트를 나눴고, 올렸다.

배포도 해야 한다.

NEXT 
서버사이드 랜더링
SSG
Static Generation
Static Site generation
정적 사이트를 만드는 것이다.
SP는 정적파일은 완전 클라이언트에서만 
미리 정적인 페이지 몇개 만들고, 나머지는 만들어준다.
정적인 페이지 밖에 없다.
static site generation 하는 것을 보여준다.

next 14.2

page-2 / depth-3

<header>
    <ul>
        <li><Link href="">
        <li>

static export 설명이 나와 있어서 보면 된다.

npm run build
SSG 동일한 모드
out 디렉토리 안에 
out 디렉토리를 index.html 은 열리지 않는다.

SSG
스태틱 사이트 제너레이터

movie 
버쎌 자체에 올리든
데이터베이스를 내부에 안가지고 있으면
정적 파라미터는 검색은 할 수 있다.

지금은 주소 만들어 진 것이
targetdDt=yyyymmdd 특정 날짜 박스 오피스
/ㅡmovie?movieCd=20240010 특정 영화에 대한 조회

Next JS
클라이언트로 빼야 한다.


풀피쳐로 갈 것인가

타이틀
메타데이터에 관해서는 쉽게 

각 페이지 마다 타이틀이 다르게 들어가는 경우가 있다.

export const metadata = {

}

export const metadata:Metadata = {
    title: '영화 위키',
    description: '일별 박스 오피스를 확인하고 영화 정보와 영화인 정보를
    OpenGrash: {
        title: 
        description: 
    }
}

영화 상세 정보
영화 위키
각각 다르게 타이틀을 붙일 수 있다.
{영화명}

공통 모듈화

배포 필요

배포는 결정을 스스로 하는 경우도 있지만, 타의로 하는 경우가 많다.
Vercel 서비스를 사용하는 경우가 많다.
요금제가 팀이나 회사에서 다르다.
개인적인 목적은 가능하다.
전문적인 경우 Pro
대표적인 배포 사례

기본으로 Deployment
리눅스 환경이다.
npm build
실행

한번도 안썼다.
한번도 안썼다.
Key를 안썼다. > 배열이 아니었다.

npm run build

npm run start

build 한 내용만 돌리는 것이다.
엔진 X
아파치
서비스는 80 포트로

## 배포
## Node.js 직접 배포
1. npm run build
2. npm run start
    2-1. pm2 같은 Process Manager 이용
3. apache, nginx 80 -> 3000 연결되도록 proxy 처리
리눅스에 대한 

간단하게 해 주는 도구가 있는데, Vercel 서버이다.
Vercel은 테스트 할 수 있다.
새 프로젝트
가장 쉽게 할 수 있는 방법은 Git Service와 연동이다.
비용은 Hobby는
개인 계정이 있고, 조직계정이 있다.
개인 계정은 Hobby만 가능하다.
movie-wiki-2024
private
mkdir movie-wiki-2024
cd movie
git add .;git commit -m '추가'

연결 Git
import
프로젝트 이름
Vercel
디텍트가 되어서 
방문하기 사이트 접속

*.vercel.app
크라임씬
Vercel 아마존 웹서비스
Function Region 
다음 번 부터 배포

배포되는 속도가 굉장히 빠르다.
Git 에서 배포 자동화
배포마다 주소가 다 생긴다.
아마존 웹서비스 

OpenNext 
AWS 직접 제공 하는 오픈 소스 프로젝트이다.
AWS 람다 기반으로
아이들 상태에서 나가는 비용이 없다.

버셀은 일부 기능 숨기고,
AWS CLI 툴 이나 개발 툴이 있어야 한다.

SST 기반으로 만들어 진다.
sst.dev/docs
배포하는 것을 제공한다.

Next.js on AWS with SST
App Router 
Cloudflare

아마존 계정 내에 올리는 것이다.

OpenNEXT로 해서 AWS로 올린다.

SSG 정적 사이트
GitHub Page
특정 디렉토리에서 

Firebase Hosting 정적 사이트
    - 베타 기능으로 

Firebase

AWS Amplify 사용하면 올릴 수 있다.
소스코드만 연동하면 자동으로 배포된다.

개발 패키지

앰플리파이에서 편의 기능을 제공한다.


버쎌에 올리면 된다.
자꾸 배포를 해 봐야 한다.

