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
  - `git reset --hard HEAD@{1}`
  - 최신 커밋을 가리킴

## 02. 커밋 히스토리를 보는 다양한 방법
1. `git log --pretty=oneline`
  - 현재에 있는 브랜치 뿐만 아니라 다른 브랜치로 보려면
  - git log --pretty-oneline -all
  - 뭔가 헷깔려. 마치 premium 브랜치의 리버트 같이 보임

2. `git log --pretty=oneline --all --graph`
  - 커밋 히스토리가 각 브랜치와의 관계가 잘 드러노도록 그래프 형식으로 출력
  - * 가 커밋 하나

## 03. Git을 GUI 환경에서 사용할 수 있게 해주는 프로그램
1. Sourcetree 설치하기

## 04. Git 실전 퀴즈 2
1. git `reflog`
  - 이때까지 HEAD가 가리켜왔던 커밋들의 기록을 보여줍니다.

2. git log --pretty=oneline `--all --graph`
  - 모든 브랜치의 커밋을 보려면 --all 옵션을
  - 커밋 히스토리를 좀더 입체적으로 보려면 --graph옵션을 사용하면 됩니다.

## 05. 깔끔한 커밋 히스토리를 원할 땐 git merge 대신 git rebase
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

## 06. 작업 내용 임시 저장하기
1. get_Abs(num) 추가
  - 절대값 반환
```
def get_Abs(num):
  if num >= 0
    reutnr num
  else:
```
2. `긴급 무료 버전의 라이센스 정보를 수정해 주세요! 당장!!`
  - git checkout master
  - Error
  - 방금 수정한 것이 날라갈 수도 있다.

3. `git stash`
  - **안전한 곳에 보관하다, 넣어두다**
  - working directory에서 작업하던 내용을 깃이 따로 보관
  - stack: 어떤 데이터를 저장하는 구조
  - 최근 커밋 이후로 작업했던 내용은 모두 스택에 옮겨지고 working directory 내부는 다시 최근 커밋의 상태로 초기화

4. `git stash list`
  - 작업했던 내용이 스택에 잘 들어가 있는지 보는 함수

5. 라이센스 파일 수정
  - `git stash`를 했기 때문에, master 브랜치로 이동할 수 있다.
  - git checkout master
  - 라이센서 파일 수정: Free for 1 year
  - git add .
  - git commit -m "Add free License duration info"

6. 스택에 들어 있는 내용을 불러오기
  - git check premium
  - `git stash apply`
  - 적용하다
  - 스택에 있는 내용을 다시 `working directory`로 가져와서 적용
```
def get_Abs(num):
  if num >= 0
    reutnr num
  else:
    return -num
```
  - git add .
  - git commit -m "Add get_Abs function"
  - 어떤 브랜치에서 하던 작업을 아직 커밋하지 않았는데 다른 브랜치로 가야하는 상황에서
  - `작업 중이던 내용을 잠깐 저장하고 싶을 때`

## 07. 잘못된 브랜치에서 작업을 하고 있었다면?
1. master 에서 잘못하고 있을 때
```
def get_Percent(a,b):
  return (a/b) * 100
```
  - 프리미엄 브랜치에서 해야할 작업을 마스터 브랜치에서 한 상황!

2. `git stash`으로 쉽게 해결
  - git stash
  - 저장이 잘 되었음
  - git checkout preminum
  - git stash list
  - git stash apply stash@{0}
  - **confilct 해결**
  - Save
  - git add .
  - git commit -m "Add get_Percent function"

3. `잘못된 브랜치에서 작업하는 실수를 했을 땐?`
  - `git stash`로 stack에 작업 내용을 저장한다.
  - 올바른 브랜치로 가서 다시 git stash apply를 한다.

4. `스택에 작업 내용 너무 많이 쌓여서 보기 힘드네`
  - git stash list
  - `git stash drop stash@{0}`
  - git stash list
  - git stash drop stash@{0}
  - git stash list

## 08. 적용한 작업 내용은 스택에서 없애기
1. 작업 내용 저장
  - git stash

2. 작업 내용 조회(=스택 살펴보기)
  - git stash list

3. 작업 내용 적용
  - git stash apply [작업 내용의 아이디]
  - 작업 내용의 아이디를 생략하면 가장 최근의 작업 내용이 적용됨

4. 작업 내용 제거
  - git stash drop [작업 내용의 아이디]
  - 작업 내용의 아이디를 생략하면 가장 최근의 작업 내용이 제거됨
  - `git stash pop [작업 내용의 아이디]`
  - 작업 내용을 적용하면서 동시에 스택에서 제거도 해주는 커맨드

## 08. Git 실전 퀴즈 3
1. `rebase`
  - git rebase는  현재 브랜치에서 다른 브랜치의 내용을 반영한다는 점에서 git merge와 같은 동작을 합니다.

2. `stash`
  - git stash 커맨드는 현재 브랜치에서 작업하던 내용을 잠시 스택이라는 영역에 저장해 줍니다. stash는 '넣어 두다. 숨기다'라는 뜻을 가집니다.

3. `apply`
  - git stash apply 커맨드는 스택 영역에 저장된 작업 내용들 중 가장 최근에 저장된 것을 working directory에 다시 적용해 줍니다.
  - 만약 맨 뒤에 stash@{0} 등과 같은 작업 내용을 가리키는 아이디를 적어주면 해당 작업 내용을 적용합니다.

4. `pop`
  - git stash pop 커맨드는 스택에서 가장 최근의 작업 내용을 제거하면서 동시에 그것을 working directory에 적용해 줍니다.
  - pop은 빼내다. 뽑아내다 라는 뜻으로 원래 스택이라고 하는 자료구조에서 가장 최근에 넣은 자룔를 추출할 때 사용하는 표현입니다.

## 10. 필요한 커밋만 가져오는 git cherry-pick
1. get_Sum함수 추가
  - 1부터 숫자 n까지의 합을 구해주는 get_Sum함수를 프리미엄 버전에 추가
  - 테스트를 하기 위해서 test 브랜치로 이동
  - git checkout test
```py
def get_Sum_ver1(n):
  return n(n+1)/2
```
  - git add .
  - git commit -m "Add get_Sum_ver1 function"

2. get_Sum함수 수정
  - 커밋을 완료했는데, 누군가가 새로운 방법으로 구현된 get_Sum 함수를 만들었다고 해서 그것을 적용
```py
def get_Sum_ver2(n):
  sum = 0
  for i in range(1, n+1):
    sum = sum + i
  return sum
```
  - (test) git add .
  - (test) git commit -m "Add get_Sum_ver2 function"
  - git checkout premium

3. 함수만 가져오는 방법
  - getSum_ver1 만 필요한 상황
  - git history --all --graph
  - `get cherry-pick`
  - 좋은 것만 골라먹다
  - cherry picker: 본인에게 유리한 것만 선택하는 사람
  - 자신이 원하는 작업이 들어 있는 커밋들만 가져와서 현재 브랜치에 추가
  - git cherry-pick 148d
  - **confilct 해결**
  - :wq
  - git add .
  - git commit -m "Add get_Sum function from test branch"

4. `git cherry-pick`
  - 원하는 작업이 있는 커밋의 내용만 가져올 수 있는 커맨드

## 11. 여러 커밋을 하나의 커밋으로 만들기
1. 팩토리얼 함수 추가
  - 1부터 어떤 수 사이에 있는 모든 수들을 다 곱한 값을 알려주는 함수
```py
def factorial(n):
  if n == 1:
    return n
  else :
    return n * factorial(n-1)
```
  - git add .
  - git commit -m "Add factorial function"

2. 팩토리얼 효울 함수로 수정
```py
def factorial(n):
  num = 1
  while n >= 1:
    num = num * n
    n = n-1
  return num
```
  - git add .
  - git commit -m "Add factorial function2"

3. 커밋을 없었던 것으로 하고 싶을 때
  - git history
  - `git reset`의 3가지 옵션
    - **--hard : working directory 초기화 (주의:쓰지 말것)**
    - **--mixed : working directory의 상태를 건드리지 않는 옵션**
    - **--soft : working directory의 상태를 건드리지 않는 옵션**
  - git reset --soft 056d
  - git add .
  - git commit -m "Add factorial function"
  - git history

## 12. git이 무시하는 파일들
1. .gitignore 파일 살펴보기
  - `.gitignore`파일은
  - working directory 내에 존재한느 파일들 중에서
  - 마치 존재하지 않는 것처럼
  - Git이 인식해야 할 파일들의 목록이 적힌 파일입니다.

## 13. Git 실전 퀴즈 4
1. `cherry-pick`
  - git cherry-pick 커맨드는 다른 브랜치를 merge하고 싶지는 않지만 해당 브랜치의 커밋 히스토리 중 마음에 드는 특정 커밋만을 가져와서 현재 브랜치에 반영하고 싶을 때 사용합니다. check-pick은 '마음에 드는 것만 골라먹다'라는 뜻을 가지는데요.

2. `.gitignore`
  - `.gitignore`파일은 보통 Git으로 프로젝트의 버전 관리를 시작하려고 할 때 작성하는데요. .gitignore파일에는 working directory 안에 존재하기는 하지만 Git으로 버전 관리하고 싶지 않은 것들'의 이름을 적으면 됩니다.

