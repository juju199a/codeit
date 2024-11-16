# 2. 자주 쓰는 CSS 속성
## 01. 텍스트 스타일링 정리
1. 글자색 color
  - `color: #F23030`

2. 글자 크기 font-size
  - `font-size:24px`

3. 글꼴 font-family
```
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Noto+Sans+KR&family=Poppins&display=swap" rel="stylesheet">
```
  - font-family: Poppins, "Noto Sans KR", sans-serif;
  - font-family: "Noto Sans KR", sans-serif;

4. 글자 굵기 font-weight
  - 100,200,300,...,900까지 씁니다.
  - `font-weight: 600;`

5. 줄 높이 line-height
  - 단위 없이 사용한다.
  - `line-height: 1.7;`

6. 텍스트 꾸미기 text-decoration
  - 밑줄, 취소선
  - `text-decoration: none;`

## 02. 코드잇 베리타스
1. `line-height: 1.5;`

2. `text-decoration: none;`

## 03. 배경 이미지: background-image
1. `background-image`
  - background-image: url('pizza.png');
  - background-repeat: no-repeat;
  - background-position: center;
  - background-size:cover;

## 04. 그라디언트: linear-gradient
  - `background-image: linear-gradient(rgba(0,0,0,1), rgba(0,0,0,0))`
  - 방향을 바꿔주고 싶으면 맨 앞에 각도를 적어 주면 된다.
  - `background-image: linear-gradient(90deg, rgba(0,0,0,1), rgba(0,0,0,0))`
  - 그라디언트 단계마다 비율을 다르게 하고 싶다면, 중간에 40%라고 적어 줄 수 있다.
  - `background-image: linear-gradient(90deg, rgba(0,0,0,1), 40%, rgba(0,0,0,0))`
  - Google > gradient generator
  - `그라디언트 코드를 만들 수 있습니다.`
```
background-image: 
    linear-gradient(90deg, rgba(0,0,0,1), 40%, rgba(0,0,0,0)),
    url('pizza.png');
```

## 05. 아이유의 좋은 날
1. `background-image: url('bg.png');`

2. `linear-gradient(rgba(159, 84, 209, 0.2), rgba(115, 82, 208, 0.6))`

3. 
```
background-image:
  linear-gradient(rgba(159, 84, 209, 0.2), rgba(115, 82, 208, 0.6)),
  url('bg.png');
background-repeat: no-repeat;
background-position: center;
background-size: cover;

```

## 06. 그림자: box-shadow
1. box-shadow
  - box-shadow: `10px 15px` rgba(0,0,0,0.4);
    - 가로로 10px, 세로로는 아래로 15px 아래에 새긴 겁니다.
  - box-shadow: 10px 15px `20px` rgba(0,0,0,0.4);
    - 20px은 블러. 흐림정도를 나타낸다. 경계를 흐려진다.
  - box-shadow: 10px 15px 20px `5px` rgba(0,0,0,0.4);
    - 5px: 그림자가 얼마나 퍼질지. 그림자 크기
  - 전체적인 스토리를 이해해야 한다.
  - 그림자는 `영역`에 생기는 것인데, `위치`와 `색깔`을 정하고,
  - `어느정도 흐리게`할지 정한 다음에, `퍼지는 크기`를 정할 수 있다.
  - `box-shadow: 0 4px 15px rgba(0,0,0,0.4)`
  - MDN 사이트
  - Google > box shadow generator

## 07. 불투명도: opacity
1. 품절
  - `opacity: 0.5;`
  - 1에 가까울 수로 불투명, 0은 완전 투명
  - 정말 자주 씀

## 08. 자유여행 액티비티
1. box-shadow: 0px 4px 28px `rgba(0, 0, 0, 0.2)`;

2. 불투명도 opacity 
  - background-image: linear-gradient(rgba(0, 0, 0, 0.3), rgba(0, 0, 0, 0)),
    url('./activity-duck.png');
  - opacity: 0.3;

09. 새로 배운 CSS 속성 정리
1. 배경 이미지 background-image
  - background-image: url('flowers.png');

2. 배경의 위치 background-position
```css
background-position: top; /* 위 */
background-position: right; /* 오른쪽 */
background-position: bottom; /* 아래 */
background-position: left; /* 왼쪽 */
background-position: left top; /* 왼쪽 위 (지정하지 않았을 때 기본값) */
background-position: center;
```

3. 배경의 반복 background-repeat
```css
background-repeat: repeat; /* 반복하기 (지정하지 않았을 때 기본값) */
background-repeat: no-repeat; /* 반복 안 함 */
```

4. 배경의 크기 background-size
```css
background-size: cover; /* 비율 유지하면서 꽉 차게. 이미지 잘릴 수 있음 */
background-size: contain; /* 비율 유지하면서 최대한 크게. 이미지 잘리지 않음 */
background-size: 40px 30px; /* 가로 40px 세로 30px */
```

5. 그라디언트 linear-gradient()
```css
background-image: linear-gradient(#000000, #ffffff);
background-image:
  linear-gradient(45deg, rgba(0, 0, 0, 0.8), rgba(0, 0, 0, 0.2));
```

6. 그림자 box-shadow
```css
box-shadow: 5px 10px 15px 8px rgba(0, 0, 0, 0.6);
/*
  가로: 5px
  세로: 10px
  흐린 정도(Blur): 15px
  퍼지는 정도(Spread): 8px
  색상: rgba(0, 0, 0, 0.6)
*/
```

7. 불투명도 opacity
```css
opacity: 0; /* 투명 */
opacity: 0.6;
opacity: 1; /* 불투명 */
```
