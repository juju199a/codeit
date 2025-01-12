# Amazon EC2 Linux 실습
## 1교시 (실습) 저번주에 배운 것 복습. WebServer 만들기
- `Google 크롬 익스텐션`
- `내 도메인 한국`

- 서울리즌 > 인스턴스 시작
- webserver
- Amazon Linux
- = CentOS 9 과 똑같은 배포판이다.
- 맥 = 시간당 과금
- 아마존, RedHat = 사용한 만큼
- 아마존 리눅스 2
- 인스턴스 유형: t2 micro 무료 버전
- 시간당 과금
- 통합 빌링이 되면 개인적으로 썼던 것, 크레딧은 쓸 수 없다.

### PHP
- 소스 파일 다운로드
- EC2가 부팅되면서 설치된다.
```sh
#!/bin/sh
​
#Install a LAMP stack
dnf install -y httpd wget php-fpm php-mysqli php-json php php-devel
dnf install -y mariadb105-server
dnf install -y httpd php-mbstring
​
#Start the web server
chkconfig httpd on
systemctl start httpd
​
#Install the web pages for our lab
if [ ! -f /var/www/html/immersion-day-app-php7.zip ]; then
   cd /var/www/html
   wget https://icshin-lab.s3.ap-northeast-2.amazonaws.com/edu-ctec/immersion-day-app-php7.zip
   unzip immersion-day-app-php7.zip
fi
​
#Install the AWS SDK for PHP
if [ ! -f /var/www/html/aws.zip ]; then
   cd /var/www/html
   mkdir vendor
   cd vendor
   wget https://docs.aws.amazon.com/aws-sdk-php/v3/download/aws.zip
   unzip aws.zip
fi
​
# Update existing packages
dnf update -y
```

- AWS SDK for PHP
- `dnf update -y` 실제 쉘 상태에서 쭉 업데이트 하다가 마지막에 할것인가 말 것인가 단계가 나온다.
- 자동으로 `y`라고 해라
- `y`를 안하면 타임아웃이 되어 버린다.

- AWS에 올라간 퍼블릭 키가 포함된 것으로 키페어가 만들어진다.

- `http://15.165.17.253`
- aws 보안 

### EC2 보안
- 인바운드 규칙 편집
- All Any Any로 다 열어 준다.

### 프로비저닝 완료, 쉘접속
- 브라우저 방식으로 하는 SSH

- sudo vi userdata.sh
- sudo vim userdata.sh

- VS Code > Remote Explorer
```
Host: 공인 IP (호스트명)
  HostName: 공인 IP
  User: ec2-user
  IdentityFile '(\)역슬래쉬'
```
- MobaXterm
- Remote host: 15.165.17.253
- Specify username: ec2-user
- Advanced SSH settings > Use private key > `juju199a-koreait-keypair.pem`

## 2교시 AWS Cloud Practitioner Essentials
- 스토리지 및 데이터베이스
- S3 스토리지 오브젝트 스토리지
- AWS 데이터베이스 종류
- EBS (Elastic Block Store)
- NoSQL (다이나 모드)
- 블록 스토리지
  - 데이터의 조각
  - 트랙, 실린더, 엑세스 암
  - 블록 스토리지는 여기에 저장을 한다.
  - `토렌토`
  - 99% 끊기면 99% 블록만큼은 읽을 수 있다.
- 객체 스토리지
  - `키와 메타데이터와 벨류`. 대용량 스토리지. 오브젝트 스토리지
  - 1테라 저장 시 99%에서 끊긴다. > 읽을 수 없다.
  - 1테라 바이트 이상 되면 쓸 수 없다.
- 연결된 인스턴스
  - 인스턴스 스토어
  - 1U 2U 서버
  - 데이터 센터 > AS > 리전
  - `물리 서버`
  - CPU > 물리서버 > OS > 가상화 > EC2 (EBS 블록 스토리지를 쓴다.)
  - 물리서버를 쓰는 것이 인스턴스 스토리지이다.
  - 물리서버의 굉장히 빠른 속도를 사용한다.
  - 인스턴스가 중지 되면 데이터가 모두 삭제된다.
  - 철저한 자본주의적 비지니스이다.
  - 스탑앤 스타트

### EBS 볼륨
- EC2 - EBS 볼륨
- EBS 8G 볼륨
- EC2 <- (네트워크 구간) -> EBS 볼륨
- 데이터를 종료하지 않는 이상 인스턴스는 계속 남아 있다.
- **EC2를 삭제하면 EBS에도 같이 삭제된다.**
- EC2에 대한 백업
- 스냅샷 백업 (특정 시간대까지만 저장)
- 변경된 데이터만 백업 (증분 백업, 인크리멘탈 백업)
- AMI 백업 (풀백업) : OS가 들어가 있는 채로 백업
- 스냅샷 : 데이터만 백업
- 실제 데이터는 1GB -> 스냅샷 (데이터만 백업)
- 주중엔 스냅샷 백업
- 주말엔 AMI 백업

### `객체 스토리지`
- `Simple Storage Service` 
- S3
- 데이터, 메타데이터, 키
- **매우 중요** 데이터가 99%에서 멈추면 99% 만큼 쓸 수 없다.
- EC2는 서브넷 안에서
- VPC 밖에서 사용
- 스토리지 클래스 (비용 대비 등급)
  - `S3 Standard`: S3의 정가이다. 몇 백테라가 들어간다. 3개의 복제를 스스로 한다. 3개의 에이젯
  - `S3 Standard-IA `: 자주 액세스 하지 않는 데이터를 여기에 저장. 이월 상품
  - `S3 One Zone-IA` : 하나의 데이터 공간. 에이젯. 가격이 싸다.
- SLA
  - 가용성: 99.99%
  - S3 Intelligent-Tiering : 액세스가 많으면 Standard, 액세스 적으면 Standard-IA
  - S3 Glacier Instance Retrieval: 영구 보간 1달에 1기가 10원 안나옴 0.0114
  - S3 Glacier Flexible Retrival: 장기 보관용 아카이브 백업
  - S3 Glacier

### 지식 확인
- 비용 절감. 자주 액세스: S3 Standard-IA

### 파일 스토리지
- 파일 스토리지: NAS를 넣으면 안된다.
- S3는 피어 투 피어 이다.
- 디렉토리 체계가 없다.
- EFS: Elastic File System

## 3교시 베스쳔, 데이터베이스
- 브라우저 기반의 연결
- 접속 로그가 남는다.
- `Session Manager` 이다.
- SSH 클라이언트
- 퍼블릭과 클라이언트
- 인터넷을 통해서 프라이빗을 주
- 노트 북 > 프라이빗 중계 서버 > 프라이빗에 접속한다.
- SSH 클라이언트
- 베스쳔
- 중계서버에 카피
- 키페어 파일에 권한 부여가 되어 있어야 한다.
- `ssh -i` 
- 프라이빗 
- VPC > 2A
- VPC > 2C
- 키페어가 있어야 한다. > `SSH 클라이언트`
- 요즘은 `클라우드 쉘`에서 `파일 업로드`
- `aws-cost.sh`
- AWS가 바이러스까지 체크하지 않는다.
- gcp 런쉘
- 클라우드 런

### 관계형 데이터베이스
- 엑셀 같은 형태
- 모든 개발이 DB에 의존
- 테이블이 추가가 어렵다.
- SQL
- Oracle, MySQL, MariaDB

### 비관계형 데이터베이스
- JSON 형태 (키: 벨류)
- 구조가 단순
- 다이나믹 스키마
- 몽고 DB
- SNS에서는 NoSQL
- 개발이 자유롭다.

### Amazon Relational Database Service
- Amazon RDS 데이터베이스 엔진
  - RDS는 DB 인스턴스. EC2이다.
  - EC2 + EBS
  - 그대로 싱가폴로 복사 옮길 수 있다.
- Amazon Aurora
  - 구조가 다르다.
  - EC2(CPU) + EBS (Cluster 스토리지)
  - 싱가폴로 옮길 수 없다.
  - 비용 절감? -> 오히려 비싸다.
  - `AZ` 비용이 바싸다.
  - 대신 가용성, 내구성은 아주 높다.
  - 엔터프라이즈급 관계형 데이터베이스스

## Amazon DynamoDB
- Amazon DynamoDB
- 서버리스 데이터베이스
- 키 값 데이터베이스
- 하루 10조 개 요청으로 확장 

### AWS Database Migration Service
- 데이터 이전을 쉽게 해 준다. (DMS)
- Oracle 골든 게이트
- 원본 데이터 베이스 > DMS > Amozon Aurora
- 실시간 전송을 해 준다.
- 쌓이는 대로 온라인으로 

### 추가 데이터베이스 서비스 (1/2)
- Amazon Redshift
  - 포스트그레 기반
- Amazon Neptue
  - 그래프 형
- Amazon Managed Blockchain
  - 블록체인
- Amazon ElasticCache
  - 메모리 상
- Amazon DynamoDB Acclerator
  - 다이나모 DB에서 캐쉬기능
  - 다이나모 DB를 게임에서 많이 쓴다.
  - 마이크로 초까지 향상

- 지식확인
- 아카이브에 최적화 = Glacier 이다.
  - 비용 절감 = S3 Glacier
- EBS 볼륨
  - EBS 볼륨은 단일 가용 영역
  - Amazon EFS
- 고객 S3에 저장
  - Amazon 
- DynamoDB = JSON을 쓴다.
  - RDS <-> D
  - RDS 정교하고, 굉장히 빠를 필요가 없을 때,
  - 정합성 무결성
  - DynamoDB = NoSQL
  - 중복을 허용
  - 무조건 저장하다.
  - 두가지를 똑같이 쓸 수 없다.

### 모듈 6 보안
- 버킷에 권한 넣고 한다.
- 공동 책임 모델 (라스폰스 쉐어드 모델)
- AWS 책임
  - 인프라 책임
  - AWS 가상화 자체가 해킹 당했을 때
- 고객 책임
  - 고객 데이터
  - 방화벽 구성
  - 트래픽 보호
  - 최신 업데이트
  - 호스트 기반 방화벽 (EC2에 깐다.)
  - 네트워크 방화벽과 구별

- 역삼동 센터 필드 (18층)
- 하드웨어 소프트웨어

- EC2 에서 보안 그룹 구성
- 서버 유지 관리 > AWS

### IAM 서비스
- 커피숍
- 코스트 코, 교대 인증
- POS 시스템에 엑세스 함
- AWS Identity and Access Management (IAM)

### IAM 기능
- IAM 사용자
- IAM 정책
- IAM 그룹
- IAM 역할
- 다중 인증

- 보안 주체 (Entity)
## IM 사용자
- 로그인
- 유저만의 Access
- 처음엔 백지 상태
- 사용자에게 권한을 주지 말고, 그룹에 포함시켜서, 그룹에 권한을 넣고,
- 그 권한을 상속 받도록 해라
- 즉 그룹에 정책을 넣고, 그룹과 사용자를 연결한다.
- `IAM 정책` = `IAM 폴리시`
- IAM 정책 -> IAM 역할 -> EC2
- 사용자가 롤(역할)에 `위임`한다.

### AWS 권한 간과하지 마라
- AWS 권한이 맞게 들어가야 사용 가능하다.

### AWS 계정 루트 사용자
- root 사용자

### IAM 
- IAM은 특정 사용자에게 발급된다.

### IAM 정책 
- 상세한 정책을 만들 수 있다.
- 제공하는 기본 정책 있다.
- 커스텀 정책이 있다.

### 리소스 정책
- RESTFul API
- s3:ListObject
- s3:GetObject
- `awsdoc-example-bucket/*`
- S3리소스에 버켓 정책이 들어가는 구조

### MFA 인증
- AWS 리소스 접근

### AWS Organizations
- 프렌차이즈 카페 
- 지역간 나라간 특정한 조직
- 통합 관리할 서비스가 필요하다.
- IAM을 관리하는 서비스이다.
- Oranization에서는 계정을 만들 수 있다.
- 서비스 제어 정책 (SCP)
- OU = IAM Oranization과 같다.

- 지식 확인
- 계정에 넣을 수 있고, OU에 권한을 넣을 수 있다.

### 컴플라이언스
- AWS Artifact
- 안전해요. 우리 것 많이 쓰세요.
- ISO 인증
- 42001 AI ISO인증
- ISMS
- Artifact에서 할 수 있는 것
- SCP (서비스 제어)

### AWS WAF
- Web Application Firewall
- CDN에 들어 있다.
- WAF에서 먼저 거르고, 합법적인 트래픽 
- WAF는 룰이 늘어날 때마다 비용이다.
- `관리형 규칙` > 제공하는 것
- `사용자 지정 규칙`

### AWS Shield
- AWS Shield 
- DDoS 방어
- 기본적으로 ISO 4계층까지 막아주는데, 어플리케이션까지 보호 하는 것은
- 굉장히 비싸다.
- 방어, 분석, 차단
- 기본
- 스탠다드
- EC2 취약점 = 

### AWS Key Management Service
- 키관리 어떻게 할 것인가.
- 암호화 또는 암호화 해독

### Amazon GuardDuty
- 네트워크 및 계정 활동
- 위협을 탐지
- 탐지 결과를 검토한다.

- 지식 확인
- IAM 정책에 대한 설명은?
  - 자격증명 = 로그인
- 임시 액세스 권한
  - 롤
- 최소 권한
  - 특정 작업만 
- DDoS
  - Shield
- KMS
  - 암호화 키 관련

## 4교시 모니터링 분석
### AWS CloudWatch
- 사용한 만큼 과금
- 어느 정도 썼는지
- Cloud Watch
- 지표: 매트릭
  - CPU
  - 네트워크
  - Min Max AVG
  - 5분 단위가 무료
  - 1분 단위가 유료
- 임계값
  - 한계값
- 작업
  - 임계값에 도달하면 어떻게 할 것인가.
- 온프레미스도 가능하다.
- apache log에 access 로그, error log
- 어플리케이션 로그, 시스템 로그
- event log
- ssh log
- AWS CloudWatch 대시보드

### AWS CloudTrail
- 여러 IAM의 추적이 가능하냐? 
  - 그렇다. CloudTrail
  - API 날린 것 다 남는다.
  - 비정상적인 계정 활동 다 남는다.

(지식 확인)
- 실시간 Watch는 아니다. 5분 무료 1분 유료
- 인프라 전체

### AWS Trusted Advisor
- 월 100달러의 서포트를 할 때 나온다.
- 컨설턴트 커피숍을 관찰
- 컨설턴트, 제시: AWS
- 변경: 고객
- 5가지 범주
  - 비용 최적화
  - 성능
  - 보안
  - 내결합성: 이중화 구성
  - 서비스 한도: EC2는 20개가 제한
  - 100개 이상 쓰면 신청을 해야 한다.
  - 미리 늘려 놔야지 쓸 수 있다.

- 지식확인
- CloudWatch
  - 리소스의 사용량 및 성능을 모니터링
- 버킷을 검토 하는데 쓴느 것
  - AWS Trusted Advisor
- AWS Trusted Advisor 대시 보드
  - 성능, 내결합성

### AWS Cloud 
- 프리티어
- Organizations 및 통합 결제

### 프리티어
- 

- 종량제: 온디멘드
- 예약한 경우: RIA
  - 선납 후
- 볼륨 기반 할인 적용으로 비용 감소
  - 특정 리소스 갯수가 아니라 용량으로 따진다.
  - 네트워크 볼륨
  - 게임사들이 CDM으로 계약 맺어서 쓰고 있다.
- 요금 계산기
- 리전 마다 비용 마다 다르다.
- AWS Lambda 서비스 요금
  - 동시 병렬처리를 해서, 과금이 갑자기 많이 나올 수 있다.
- Amazon EC2 요금
  - 스팟 인스턴스로 비용 절감

- Amazon S3 요금
- 아웃바운드 이면 과금이 된다.
- AWS로 들어가는 비용은 없다.
- 리전 마다 과금이 된다.

- 지식 확인
- 1년으로 계약
- 리전별 서비스 비용
- MSP 브록커 (CBP, CSP)
- MSP에 붙이는 것은 `통합결제`이다.
- 결제 과금

- 대량 구매 할인

### AWS Budgets

### Cost Explorer
- 비용 및 사용량을 그래프로 볼 수 있다.
- GITOPS : 깃허브 위한 운영
- FINOPS : 비용 절감을 위한 운영
- 비용절감 RI

### AWS Support 플랜
- Developer
- Business
- Enterprise On-Ramp

### AWS Marketplace
- AWS Marketplace 범주
- 소프트 웨어, EC2 AMI 형태로 올라간다.

- 지식 확인
- 비용 시각화: Cost Explorer
- 임계값 초과: Budget
- TAM: Enterprise

### AWS Migration
- AWS Cloud Adoption Framework
- 관점 (6가지 카프)
  - 비즈니스
  - 인력
  - 거버넌스
  - 운영
  - 보안
  - 플랫폼
- 지식확인
- 7가지 마이그레이션 전략
- 재배치
- 리호스팅
- 리플랫포밍
- 리팩터링, 리아키텍팀
- 서버리스

### AWS Snow 패밀리
- 오프라인으로 데이터를 넘긴다.
- AWS Snowcone
- 손바닥 위에 올라가는 IOT 전용
- AWS snowball
- AWS snowmobil
- 컴퓨팅 디바이스
- GPU까지 들어 있다.

### AWS를 통한 혁신
- 서버리스 애플리케이션
- 인공 지능 (AI)
- 기계 학습 (ML)

### Amazon CodeWhisperer 소개
- IDE 및 코드 편집기용 AI 기반 코드 생성기
- 깃 허브 
- 커서 AI
- AI 기반 보안 스캐너
- 개발자에게 제공되는 이점

### Well-Architected Framework
- 잘 만든 아키텍트
- 운영 우수성
- 설명서, 장애 예상
- 지원 프로세스 및 
- 모든 계층에 보안 적용
- 웹, 데이터베이스, 백용
- https 방식
- 보안 모범 사례 자동화
- 안정성
- 가용성
- 서버리스 아키텍쳐 사용
- 비용 최적화
- 지속 가능성
- CI/CD
- 보안 관점
- 운영 관점
- 리호스팅, 유지
- Snowcone - 8TB
- Snowball Edge Storage - 80TB의 가용 용량
- 6G가 있어야 한다.
- 복구 - 안정성

## 실습
- Cloud Formation 을 만든다.

My Public IP: 58.141.234.62
https://bit.ly/Edu-koreait

버킷명
juju199a-koreait-s3-lab

http://172.31.1.10
http://43.202.41.172

192.168.0.2

zmf

## 삭제
1. 클라이드 포메이션 
  - 그러면 EC2도 삭제 된다.
2. 오전에 만든 webserver 삭제
3. S3 버킷 (2개 만듦)
  - 안에 내용 부터 지워야 버킷이 삭제 된다.
  - 내용 삭제 > 버킷 삭제
4. IAM 롤은 삭제 안함






