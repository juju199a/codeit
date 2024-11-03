# 1. Django 개발 환경 구성하기
## 01. Django 웹 개발 코스 소개
1. 웹서비스
  - 회원가입
  - 로그인
  - 좋아요
  - 댓글
  - 팔로우

2. Why is django?
  - `파이썬 언어`로 된 프레임워크
  - `많은 것을 제공`해 주는 프레임워크
  - `검증된` 프레임워크

## 02. Django Framework가 뭐지?
1. django
  - 웹 프레임워크
  - `nodejs`: Javascript
  - `Laravel`: PHP
  - `RAILS`: Ruby
  - `spring`: Java

2. 프론트 엔드
  - front, 앞부분
  - React
  - Angular
  - Vue

3. 백 엔드
  - back, 백엔드
  - 광고를 보워줘야겠다.

4. django
  - 백엔드?
  - 프론트엔드?
  - 풀스택 
  - 백엔드로 사용 + React 프론트 엔드

## 03. Django 개발 환경 이해하기
1. Python 3.7.7 버전 사용

2. Visual Studio Code
  - 신택스 하이라이트
  - 확장 프로그램 (Extension)

3. 가상환경
  - 프로젝트 A
  - 프로젝트 B
  - `pyenv`: 파이썬 버전 설치, 관리
  - `pyenv-virtualenv`: 가상 환경을 구성 파이썬 패키지 관리

4. for Windows
  - WSL (Windows Sybsystem for Linux)
  - Windows에서 리눅스 터미널을 사용할 수 있게 해 주는 확장 프로그램
  - macOS와 비슷한 개발 환경을 Windows에서 만들 수 있다.

5. for macOS
  - Homebrew
  - macOS의 패키지 관리 프로그램
  - pyenv와 pyenv-virtualenv 모두 homebrew를 통해 설치 가능
  - 패키지 설치부터 제거까지 간편하게 가능하다.

6. Django 2.2 버전 사용
  - LTS(Long Term Support)

## 04. Django 개발환경 구성하기
1. MAC 환경에서 설치
  - VSCode 설치 - 코드를 편집하는 텍스트 에디터
  - Homebrew 설치 - macOS의 프로그램 설치 관리를 편하게 해주는 프로그램
  - pyenv.pyenv-virtualenv 설치
  - pyenv를 이용한 파이썬 설치
  - pyenv-virtualenv를 이용한 가상환경 생성
  - pyenv로 설치한 파이썬 적용 및 django 2.2 설치

## 05. Django 개발 환경 구성하기 (Windows)
1. Windows 환경에서 설치
  - 검색 > Windows 기능
  - Windows 기능 켜기/끄기
  - Linux용 Windows 하위 시스템 항목에 체크
  - 검색창 store > ubuntu
  - Ubuntu > 시작 화면에 고정 / 작업 표시줄에 고정

2. Ubuntu 설치
  - Ubuntu 18.04 LTS
  - username: codeit
  - password: 1234
  - `sudo apt-get update`
```
sudo apt-get install -y make build-essential \
libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev \
wget curl llvm libncurses5-dev libncursesw5-dev \
xz-utils tk-dev git python-pip sqlite3
```
  - mkdir codeit-django
  - cd codeit-django
  - `code .`
    - VSCode 서버가 설치
  - Extensions > wsl 검색 > WSL 설치
  - `code .` > 잘 나옴

3. pyenv, pyenv-virtualenv 설치
  - `curl https://pyenv.run | bash`
  - echo $SHELL
```
sed -Ei -e '/^([^#]|$)/ {a \
export PYENV_ROOT="$HOME/.pyenv"
a \
export PATH="$PYENV_ROOT/bin:$PATH"
a \
' -e ':a' -e '$!{n;ba};}' ~/.profile
```
  - echo 'eval "$(pyenv init --path)"' >>~/.profile
  - echo 'eval "$(pyenv init -)"' >> ~/.bashrc
  - echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.bashrc
  - 우분투 종료 후 다시 실행
  - pyenv --version

## 06. Django 개발 환경 구성 하기 2
1. pyenv를 이용한 파이썬 설치
  - `pyenv install --list`
    - pyenv로 설치 할 수 있는 python 버전 보기
  - `pyenv install 3.7.13`
    - pyenv로 python 설치하기
  - `pyenv install 3.8.13`
  - `pyenv versions`
    - 설치된 python 버전 확인하기

2. pyenv-virtualenv를 이용한 가상환경 생성
  - `pyenv virtualenv 3.7.13 django-envs`
    - pyenv로 가상 환경 생성하기
  - `pyenv uninstall django-envs`
    - pyenv로 생성한 가상 환경 지우기
  - `pyenv versions`
    - django-envs: 심볼릭 링크

3. pyenv로 설치한 파이썬 적용 및 django 2.2 설치
  - `global 가상환경`
    - 시스템 전역에 적용하는 환경
    - global 가상환경을 적용하면 따로 지정해 주지 않아도 기본적으로 global환경을 사용
  - `local 가상환경`
    - 특정 디렉토리 내부에서만 적용되는 환경
    - global 환경이 지정되어 있더라도 local환경이 적용됨
  - `pyenv global 3.8.13`
    - 가상환경 global 적용하기
  - `cd codeit-django`
  - `pyenv version`
  - `pyenv local django-envs`
  - `pyenv version`

3. django 설치
  - `pip3 install django==2.2`
    - 파이썬 패키지 설치하기
  - `django-admin --version`
    - 2.2
  - `pip3 list`
    - 설치되어 있는 파이썬 패키지 목록 보기

## 07. 개발 환경 구성 꿀팁 (Windows)
1. 폰트 설정하기
  - Google > d2coding > Github > Ver 1.3.2 > D2Coding-Ver1.3.2-20180524.zip > 압축 풀기
  - 시작 > 글꼴 설정
  - D2Coding > 3개 글꼴 > 드래그 앤 드롭으로 설치
  - WSL > 글꼴 변경

2. 윈도우 탐색기로 WSL 사용하기
  - `cd codeit-django`
  - `explorer.exe .`
    - 창이 열림

3. 파일 확장자 보이도록 설정

## 08. VSCode 더 편하게 사용하기
1. Visula Studio Code

2. 확장 프로그램 (Extension)
  - Extension > django
  - Python Extension
  - Django Extension
  - vscode-icons
  - indent-rainbow : 들여쓰기
  - Bracket Pair Colorizer2

3. VSCode에서 파이썬 버전 선택하기
  - `Control + p`
    - 명령 팔레트를 실행

## 09. 커맨드 라인 더 편하게 사용하기
1. Zsh Shell
  - 제트 쉘, 지 쉘
  - `echo $SHELL`
  - Zsh Shell 설치하기 for WSL Ubuntu
  - `sudo apt-get install zsh`
  - chsh -s `which zsh`
  - WSL 재실행 > 0
  - echo $SHELL

2. Oh-My-Zsh
  - sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

3. Zsh 테마 변경 및 설정
  - cd ~
  - code .
  - .zshrc > ZSH_THEME="robbyrussell" > "agnoster"
  - pyenv 설정하기
  - .bashrc > 3줄 복사해서 > .zshrc 로 붙여넣기
    - 그러나 .zsh_profile에 추가해야 함 (질문보기로 해결)

4. 재미있는 Zsh 플러그인
  - **4.1 zsh-syntax-highlighting**
  - cd ~
  - `git clone https://github.com/zsh-users/zsh-syntax-highlighting.git`
  - echo "source ${(q-)PWD}/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh" >> ${ZDOTDIR:-$HOME}/.zshrc
  - **4.2 autojump**
  - cd ~
  - git clone https://github.com/wting/autojump.git
  - cd autojump
  - ./install.py
  - 아래 2줄 복사
```
[[ -s /home/codeit/.autojump/etc/profile.d/autojump.sh ]] && source /home/codeit/.autojump/etc/profile.d/autojump.sh
autoload -U compinit && compinit -u
```
  - cd ~
  - code .
  - WSL 재실행
  - **4.3 zsh-autosuggestions**
  - cd ~
  - git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
  - cd ~
  - code .
  - .zshrc 에 수정 
```
plugins=(git zsh-autosuggestions)
```


