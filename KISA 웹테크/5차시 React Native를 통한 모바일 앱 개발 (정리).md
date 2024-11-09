# 1교시 요약

1. 개요 및 React Native 특징
    - React Native: Meta(구 페이스북)가 공개한 오픈소스 크로스 플랫폼 개발 기술
    - 안드로이드와 iOS에서 동작하는 모바일 애플리케이션을 단일 코드로 개발 가능
    - JSX: JavaScript + XML 문법 사용, 자바스크립트 깊은 이해가 필요

2. 네이티브 vs 하이브리드 vs 크로스 플랫폼
    - 네이티브 앱: Android/iOS별 별도 개발 (성능 우수)
    - 하이브리드 앱: 웹뷰(WebView) 기반 (개발 편의성 높지만 성능 낮음)
    - 크로스 플랫폼 앱: 하나의 코드로 여러 플랫폼 빌드 (React Native, Flutter, Xamarin)
    - React Native: 빌드 시 네이티브 코드로 변환됨
    - Bridge: 네이티브와 자바스크립트 엔진 간 연결

3. React Native 학습 및 설정
    - 환경 설정 복잡: Android 에뮬레이터, Xcode 시뮬레이터 등 필요
    - Expo: React Native를 위한 프레임워크
    - 초기 학습에 유용하나, 실무 적용은 신중해야 함
    - Snack: 웹에서 React Native 앱을 테스트할 수 있는 도구 (`https://snack.expo.dev/`)

4. 최신 버전과 업데이트
    - 버전 0.76: 메이저 업데이트 포함
    - 엔진과 브리지 성능 개선
    - 공식 문서(주제별로 구성)에서 최신 정보 확인 필요

5. 기타 특징
    - React Native for Windows / MacOS 등 다양한 OS 지원
    - React와 React Native는 코드 구조가 비슷하지만, 일부 기능 차이가 있음 (예: <Text>는 웹에는 없고 네이티브에서는 필수)


# 2교시 요약

1. 함수형 컴포넌트와 JSX
    - 함수형 컴포넌트: React Native에서 주로 사용하는 컴포넌트 형식
        - return문에서 JSX를 반환함
        - JSX: XML-like 문법으로, HTML과 비슷하지만 자바스크립트와 결합됨
        - {} 중괄호: 자바스크립트 코드를 JSX 안에 삽입할 때 사용

2. 스타일링과 단위
    - StyleSheet: 웹의 CSS와 유사하지만 1:1 매핑은 아님
        - 예: %와 px(뷰포트 기준의 dp)만 사용
        - 클래스가 아닌 객체(container 등)에 스타일 설정
    - 인라인 스타일:
        - 가능하면 사용을 지양하지만, 간단한 스타일에서는 사용 가능
        - 예: <Text style={{ color: 'blue' }}>Hello</Text>
        - 배열로 스타일을 병합 가능:
```jsx
<Text style={[styles.text, { color: 'blue', fontWeight: 'bold' }]} />
```
    - Styled Components:
        - Emotion Native나 NativeWind와 같은 도구 사용 가능
        - Tailwind CSS는 공식 지원되지 않으나 NativeWind와 twrnc 등으로 대체 가능

3. 상태 관리와 입력 처리
    - React의 useState, useEffect 등을 그대로 사용
        - 숫자 입력 시 전화 키패드로 처리하는 것이 편리
        - 예: <TextInput keyboardType="phone-pad" />

4. 개발과 테스트 환경
    - Expo-Go 앱: 모바일 기기에서 빠르게 테스트 가능
    - USB 배포: 빠른 반응 확인을 위해 물리 디바이스에 연결
    - 원격 안드로이드 디바이스 사용 가능
    - 기능 테스트는 웹에서 간단히 가능

5. 기타 유용한 기능
    - toLocaleString(): 숫자에 3자리마다 쉼표 삽입

```javascript
const result = 1234567;
console.log(result.toLocaleString()); // "1,234,567"
```


# 3교시 요약

1. 기본 개념과 라이브러리 사용
    - dayjs: 시간 관련 작업에 사용하는 경량 라이브러리 ("dayjs": "1.11.13")
        - npm에서 라이브러리 설치 가능 (https://npmjs.com)
        - React Native에서는 웹과 달리 window나 document 객체에 접근할 수 없음
        - JQuery처럼 DOM을 직접 제어하는 것이 불가

2. 네트워크 요청
    - Axios와 Fetch를 사용해 네트워크 통신 가능
        - Node.js와 React Native에서 암호화 등 일부 기능은 동일하게 사용 가능

3. 이미지 처리
    - Image와 ImageBackground:
        - Image: 자식 객체를 가질 수 없음
        - ImageBackground: 자식 객체를 포함할 수 있어 백그라운드 이미지로 사용

```jsx
<Image 
  source={{ uri: 'https://picsum.photos/200' }} 
  style={{ width: 300, height: 200, resizeMode: 'cover' }} 
/>
```
        - resizeMode: 이미지를 자르는 방식 (cover, contain 등)
        - Dimensions: 화면 크기에 따라 이미지나 레이아웃 조정

4. 시간 업데이트와 애니메이션
    - **setInterval**을 사용해 시간 실시간 업데이트:

```javascript
useEffect(() => {
  const interval = setInterval(() => {
    setDate(dayjs().format('MM월 DD일\nHH:mm:ss'));
  }, 1000);
  return () => clearInterval(interval); // 메모리 누수 방지
}, []);
```
    - 애니메이션: React Native는 기본 애니메이션 API와 외부 라이브러리를 제공
        - 트랜지션과 잠금 방지 기능도 React Native용 라이브러리로 구현 가능

5. 프로젝트 구성과 설정
    - View, Text, Image: 화면을 구성하는 기본 컴포넌트
    - npx create-expo-app: Expo를 사용해 프로젝트 생성
    - Node.js 설치: 개발 환경 설정 시 NVM(Node Version Manager) 추천
    - Windows: nvm-windows 사용 권장
    - 버전 확인 명령어:
```bash
node -v
npm -v
npx -v
```

6. 네비게이션 설정 (오후 내용 예고)
    - 여러 화면을 구현하려면 네비게이션 설정 필요
    - Expo를 사용해 윈도우 랩탑 등 다양한 환경에서 에뮬레이터 실행 가능


# 4교시 요약

1. Expo 외 직접 작업하기
    - 에디터: VS Code 추천, WebStorm 개인 무료 사용 가능.
    - 메모장 사용 주의: 특수 문자나 줄바꿈 이슈 발생 가능.
    - 명령어: npx create-expo-app 사용 권장.
    - 권장 터미널: PowerShell 권장, WSL 2는 설정에 시간이 걸림.

2. 디렉토리 구조 관리
    - package.json 위치 관리 중요.
    - 상위 디렉토리의 package.json이 하위 디렉토리에서 참조될 수 있어 예기치 않은 오류 발생 가능.

```markdown
~/work/
  ├── package.json
  └── sub-dir/
      ├── package.json  # 상위 폴더와 충돌할 수 있음.
      └── app/router/
```

    - Tip: package.json 파일은 동일 디렉토리에만 두고, 하위 폴더에 추가로 생성하지 않기.

3. 터미널 명령어 및 프로젝트 실행
    - 프로젝트 생성:
```bash
npx create-expo-app@latest
```
```bash
cd first-expo-app
npm run start
```
    - 애뮬레이터: 실행 시간 오래 걸림. Expo Go 앱 권장.

4. Metro Bundler 및 엔진 구조
    - Metro Bundler: React Native에서 JavaScript 엔진을 담당.
        - PC에서 JavaScript 엔진이 실행되고, 모바일 디바이스와 네트워크 통신.
    - 개발 중에는 네트워크 연결 필수, 하지만 최종 배포 시엔 Metro Bundler가 필요하지 않음.

5. 디바이스와 Metro Bundler 문제 해결
    - Hot Reloading: index.tsx 수정 시 실시간 업데이트 가능.
    - 디바이스에서 Reload 방법:
        - 디바이스를 흔들거나, Expo Go에서 Reload 클릭.
    - 네트워크 문제 해결:
        - QR 코드를 재스캔하거나 앱을 다시 시작.
        - 로컬 네트워크 권한 허용:

```plantext
설정 > 앱 > Expo Go > 로컬 네트워크 > 허용
```


# 5교시 요약

1. 앱 디렉토리 구조: Expo에서는 App이 중요한 역할을 하며, 디렉토리 내 파일 기반 라우팅이 이루어진다.

2. 네비게이션 개념:
    - Router: 웹 애플리케이션에서는 필수적이며, Next.js처럼 자체적으로 제공되기도 함.
    - React Router Dom과 React Navigation: 둘 다 사용 가능하며, 여러 페이지를 가진 앱을 만들기 위한 도구이다.
    - 파일 기반 라우팅: Expo에서 제공, Web React의 Router 방식과 유사하며 편의 기능을 제공한다.
3. Expo-router:

    - app 디렉토리가 중요한 역할을 하며, _layout.tsx와 같은 파일을 사용하여 네비게이션을 구성한다.
    - 화면 구성 예시:
        - app/index.tsx: 메인 페이지는 항상 index로 설정해야 하며, 다음과 같이 작성:

```jsx
<Stack.Screen name="index" options={{ headerShown: false }} />
```

4. 네비게이션 타입:
    - Stack Navigation: 화면이 쌓이는 방식으로, 안드로이드 스타일의 네비게이션이다.
    - Tabs Navigation: 하단 탭 형식으로 페이지 간 전환이 애니메이션 없이 이루어진다.
    - Drawer Navigation: 사이드에서 나오는 메뉴 형식으로 구성된다.

5. 페이지 구조
    - 예시로 키오스크 앱을 만들며, index.tsx, category.tsx, single.tsx, set-menu.tsx와 같은 파일이 포함된다.
    - layout.tsx 수정 예시:

```tsx
<Stack.Screen name="index" options={{ headerShown: false }} />
<Stack.Screen name="category" options={{ headerShown: false }} />
<Stack.Screen name="single" options={{ headerShown: false }} />
<Stack.Screen name="set-menu" options={{ headerShown: false }} />
<Stack.Screen name="+not-found" />
```

6. 컴포넌트 사용법:
    - SafeAreaView vs. View: SafeAreaView는 화면의 안전 영역을 고려하여 표시되며, View는 일반적으로 사용된다.
    - 스타일 설정 예시:
```jsx
<View style={{ backgroundColor: '#999', flex: 1, justifyContent: 'center', alignItems: 'center' }}>
```

7. 링크 설정:
    - Link 컴포넌트의 스타일 지정 및 부모 요소의 크기를 100%로 설정하는 방법:
```jsx
<Link href={'/category'}>
    <View style={{ width: '100%', height: '100%' }}>
```

# 6교시 요약

1. 링크 지원의 한계: 모든 경우에 Link 컴포넌트가 지원되는 것은 아니다.

2. 터치 가능한 컴포넌트:
    - React에서 사용할 수 있는 터치 가능한 컴포넌트로는 다음이 있다:
        - Pressable
        - TouchableOpacity
        - TouchableHighlight
        - TouchableWithoutFeedback
3. 다이나믹 및 프로그래머블 네비게이션:
    - 다이나믹 네비게이트와 프로그래머블 네비게이트를 사용할 수 있다.

```jsx
<TouchableOpacity onPress={() => {
    router.push('/category');
}}>
```

4. 탭 전환: 앱에서 새 탭으로 열기와 빠른 전환은 동일하게 처리할 수 있다. 일반적으로 onPress를 통해 빠르게 추가하는 것이 선호된다.

5. 동적 ID 처리: 동적으로 ID와 같은 값을 처리할 수 있는 구조를 만들어야 한다. 이때 ScrollView 컴포넌트를 사용할 수 있다.

6. 스타일 지정:
    - 기본 스타일을 지정하는 것이 번거로워, StyleSheet를 사용하는 것이 좋다.
    - 예시: TouchableOpacity에 스타일을 적용할 때

```jsx
<TouchableOpacity style={{ border: '1px solid black' }}>
```

7. 리스트 처리:
    - FlatList: 리스트를 효과적으로 표시하는데 유용한 컴포넌트이다. 주로 두 가지가 필요하다:
        - data (데이터 배열)
        - renderItem (각 아이템을 렌더링하는 함수)

```jsx
<FlatList
    data={LIST}
    renderItem={({ item }) => (
        // 아이템 컴포넌트
    )}
/>
```

8. ScrollView vs FlatList:
    - **ScrollView**는 모든 항목을 메모리에 로드하지만, 항목 수가 많을 때는 성능 저하를 초래할 수 있다.
    - **FlatList**는 화면에 보이는 항목만 메모리에 로드하여 성능을 최적화한다. 따라서 FlatList를 사용하는 것이 권장된다.

9. 가독성을 위한 Item 함수: 가독성을 높이기 위해 아이템 렌더링 함수를 별도로 정의할 수 있다.

10. Key 속성의 중요성:
    - React에서는 key 속성이 매우 중요하다. 각 아이템에 유니크한 key를 설정해야 하며, 중복된 키는 경고를 발생시킨다.
    - 동일한 레이블을 가진 경우에도 각 아이템은 반드시 다른 key를 가져야 하며, 데이터가 삭제될 때 key를 기준으로 변경사항을 관리한다.


# 7교시 요약

1. 버튼 처리: 단품 메뉴 아래에 버튼을 추가하기 위해 **TouchableOpacity**를 **View** 안에 넣는다.

2. Flexbox 설정:
    - 가로 방향으로 배치할 때는 flexDirection을 설정해야 하며, 예를 들어:

```jsx
style={{ flexDirection: "row", gap: 12 }}
```

    - flex: 1 속성을 사용하여 공간을 적절히 분배한다.

3. 세트 메뉴 처리: 세트 메뉴는 타일 리스트 형태로 구성되며, FlatList를 사용하여 아래와 같이 설정한다:

```jsx
<FlatList numColumns={2} />
```
    - 유동적인 구성 요소가 필요할 경우, **FlatList**를 껐다 켜는 방식으로 처리해야 한다.

4. FlatList의 한계: **FlatList**는 **justifyContent**를 사용할 수 있어 유연한 레이아웃 구성이 가능하다.

5. 타입스크립트 활용:
    -   타입스크립트를 사용하여 오류를 줄인다. any 타입 사용은 피해야 하며, 다음과 같이 타입을 정의한다:

```typescript
type ListItemType = {
    key: string;
    name: string;
    link: string;
};
```
    - types/index.ts와 types/ListItemType.ts 파일을 생성하여 타입을 정의한다.
    - 링크를 통해 상품의 상세 정보나 유튜브 커머셜 동영상을 보여줄 수 있다. 이때 링크 타입을 string에서 vid:string으로 변경할 수 있다.

6. 컴포넌트 및 API 문서화:
    - React Native의 컴포넌트는 화면에 보이는 요소로, API는 보이지 않는 요소로 분류된다.
    - 애니메이션 처리에 필요한 API로 Dimensions를 사용할 수 있다.
    - Modal 및 Image 같은 컴포넌트는 React Native에서 활용할 수 있다.

7. Expo SDK와 React Native의 결합:
    - 필요하다면 Expo 없이 React Native만으로 작업하는 것도 가능하다.
    - **WebView**를 사용하면 React Native 내에서 웹 콘텐츠를 호출할 수 있다.

8. 임베디드 콘텐츠:
    - 유튜브 콘텐츠를 임베디드로 포함할 수 있으며, 단순 임베드는 **WebView**를 통해 구현한다.
    - Expo에서는 기본적으로 제공하는 구성 요소를 사용할 수 있지만, 모든 기능을 보장하지는 않는다.

9. 결제 및 데이터 관리:
    - Stripe 연동 및 SQL Lite 사용에 대한 언급이 있었다.
    - SMS 연동은 별도의 플랜을 필요로 하며, **AsyncStorage**를 통해 작은 데이터(예: 토큰)를 저장할 수 있다.
    - **WebView**를 통해 다양한 웹사이트를 앱 내에서 표시할 수 있다.

# 8 교시 요약

1. 상세정보 페이지:
    - 다이나믹 라우트를 사용하여 게시물이 변경될 때마다 업데이트된다.
    - Next.js에서 사용했던 패턴과 유사하나, 약간의 차이가 있다.
    - 대괄호 []를 사용하여 유동적인 라우트를 설정한다.

2. Link 컴포넌트:  
    - 두 가지 방법으로 페이지를 설정할 수 있다:
        - 첫 번째 방법: 대괄호를 사용하여 동적으로 설정
        - 두 번째 방법: **useLocalSearchParams()** 훅을 사용한다.
    - 예를 들어, details/[vid].tsx 파일을 생성하여 비디오 ID를 잘 가져오는지 확인한다.
    - 링크를 감싸고 href={'/'}를 설정하여 라우터 기능을 추가한다.

3. WebView 설치:
    - WebView를 사용하기 위해 설치한다:
```bash
npx expo install react-native-webview
```
    - 이후, npm start로 서버를 실행하고 페이지를 다시 로드한다.
    - 유튜브 비디오를 로드하기 위해 **WebView**의 **source** 속성을 설정한다.
    - 아래와 같이 스타일을 조정하여 화면에 꽉 차게 설정한다:
```jsx
<View style={{ width: '100%', aspectRatio: 16 / 9 }}>
    <WebView source={{ uri: 'https://www.youtube.com/embed/{vid}' }} />
</View>
```

4. 리액트 라이브:
    - 비디오를 유튜브가 아닌 다른 소스에서 가져올 경우, 리액트 라이브가 필요할 수 있다.
    - 파일 기반 라우트에서 대괄호를 사용하여 매개변수를 동적으로 설정할 수 있다.

5. 저장 및 데이터 관리:
    - 앱을 껐다 켰을 때 데이터를 저장하기 위해 **AsyncStorage**를 사용할 수 있다.
    - 로컬 DB는 SQLite를 활용할 수 있다.

6. React Navigation과 Expo:
    - React Navigation과 Expo Route의 문서를 참고하여 설치 방법을 익힌다.
    - Expo 라이브러리 외에도 React Native 프레임워크를 사용하여 직접 프로젝트를 생성할 수 있다.

7. Expo 및 React Native의 차이점:
    - Expo는 앱의 배포와 빌드를 서버에서 처리하며, 사용자에게 쉽게 배포할 수 있다.
    - Expo의 문서에 따르면, 앱스토어나 구글에 전송하기 위해서는 Expo 서버를 통해 빌드한 후 다운로드해야 한다.
    - Expo의 과금 서비스인 EAS (Expo Application Services)도 활용 가능하다.

8. 마이크로소프트 코드 푸시:
    - 작은 앱들을 위해 마이크로소프트의 코드 푸시를 사용하여 라이브 업데이트를 지원한다.
    - 앱의 아이콘 생성 및 문서화 작업이 필요하다.