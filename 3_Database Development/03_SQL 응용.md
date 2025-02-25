# SQL 응용
## :mag: 079 SQL의 개념
### DDL(Data Define Language, 데이터 정의어)
- 정의
  - SCHEMA, DOMAIN, TABLE, VIEW, INDEX를 정의하거나 변경 또는 삭제할 때 사용하는 언너
- 3가지 유형

|명령어| 기능|
|-----|----|
|CREATE| SCHEMA, DOMAIN, TABLE, VIEW, INDEX를 정의함|
|ALTER| TABLE에 대한 정의를 변경하는 데 사용함|
|DROP| SCHEMA, DOMAIN, TABLE, VIEW, INDEX를 삭제함|

### DML(Data Mainpulation Language, 데이터 조작어)
- 정의
  - 데이터베이스 사용자가 응용 프로그램이나 질의어를 통하여 저장된 데이터를 실질적으로 처리하는 데 사용되는 언어
- 4가지 유형

|명령어|기능|
|---|----|
|SELECT| 테이블에서 조건에 맞는 튜플을 검색함|
|INSERT| 테이블에서 새로운 튜플을 삽입함|
|DELETE| 테이블에서 조건에 맞는 튜플을 삭제함|
|UPDATE| 테이블에서 조건에 맞는 튜플의 내용을 변경함|

### DCL(Data Control Language, 데이터 제어어)
- 정의
  - 데이터의 보안, 무결성, 회복, 병행 수행 제어 등을 정의하는 데 사용되는 언어
- 종류

|명령어|기능|
|----|----|
|COMMIT| 명령에 의해 수행된 결과를 실제 물리적 디스크로 저장하고, 데이터베이스 조작 작업이 정상적으로 완료되었음을 관리자에게 알려줌|
|ROLLBACK| 데이터베이스 사용자에게 사용 권한을 부여함|
|GRANT| 데이터베이스 사용자에게 사용 권한을 부여함|
|REVOKE| 데이터베이스 사용자의 사용 권한을 취소함|





## :mag: 080 DDL
### CREATE TABLE
- 정의
  - 테이블을 정의하는 명령문
- 표기 형식
```
CREATE TABLE 테이블명
    (속성명 데이터_타입 [DEFAULT 기본값][NOT NULL],...
    [, PRIMARY KEY(기본키_속성명),...)]
    [, UNIQUE(대체키_속성명,...)]
    [, FOREIGN KEY(외래키_속성명,...)]
        [REFERENCES 참조테이블(기본키_속성명,...)]
        [ON DELETE 옵션]
        [ON UPDATE 옵션]
    [, CONSTRAINT 제약조건명][CHECK (조건식)];
```
- 특징
  - 기본 테이블에 포함될 모든 속성에 대하여 속성명과 그 속성의 데이터 타입, 기본값, NOT NULL 여부를 지정함
  - PRIMARY KEY
    - 기본키로 사용할 속성 또는 속성의 잡합을 지정
  - CHECK
    - 속성 값에 대한 제약 조건을 정의

### ALTER TABLE
- 정의
  - 테이블에 대한 정의를 변경하는 명령문
- 표기 형식
```
ALTER TABLE 테이블명 ADD 속성명 데이터_타입[DEFAULT '기본값'];
ALTER TABLE 테이블명 ALTER 속성명 [SET DEFAULT '기본값'];
ALTER TABLE 테이블명 DROP COLUMN 속성명 [CASCADE];
```
- 특징
  - ADD
    - 새로운 속성(열)을 추가할 떄 사용함
  - ALTER
    - 특정 속성의 Default 값을 변경할 때 사용함
  - DROP COLUMN
    - 특정 속성을 삭제할 때 사용함

### DROP
- 정의
  - 스키마, 도메인, 기본 테이블, 뷰 테이블, 인덱스, 제약 조건 등을 제거하는 명령문
- 표기 형식
```
DROP SCHEMA 스키마명 [CASECADE | RESTRICT];
DROP DOMAIN 도메인명 [CASECADE | RESTRICT];
DROP TABLE 테이블명 [CASECADE | RESTRICT];
DROP VIEW 뷰명 [CASECADE | RESTRICT];
DROP INDEX 인덱스명 [CASECADE | RESTRICT];
DROP CONSTRAINT 제약조건명;
```
- 특징
  - CASCADE
    - 제거할 요소를 참조하는 다른 모든 개체를 함께 제거함, 즉 주 테이블의 데이터 제거 시 각 외래키와 관계를 맺고 있는 모든 데이터를 제거하는 참조 무경성 제약 조건을 설정하기 위해 사용됨
  - RESTRICT
    - 다른 개체가 제거할 요소를 참조중일 때는 제거를 취소함





## :mag: 081 DCL
### GRANT / REVOKE
- GRANT
  - 권한 부여를 위한 명령어
- REVOKE
  - 원한 취소를 위한 명령어
- 테이블 및 속성에 대한 권한 부여 및 취소
```
GRANT 권한_리스트 ON 개체 TO 사용자 [WITH GRANT OPTION];
REVOKE [GRANT OPTIN FOR] 권한_리스트 ON 개체 FROM 사용자 [CASCADE];
```

### ROLLBACK
- 정의
  - 아직 COMMIT 되지 않은 변경된 모든 내용들을 취소하고 데이터베이스를 이전 상태로 되돌리는 명령어





## :mag: 082 DML
### 삽입문(INSERT INTO ~)
- 정의
  - 기본 테이블에 새로운 튜플을 삽입할 때 사용
- 일반 형식
```
INSERT INTO 테이블명([속성명1, 속성명2,...])
VALUES (데이터1, 데이터2,...);
```
- 특징
  - 대응하는 속성과 데이터는 개수와 데이터 유형이 일치해야 함
  - 기본 테이블의 모든 속성을 사용할 때는 속성명을 생략할 수 있음
  - SELECT문을 사용하여 다른 테이블의검색 결과를 삽입할 수 있음