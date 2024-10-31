# 7. Git 자유자재로 활용하기
## 01. git reset을 하고 나서 돌아오려면?
1. `git reset --hard abad`
  - 워킹 디렉토리에 있는 것 모두 초기화
  - cat calculator.py
  - git history
  - `이때까지 한 커밋들은 사라진 걸까?`
  - No. reset을 해도 그 이후의 커밋들이 삭제되는 건 아닙니다!

2. `git reset --hard 9856`
  - git history
  - 예전의 커밋들이 다 잘 보인다.
  - Head가르키는 것 뿐이다.

3. 만약 최신 커밋 아이디를 모른다면
  - `git reflog`
  - reference log, 헤드가 이때까지 가리켜왔던 커밋들을 기록한 정보
  - q 를 눌러서 나감
  - git reset --hard HEAD@{1}
  - 최신 커밋을 가리킴

## 02. 커밋 히스토리를 보는 다양한 방법
1. `git log --pretty=oneline`
  - 현재에 있는 브랜치 뿐만 아니라 다른 브랜치로 보려면
  - git log --pretty-oneline -all
  - 뭔가 헷깔려. 마치 premium 브랜치의 리버트 같이 보임

2. `git log --pretty=oneline --all --graph`
  - 커밋 히스토리가 각 브랜치와의 관계가 잘 드러노도록 그래프 형식으로 출력
  - * 가 커밋 하나

### 03. Git을 GUI 환경에서 사용할 수 있게 해주는 프로그램
1. Sourcetree 설치하기

### 04. Git 실전 퀴즈 2
1. git `reflog`
  - 이때까지 HEAD가 가리켜왔던 커밋들의 기록을 보여줍니다.

2. git log --pretty=oneline `--all --graph`
  - 모든 브랜치의 커밋을 보려면 --all 옵션을
  - 커밋 히스토리를 좀더 입체적으로 보려면 --graph옵션을 사용하면 됩니다.

### 05. 깔끔한 커밋 히스토리를 원할 땐 git merge 대신 git rebase
1. git merge를 쓰는 경우
  - test 브랜치: 코드 실험용 브랜치
  - (premium) git branch test
```
def get_Remainder(a,b):
    return a//b
```
  - (premium) git add .
  - (premium) git commit -m "Add get_Remainder function"
  - (premium) git checkout test
```
def get_Median(a,b):
    return (a,b)/2
```
  - (test) git add.
  - (test) git commit -m "Add get_Median function"
  - git checkout premium
  - `git merge test`
  - **conflict 해결**
  - git add .
  - git commit
  - :wq
  - git history --all --graph
  - 머지된 것이 잘 보인다.

2. `git rebase`
  - git reset --hard ef2e
  - git history
  - `git rebase test`
  - rebase: 베이스를 다시 지정하다, 커밋을 재배치하다.
  - 프리미엄 브랜치의 베이스를 테스트 브랜치로 재지정한다.
  - **confilct 해결**
  - git add .
  - `git rebase --continue`
  - 컨플릭트가 발생해서 제대로 진행되지 못한 리베이스를 계속 진행하라
  - `Applying: Add get_Remainder function`
  - git history -all --graph

3. merge와 rebase차이
  - rebase는 새로운 커밋을 만들지 않는다.
  - rebase로 만들어진 커밋 히스토리는 merge로 만들어진 커밋 히스토리 보다 깔끔
  - rebase나 merge나 결과물은 같음
  - 커밋 히스토리를 깔끔하게 만들려고 rebase를 쓴다!

4. merge vs rebase
  - `merge`: 두 브랜치를 합쳤다는 정보가 커밋 히스토리에 꼭 남아야하는 경우
  - `rebase`: 커밋 히스토리를 깔끔하게 유지하는 게 더 중요한 경우

## 06. 

