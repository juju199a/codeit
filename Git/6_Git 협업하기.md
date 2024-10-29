# 6. Git 협업하기
## 04. 이 코드는 누가 작성했을까?
1. `git blame`
    - blame: 비난하다, ~을 탓하다
    - 어떤 파일의 특정 코드를 누가 작성했는지 찾아내기 위한 커맨드
    - git blame calculator.py
    - git show 3a09
        - 누가 이 코드를 작성했는지 알 수 있다.

## 05. 이미 Remote Repository에 올라간 커밋을 취소해야 한다면
1. 무료 버전 수정
    - git checkout master
        - master는 무료 브랜치
    - caculator.py 파일을 subline 텍스트에서 열어주세요.
```py
def square(a):
    return a*a
```
    - git add .
    - git commit -m "Add squre function"
    - git push

2. 최신 커밋을 되돌린다.
    - `git revert (작업을 되돌리고 싶은 커밋의 아이디)`
        - 되돌리다. 복귀하다
    - git revert f658
    - 커밋 메시지를 입력하라는 메시지
        - 자동으로 메시지 나옴 > 그대로 사용
    - :wq
    - Revert 완료
    - cat calculator.py
    - git history
    - git push
    - git history

3. 이미 Push를 해 버렸으면 Reset을 쓰면 안됨

## 06. 여러 커밋 취소하기
1. 여러 커밋 취소
    - git history
    - `git revert` (어느 커밋부터 어느 커밋까지)
    - git revert facd..eea5
        - facd 커밋은 포함되지 않는다.
        - 커밋 
    - 커밋 메시지를 입력하라는 메시지
    - :wq
    - cat README.md
    - git history
    - git push
    - git history

2. 프리미엄 브렌치로 가서 해 볼께요.
    - git checkout premium
    - git history
    - git revert facd..eea5
    - wq
    - git push
    - git history

## 07. Git 실전 퀴즈
1. git push

2. git fetch

3. git blame
    - 어떤 파일의 내용 한줄 한줄이 각각 어떤 커밋에 의해 탄생했는지를 확인하려면 아래와 같은 커맨드를 써야 합니다.

4. git revert [커밋 아이디]
    - 특정 커밋에서 이루어진 작업을 그대로 되돌리는(취소하는) 새로운 커밋을 추가

## 08. Git 협업하기 정리 노트
1. git fetch
    - 로컬 레포지토리에서 현재 HEAD가 가리키는 브랜치의 업스트림(upstream) 브랜치로부터 최신 커밋들을 가져옴(가져오기만 한다는 점에서, 가져와서 머지까지 하는 git pull과는 차이가 있음)

2. git blame
    - 특정 파일의 내용 한줄한줄이 어떤 커밋에 의해 생긴 것인지 출력

3. git revert
    - 특정 커밋에서 이루어진 작업을 되돌리는 (취소하는) 커밋을 새로 생성

