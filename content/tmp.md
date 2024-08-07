---
title: 정보처리산업기사 실기 요약
---
## 1. OS
### i. OS
- OS (Operating System) : 자원 관리, 스케줄링, 인터페이스 등을 제공하는 프로그램의 모임
	목적
	1. 처리 능력(Throughput) 향상
	2. 반환 시간(Turn Around Time) 단축
	3. 사용 가능도(Availability) 향상
	4. 신뢰도(Reliability) 향상
- 운용 기법
	- 일괄 처리(Batch)
	- 다중 프로그래밍 : 1 CPU, 여러 Program
	- 시분할(Time Sharing) : 번갈아가며, Round Robin
	- 다중 처리 : 여러 CPU, 여러 Program
	- 실시간 처리
	- 다중 모드 처리 : 여러 기법 합침
	- 분산 처리 : 여러 computer, 하나의 작업
### ii. 종류
- Windows (Microsoft)
	- GUI (Graphic User Interface)
	- 선점형 멀티태스킹 (Preemptive)
	- PnP (Plug and Play)
	- OLE (Object Linking and Embedding)
	- 파일명 255자까지
- UNIX (AT&T 연구소, MIT)
	- 시분할 시스템 / 다중 사용자, 다중 작업
	- 개방형 시스템 (Open system) / C언어 (이식성 좋음)
	- 트리 구조 파일 시스템
	- 커널(Kernel) / 쉘(Shell) / 유틸리티 프로그램(Utility Program)
- LINUX (Linus Torvalds)
	- UNIX 기반, 호환성 좋음
- MacOS (Apple) / Android (Google) / iOS (Apple)
### iii. Shell 명령어

| 역할         | Windows | UNIX/LINUX    |
| ---------- | ------- | ------------- |
| 파일 목록 표시   | DIR     | ls            |
| 파일 복사      | COPY    | cp            |
| 파일 삭제      | DEL     | rm            |
| 파일 내용 표시   | TYPE    | cat           |
| 파일 이름 변경   | REN     | mv (이름 변경 가능) |
| 파일 이동      | MOVE    | mv            |
| 디렉터리 생성    | MD      | mkdir         |
| 작업 디렉터리 변경 | CD      | cd            |
| 디렉터리 삭제    | RMDIR   | rmdir         |

- Windows
	- CLS : 화면 내용 지우기
	- FIND \[문자열\] \[파일명\] : 파일 내의 문자열 검색
	- CHKDSK : 드라이브 상태 점검
	- FORMAT : 드라이브 초기화
	- ==ATTRIB== : 파일 속성 변경(+/-)
		- R 읽기 전용 속성
		- A 저장/백업 속성
		- S 시스템 파일 속성
		- H 숨김 파일 속성
- UNIX/LINUX
	- ==chmod== : 파일 보호 모드 설정
		- u 소유자 / g 그룹 / o 다른 사용자 / a 모두
		- r 읽기 / w 쓰기 / x 실행
	- chown : 소유자 변경
	- find : 파일 검색
	- fsck : 파일 시스템 검사/보수
	- kill : 프로세스 종료(PID) / killall : 프로세스 종료(프로세스명)
	- fork : 프로세스 생성
	- ps : 실행 중인 프로세스 표시
	- pwd : 작업경로 표시
	- top : 프로세스 / 메모리 사용 현황 표시
	- who : 접속자 표시
### iv. 스케줄링
- 비선점 스케줄링
	1. FCFS/FIFO : 도착한 순서대로
	2. SJF(Shortest Job First) : 대기 상태 중 가장 짧은 것부터
	3. HRN(Highest Response-ratio Next)
		$\displaystyle\frac{W+S}{S}$ ($W$ : 대기 시간, $S$ : 서비스 시간)
	4. 기한부(Deadline) : 프로세스마다 시간 내에 완료
	5. 우선순위(Priority) : 대기 상태 중 우선순위 높은 것부터
- 선점 스케줄링
	1. 선점 우선순위 : 우선순위 높은 것부터
	2. SRT(Shortest Remaining Time) : 선점 SJF 방식
	3. RR(Round Robin) : 시분할, 할당량만큼 돌려가며 사용
	4. 다단계 큐 (MQ) : 그룹에 따라 다른 준비상태 큐
	5. 다단계 피드백 큐 (MFQ) : 프로세스가 그룹 이동 가능
- 교착상태 (Deadlock)
	- 상호 배제, 점유와 대기, 비선점, 환형 대기
	- 은행원 알고리즘 -> 회피 기법

## 2. DB
- DB(DataBase) : 공동으로 사용될 데이터를 중복 배제하여 통합 / 항상 사용할 수 있도록 운영하는 운영 데이터
	- 통합된 데이터 (Integrated Data) : 중복 배제
	- 저장된 데이터 (Stored Data)
	- 운영 데이터 (Operational Data) : 업무 수행에 필요한 자료
	- 공용 데이터 (Shared Data) : 여러 응용 시스템이 공동 소유/유지 자료
- DBMS(DB Management System) : 관리 소프트웨어
	- 정의(Definition)
	- 조작(Manipulation)
	- 제어(Control)
- 독립성
	- 논리적 독립성 (응용 프로그램 <-> 데이터베이스)
	- 물리적 독립성 (응용 프로그램 <-> 물리적 장치)
- 무결성
	- 개체 무결성 : 기본키는 Null이나 중복 불가능
	- 참조 무결성 : 외래키는 참조 기본키에 있거나 Null
	- 도메인 무결성 : 모든 값이 도메인에 존재
- 스키마(Schema) : 구조/제약조건에 관한 전반적인 명세
	- 외부 스키마 (사용자 개인의 입장)
	- 개념 스키마 (전체적 구조, 하나만 있음)
	- 내부 스키마 (물리적 저장장치의 입장)
- 설계 순서
	1. 요구 조건 분석
	2. **개**념적 설계
		- 개념 스키마 설계, 트랜잭션 모델링
		- E-R 모델 (개체 : 사각형 / 관계 : *마름모* / 속성 : 타원)
	1. **논**리적 설계
		- 논리 스키마 설계, 트랜잭션 인터페이스 설계
	2. **물**리적 설계
	3. 구현
- 관계형 DB 용어
	- 튜플(카디널리티, 기수), 속성(디그리, 차수), 도메인
- 관계대수 / 관계해석
	- 관계대수 (절차적)
		- Select($\sigma$), Project($\pi$), Join($\bowtie$, cartesian 이후 select), Division($\div$, 속성 기준으로 select)
		- UNION($\cup$), INTERSECTION($\cap$), DIFFERENCE($-$), CARTESIAN($\times$)
	- 관계해석 (비절차적)
- 트랜잭션 : 한꺼번에 모두 수행되어야 할 일련의 연산
	- ACID
		1. Atomicity (원자성) : 회복
		2. Consistency (일관성) : 무결성 제약 조건, 동시성 제어
		3. Isolation (독립성) : 동시성 제어
		4. Durability (지속성) : 회복
	- CRUD 분석 (Create/Read/Update/Delete)를 프로세스마다 따지는 분석법
- 정규형
	- 1NF : **도**메인이 원자값
	- 2NF : **부**분적 함수 종속 제거
	- 3NF : **이**행적 함수 종속 제거
	- BCNF : **결**정자이면서 후보키 아닌 것 제거
	- 4NF : **다**치 종속 제거
	- 5NF : **조**인 종속성 **이용**
## 3. Network
### i. Internet
- IPv4 : 32bit
	- Subnetting (ex.192.168.0.1/24)
		서브넷 마스크 1이 24bit
		네트워크 주소(첫 주소) / 브로드캐스트 주소(마지막 주소)
- IPv6 : 128bit
	- QoS(Quality of Service) 지원
	- 유니/멀티/*애니*캐스트 지원
- NAT(Network Address Translation) : 정식 IP - 다량 사설 IP 할당
### ii. OSI 7계층

| 계층        | 데이터 단위 | 역할                     | 표준                       | 관련 장비                                                          |
| --------- | ------ | ---------------------- | ------------------------ | -------------------------------------------------------------- |
| 물리 계층     | 비트     | 실제 접속/절단               | RS-232C, X.21            | 리피터, 허브(회선 통합 관리)                                              |
| 데이터 링크 계층 | 프레임    | 연결 설정(동기화/오류 제어/순서 제어) | HDLC(주제정검), MAC          | 랜카드(NIC, 컴퓨터-네트워크 연결), 브리지(LAN 내부 연결, 트래픽 분산), 스위치(LAN-LAN 연결) |
| 네트워크 계층   | 패킷     | 경로 설정(라우팅)             | X.25, IP(비연결형)           | 라우터(최적 경로 선택)                                                  |
| 전송 계층     | 세그먼트   | 투명한 데이터 전송, 종단 시스템     | TCP(연결형), UDP(비연결형, 실시간) | 게이트웨이(프로토콜 다른 네트워크 연결, 변환)                                     |
| 세션 계층     | 메시지    | 관련성 유지 / 대화 제어         |                          |                                                                |
| 표현 계층     |        | 데이터 변환, 암호화, 압축        |                          |                                                                |
| 응용 계층     |        | 서비스 제공                 |                          |                                                                |
- 프로토콜(Protocol) : 통신 규약 (구문/의미/시간)
### iii. TCP/IP
- 네트워크 액세스 - 인터넷 - 전송 - 응용
- 응용 계층

| 프로토콜   | 내용         | 포트  |
| ------ | ---------- | --- |
| FTP    | 파일 전송      | 21  |
| SSH    |            | 22  |
| TELNET | 원격 접속      | 23  |
| SMTP   | 전자 우편      | 25  |
| DNS    | 도메인 주소 매핑  | 53  |
| HTTP   | HTML 문서    | 80  |
| POP3   |            | 110 |
| NNTP   |            | 119 |
| IMAP   |            | 143 |
| SNMP   | 네트워크 정보 송신 | 161 |
| HTTPS  |            | 443 |
- 인터넷 계층

| 프로토콜 | 내용            |
| ---- | ------------- |
| IP   | 주소 지정 / 경로 설정 |
| ICMP | 제어 메시지 관리     |
| IGMP | 멀티캐스트 그룹 유지   |
| ARP  | IP -> MAC     |
| RARP | MAC -> IP     |

### iv. 경로 제어
- 경로 제어

| 프로토콜 | 내용                                                                 |
| ---- | ------------------------------------------------------------------ |
| IGP  | 자율 시스템 내의 라우팅<br>- RIP(소규모, Bellman-Ford)<br>- OSPF(대규모, Dijkstra) |
| EGP  | 자율 시스템 간 라우팅                                                       |
| BGP  | EGP 보완, 라우팅 테이블 교환                                                 |
- 흐름 제어 (송수신측 패킷 수 제한)
	- 정지 - 대기 : 하나씩 전송 후 ACK 받기
	- 슬라이딩 윈도우 : 미리 정해진 패킷 수(윈도우 크기)로 전송, 상황에 따라 윈도우 변화
- 폭주 제어 (네트워크 내의 패킷 수 제한)
	- 느린 시작 (2배씩 증가시키며 시작)
	- 혼잡 회피 (혼잡하면 +1)

## 4. Programming & SQL
### i. Programming
- 연산자 우선순위 (C 기준)

| 우선순위   | 설명                 | 연산자       |
| ------ | ------------------ | --------- |
| **1**  | 단항 연산자             |           |
| **2**  | 곱셈 / 나눗셈 / 나머지     | * / %     |
| **3**  | 덧셈 / 뺄셈            | + -       |
| **4**  | 시프트 연산자            | << >>     |
| **5**  | 관계 연산자             | < <= > >= |
| **7**  | 관계 연산자 (같은/같지 않은)  | == !=     |
| **8**  | 비트 AND 연산자         | &         |
| **9**  | 비트 XOR 연산자         | ^         |
| **10** | 비트 OR 연산자          | \|        |
| **11** | 논리 AND 연산자         | &&        |
| **12** | 논리 OR 연산자          | \|        |
| **13** | 삼항 조건 연산자          | ? :       |
| **14** | 대입 연산자 및 복합 대입 연산자 | =         |
| **15** | 쉼표 연산자             | ,         |
- 형식 지정자 (C/Java)
`%[플래그(flag)][폭(width)][.정밀도][크기(length)]서식문자(specifier)`
폭으로 출력칸 확보
정밀도(정수는 최소 자리수, 소수는 소수점 이하 자리수, 문자열은 문자 최대 개수)
### ii. SQL

## 5. Application Test
### i. 기본 원리
- 파레토 법칙 : 20%에서 80%의 오류 발견
- 살충제 패러독스 : 동일 테스트케이스로 하면 더 이상 결함 발견 불가
- 오류-부재의 궤변 : 결함이 없어도 사용자의 요구사항 만족이 중요
### ii. 분류
- 정적 테스트 : 워크스루(오류 조기 검출), 인스펙션(개선 방법 제시)
- 동적 테스트
	- 화이트박스 테스트
		- 기초 경로 검사 / 조건 검사 / 루프 검사 / 데이터 흐름 검사
	- 블랙박스 테스트
		- 동치 분할 검사(동치 클래스 분해) / 경계값 분석 / 원인-효과 그래프 검사 / 오류 예측 검사 / 비교 검사
### iii. V-모델
요구사항 - 분석 - 설계 - 구현 / 단위 테스트 - 통합 테스트 - 시스템 테스트 - 인수 테스트
하향식 통합 테스트 : 스텁
상향식 통합 테스트 : 드라이버 / 하위 모듈을 클러스터로 결합
### iv. 용어
- 테스트 케이스(TC) : 테스트 항목의 명세서
- 테스트 시나리오 : 여러 개의 TC를 묶은 집합
- 테스트 오라클 : 테스트 결과 대입하여 비교하는 기법
- 테스트 하네스 도구 : 환경 시뮬레이션으로 정상적으로 테스트되도록 하는 도구
- 결함 관리 측정 지표 : 결함 분포 / 결함 추세 / 결함 에이징