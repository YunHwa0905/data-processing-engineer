# 정보처리기사

Java · Python · C · SQL · 운영체제 · 보안을 아우르는 정보처리기사 필기 5과목 학습 노트 저장소입니다.

---

## 기술 스택

![Java](https://img.shields.io/badge/Java-007396?style=flat&logo=openjdk&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![C](https://img.shields.io/badge/C-00599C?style=flat&logo=c&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat&logo=mysql&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat&logo=linux&logoColor=black)
![Network](https://img.shields.io/badge/TCP%2FIP-0052CC?style=flat&logo=cisco&logoColor=white)
![Security](https://img.shields.io/badge/Security-FF0000?style=flat&logo=owasp&logoColor=white)
![Markdown](https://img.shields.io/badge/Markdown-000000?style=flat&logo=markdown&logoColor=white)

---

## 프로젝트 구조

```
data-processing-engineer/
├── 1_Software Design/                               # 소프트웨어 설계
│   ├── 01_요구사항 확인.md                            # 소프트웨어 생명 주기, 요구사항 분석
│   ├── 02_화면 설계.md                                # UI/UX 설계, 프로토타입
│   ├── 03_애플리케이션 설계.md                         # 아키텍처 패턴, 모듈·디자인 설계
│   └── 04_인터페이스 설계.md                           # 시스템 연계, 인터페이스 정의
│
├── 2_Software Development/                          # 소프트웨어 개발
│   ├── 01_데이터 입출력 구현.md                        # 자료구조, 정렬·검색 알고리즘
│   ├── 02_통합 구현.md                                # 모듈 통합, 빌드 도구
│   ├── 03_제품 소프트웨어 패키징.md                     # 릴리즈 노트, 형상 관리
│   ├── 04_애플리케이션 테스트 관리.md                   # 화이트박스·블랙박스 테스트
│   └── 05_인터페이스 구현.md                           # REST API, JSON, XML, AJAX
│
├── 3_Database Development/                          # 데이터베이스 구축
│   ├── 01_논리 데이터베이스 설계.md                     # ER 모델, 정규화(1NF~BCNF)
│   ├── 02_물리 데이터베이스 설계.md                     # 인덱스, 파티셔닝
│   ├── 03_SQL 응용.md                                # DDL·DML·DCL 기초
│   ├── 04_SQL 응용.md                                # 집계함수, 서브쿼리, JOIN
│   └── 05_데이터 번환.md                              # ETL, 데이터 마이그레이션
│
├── 4_Utilization of Programming Languages/          # 프로그래밍 언어 활용
│   ├── 01_서버 프로그램 구현.md                        # 서버 개발 패턴, 프레임워크
│   ├── 02_프로그래밍 언어 활용.md                      # Java·C·Python 자료형, 변수, OOP
│   └── 03_응용 SW 기초 기술 활용.md                    # 운영체제, TCP/IP 네트워크
│
└── 5_Information System Development and Management/ # 정보시스템 구축 관리
    ├── 01_소프트웨어 개발 방법론 활용.md                 # 애자일, CMMI, SPICE
    ├── 02_IT 프로젝트 정보 시스템 구축 관리.md            # IT 거버넌스, 비용 산정
    ├── 03_소프트웨어 개발 보안 구축.md                   # Secure SDLC, 보안 3요소
    └── 04_시스템 보안 구축.md                           # 접근 제어, 암호화, 방화벽
```

---

## 학습 방법

별도 설치 없이 GitHub에서 바로 열람할 수 있습니다.

```bash
# 로컬에서 열람하기
1. 저장소 클론
   git clone https://github.com/YunHwa0905/data-processing-engineer.git

2. VS Code로 열기
   code data-processing-engineer

3. 마크다운 미리보기로 확인
   Ctrl+Shift+V  — 미리보기 탭 열기
   Ctrl+K V      — 편집기 옆에 미리보기 분할
```

> GitHub 웹에서도 `.md` 파일을 클릭하면 바로 렌더링된 노트를 볼 수 있습니다.

---

## 학습 내용

| 과목 | 챕터 | 주요 학습 내용 |
|------|------|---------------|
| `1_Software Design` | 요구사항 확인 | 소프트웨어 생명 주기(폭포수·프로토타입·나선형·애자일), 요구사항 분석 기법 |
| `1_Software Design` | 화면 설계 | UI 표준, 프로토타이핑, 사용성 평가 |
| `1_Software Design` | 애플리케이션 설계 | 아키텍처 패턴, 모듈화, 디자인 패턴(GoF) |
| `1_Software Design` | 인터페이스 설계 | 내·외부 인터페이스 정의, 시스템 연계 기술 |
| `2_Software Development` | 데이터 입출력 구현 | 자료구조(스택·큐·트리·그래프), 정렬·검색 알고리즘 |
| `2_Software Development` | 통합 구현 | 모듈 통합 전략, CI/CD 개념, 빌드 도구 |
| `2_Software Development` | 제품 소프트웨어 패키징 | 릴리즈 노트, 형상 관리(Git), 버전 관리 전략 |
| `2_Software Development` | 애플리케이션 테스트 관리 | 확인·검증, 파레토 법칙, 결함 집중, 화이트박스·블랙박스 기법 |
| `2_Software Development` | 인터페이스 구현 | REST API, JSON/XML, AJAX 처리 |
| `3_Database Development` | 논리 데이터베이스 설계 | ER 모델, 관계형 모델, 정규화(1NF~BCNF), 반정규화 |
| `3_Database Development` | 물리 데이터베이스 설계 | 인덱스(B-Tree·Hash), 파티셔닝, 클러스터링 |
| `3_Database Development` | SQL 응용 (기초) | DDL(CREATE·ALTER·DROP), DML(SELECT·INSERT·UPDATE·DELETE), DCL(GRANT·REVOKE) |
| `3_Database Development` | SQL 응용 (심화) | 집계함수, GROUP BY·HAVING, 서브쿼리, JOIN, 윈도우 함수 |
| `3_Database Development` | 데이터 전환 | ETL 개념, 데이터 마이그레이션, 검증 방법 |
| `4_Utilization of Programming Languages` | 서버 프로그램 구현 | 서버 개발 패턴, 배치 프로그램 |
| `4_Utilization of Programming Languages` | 프로그래밍 언어 활용 | Java·C·Python 자료형·변수·흐름제어·OOP |
| `4_Utilization of Programming Languages` | 응용 SW 기초 기술 활용 | 운영체제(처리능력·반환시간·가용성·신뢰도), TCP/IP·OSI 7계층 |
| `5_IS Development and Management` | 소프트웨어 개발 방법론 활용 | 애자일, CMMI, SPICE, 개발 표준 |
| `5_IS Development and Management` | IT 프로젝트 정보 시스템 구축 관리 | IT 거버넌스, 비용 산정(FP·COCOMO), 아웃소싱 |
| `5_IS Development and Management` | 소프트웨어 개발 보안 구축 | Secure SDLC, Seven Touchpoints, 보안 3요소(기밀성·무결성·가용성) |
| `5_IS Development and Management` | 시스템 보안 구축 | 접근 제어, 대칭·비대칭 암호화, 방화벽·IDS·IPS |

---

## 학습 환경

- **GitHub** — 저장소 온라인 열람 (별도 설치 불필요)
- **VS Code** — 마크다운 미리보기 내장 지원 (`Ctrl+Shift+V`)
- **Obsidian** — 양방향 링크 기반 노트 관리에 최적화
