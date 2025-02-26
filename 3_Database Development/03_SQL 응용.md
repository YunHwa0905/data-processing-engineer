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

### 삭제문(DELETE FROM~)
- 정의
  - 기본 테이블에 있는 튜플들 중에서 특정 튜플(행)을 삭제할 때 사용
- 일반 형식
```
DELETE
FORM 테이블명
[WHRER 조건];
```
- 특징
  - 모든 레코드를 삭제할 때는 WHERE절을 생략
  - 모든 레코드를 삭제하더라도 테이블 구조는 남아 있기 때문에 디스크에서 테이블을 완전히 제거하는 DROP과는 다름

### 갱신문(UPDATE~ SET~)
- 정의
  - 기본 테이블에 있는 튜플들 중에서 특정 튜플의 내용을 변경할 때 사용
- 일반 형식
```
UPDATE 테이블명
SET 속성명 = 데이터[,속성면=데이터,...]
[WHERE 조건];
```





## :mag: 083 DML - SELECT-1
### 일반 형식 및 기본 검색
```
SELECT [PREDICATE] [테이블명,]속성명1, [테입르명,]속성명2,...
FROM 테이블명[,테이블명,...
```
- 특징
  - SELECT절
    - PREDICATE
      - 불러올 튜플 수를 제한할 명령어를 기술함
        - DISTINCT
          - 중복된 튜플이 있으면 그 중 텃 번째 한 개만 검색함
    - 속성명
      - 검색하여 불러올 속성(열) 및 수식들을 지정함
  - FROM절
    - 질의에 의해 검색될 데이터들을 포함하는 테이블명을 기술함

### 조건 연산자
- 논리 연산자
  - NOT, AND, OR
- LIKE 연산자
  - 대표 문자를 이요해 지정된 속성의 값이 문자 패턴과 일치하는 튜플을 검색하기 위해 사용됨
    - `*` 또는 %
      - 모든 문자를 대표함
    - _
      - 문자 하나를 대표함
    - #
      - 숫자 하나를 대표함

### 조건 지정 검색
```
SELECT [테이블명.]속성명1, [테이블명.]속성명2,...
FORM 테이블명[,테이블명,...]
[WHERE 조건];
```
- 특징
  - WHERE 절에 조건을 지정하여 조건에 만족하는 튜플만 검색
  - NULL 값의 사용
    - 주소가 NULL인, 즉 주소가 입력되지 않은 자료만 검색함
      - ex) WHERE 주소 IS NULL
    - 주소가 NULL이 아닌, 즉 주소가 입력된 자료만 검색함
      - ex) WHERE 주소 IS NOT NULL
  - BETWEEN 연산자의 사용
    - 생일이 '01/09/69'에서 '10/22/73' 사이인 자료만 검색함
      - ex) WHERE 생일 BETWEEN #01/09/69# AND #10/22/73#

### 정렬 검색
- 정의
  - ORDER BY 절에 특정 속성을 지정하여 지정된 속성으로 자료를 정렬하여 검색
```
SELECT [테이블명.]속성명1, [테이블명.]속성명2,...
FROM 테이블명[,테이블명,...]
[WHERE 조건]
[ORDER BY 속성명 [ASC | DESC]];
```
- 특징
  - 속성명
    - 정렬의 기준이 되는 속성명을 기술함
  - [ASC|DESC]
    - 정렬 방식으로 'ASC'는 오름차순, 'DESC'는 내림차순이며, 생략하면 오름차순으로 지정됨

### 하위 질의
- 정의
  - 조건절에 주어진 질의를 먼저 수행하여 그 검색 결과를 조건절의 피연산자로 사용





## :mag: 084 DML - SELECT-2
### 그룹 지정
- 정의
  - 특정 속성을 기준으로 그룹화하여 검색할 때 그룹화할 속성을 지정
```
SELECT [테이블명.]속성명, [테이블명.]속성명,...
FROM 테이블명[,테이블명,...]
[WHERE 조건]
[GROUP BY 속성명, 속성명, ...]
[HAVING 조건];
```
- 특징
  - GROUP BY절
    - 특정 속성을 기준으로 그룹화하여 검색할 때 사용함
    - 일반적으로 GROUP BY절은 그룹 함수와 함께 사용됨
  - HAVING절
    - GROUP BY와 함께 사용되며, 그룹에 대한 조건을 지정함

### 그룹 함수
- COUNT(속성명)
  - 그룹별 튜플 수를 구하는 함수
- SUM(속성명)
  - 그룹별 합계를 구하는 함수
- AVG(속성명)
  - 그룹별 평균을 구하는 함수
- MAX(속성명)
  - 그룹별 최대값을 구하는 함수
- MIN(속성명)
  - 그룹별 최소값을 구하는 함수

### 집합 연산자를 이용한 통합 질의
|집합 연산자|설명|집합 종류|
|---------|---|--------|
|UNION|* 두 SELECT문의 조회 결과를 통합하여 모두 출력함<br>* 중복된 행은 한 번만 출력함|합집합|
|UNION ALL|* 두 SELECT문의 조회 결과를 통합하여 모두 출력함<br>* 중복된 행도 그대로 출력함|합집합|
|INTERSECT|* 두 SELECT문의 조회 결과 중 공통된 행만 출력함|교집합|
|EXCEPT|* 첫번째 SELECT문의 조회 결과에서 두 번째 SELECT문의 조회 결과를 제외한 행을 출력함|차집합|





## :mag: 085 DML - JOIN
### INNER JOIN
```
SELECT [테이블명1,]속성명, [테이블명2]속성명, ...
FROM 테이블명1, 테이블명2, ...
WHERE 테이블명1.속성명 = 테이블명2.속성명
```