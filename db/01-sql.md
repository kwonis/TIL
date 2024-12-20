
<!-- TOC start (generated with https://github.com/derlin/bitdowntoc) -->

- [Database](#database)
- [Relational Database](#relational-database)
  - [RDBMS](#rdbms)
- [SQL](#sql)
  - [SQL Statements](#sql-statements)
- [Single Table Queries](#single-table-queries)
  - [Querying data](#querying-data)
  - [Sorting data](#sorting-data)
    - [ORDER BY](#order-by)
  - [Filtering data](#filtering-data)
    - [DISTINCT](#distinct)
    - [WHERE](#where)
    - [Operator](#operator)
    - [LIMIT](#limit)
  - [Grouping data](#grouping-data)
    - [GROUP BY](#group-by)
- [Managing Tables (DDL)](#managing-tables-ddl)
  - [Create a table](#create-a-table)
  - [Modifying table fields](#modifying-table-fields)
  - [Delete a table](#delete-a-table)
  - [참고](#참고)
- [Modifying Data](#modifying-data)
  - [Insert data](#insert-data)
  - [Update data](#update-data)
  - [Delete data](#delete-data)
  - [참고](#참고-1)
- [Multi table queries](#multi-table-queries)
  - [Join](#join)
  - [Joining tables](#joining-tables)

<!-- TOC end -->
# Database
- 📌 데이터 베이스
  - 체계적인 데이터 모음
- 📌 데이터
  - 저장이나 처리에 효율적인 형태로 변환된 정보
- 증가하는 데이터 사용량
  - 배달의 민족 국내 주문 건수 6억 8천만 건(2020)
  - 구독자 2억 3840만명이 1000억 시간 넷플릭스 시청(2023 1~6월)
  - 전세계 모든 데이터의 약 90%는 2015년 이후 생산된 것(IBM)
- 데이터 센터의 성장
  - 네이버 : 제2데이터센터에 6500억 투자(2020)
  - 카카오 : 제1데이터센터와 제2데이터센터에 1.5조 투자(2022)
  - 전 세계 데이터 센터 시장 2022년부터 2026년까지 연평균 20% 이상 성장 예상
  - 참고 자료 : https://www.tmcnet.com/usubmit/-data-center-market-size-grow-usd-61596-bn-/2022/11/09/9709624.htm  <img src="images/Technavio_Global_Data_Center_Market_2022_2026.jpg" width=500 style='margin:1rem'>

💡
> 데이터를 저장하고 잘 관리하여 활용할 수 있는 기술이 중요해짐
> 우리가 알고 있는 데이터 저장 방식은 어떤 것이 있을까?


- 📌 기존 데이터 저장 방식
  1. 파일(File) 이용
  2. 스프레드 시트(Spreadsheet) 이용

1. 파일을 이용한 데이터 관리
   - 어디에서나 쉽게 사용 가능
   - 데이터를 구조적으로 관리하기 어려움  
      <img src="images/file.png" width=100 style='margin:1rem'>
2. 스프레드 시트를 이용한 데이터 관리
   - 테이블의 열과 행을 사용해 데이터를 구조적으로 관리 가능   
      <img src="images/spreadsheet.png" width=300 style='margin:1rem'>
   - 스프레드 시트의 한계
     - 크기 : 일반적으로 약 100만 행까지만 저장 가능
     - 보안 : 단순히 파일이나 링크 소유 여부에 따른 단순한 접근 권한 기능 제공
     - 정확성
       - 만약 공싱적으로 "강원"의 지명이 "강언"으로 바뀌었다고 가정
       - 이 변경으로 인해 테이블 모든 위치에서 해당 값을 업데이트 해야 함
       - 찾기 및 바꾸기 기능을 사용해 바꿀 수 있지만 만약 데이터가 여러 시트에 분산되어 있다면 변경에 누락이 생기거나 추가 문제가 발생할 수 있음

- 📌 데이터베이스 역할
  - 데이터를 저장하고 조작 CRUD

# Relational Database
- 📌 데이터베이스 역할
  - 데이터를 저장(구조적 저장)하고 조작 CRUD
- 📌 관계형 데이터베이스
  - 데이터 간에 관계가 있는 데이터 항목들의 모음
  - 테이블, 행, 열의 정보를 구조화하는 방식  
      <img src="images/rdbms01.png" width=500 style='margin:1rem'>
  - `서로 관련된 데이터 포인터를 저장`하고 이에 대한 `액세스`를 제공  
      <img src="images/rdbms02.png" width=500 style='margin:1rem'>
- 관계 : 여러 테이블 간의 (논리적) 연결
  - 관계로 할 수 있는 것
    - 이 관계로 인해 두 테이블을 사용하여 데이터를 다양한 형식으로 조회할 수 있음
    - 특정 날짜에 구매한 모든 고객 조회
    - 지난 달에 배송일이 지연된 고객 조회
- 관계형 데이터베이스 예시
  - step 1
    - 다음과 같이 고객 데이터가 테이블에 저장되어 있다고 가정
    - 고객 데이터 간 비교를 위해서는 어떤 값을 활용해야 할까?
      - 이름? 주소? 만약 동명이인이나 같은 주소지가 있다면?  
        <img src="images/rdbms03.png" width=200 style='margin:1rem'>
    - 각 데이터에 고유한 식별 값을 부여하기(📌 기본 키, Primary Key)  
        <img src="images/rdbms04.png" width=200 style='margin:1rem'>
  - step 2
    - 다음과 같이 각 고객이 주문한 주문데이터가 테이블에 저장되어 있다고 가정
    - 누가 어떤 주문을 했는지 어떻게 식별할 수 있을까?  
        <img src="images/rdbms05.png" width=500 style='margin:1rem'>
    - 주문 정보에 고객의 고유한 식별 값을 저장하기(📌 외래 키, Foreign Key)  
        <img src="images/rdbms06.png" width=500 style='margin:1rem'>

- 관계형 데이터베이스 관련 용어
  - Table (aka Relation)
    - 데이터를 기록하는 곳  
        <img src="images/rdbms-word-01.png" width=300 style='margin:1rem'>
  - Field (aka Column, Attribute)
    - 각 필드에는 고유한 데이터 형식(타입)이 지정됨  
        <img src="images/rdbms-word-02.png" width=300 style='margin:1rem'>
  - Record (aka Row, Tuple)
    - 각 레코드에는 구체적인 데이터 값이 저장됨  
        <img src="images/rdbms-word-03.png" width=300 style='margin:1rem'>
  - Database (aka Schema)
    - 테이블의 집합  
        <img src="images/rdbms-word-04.png" width=300 style='margin:1rem'>
  - Primary Key (기본 키, PK)
    - 각 레코드의 고유한 값
    - 관계형 데이터베이스에서 `레코드의 식별자`로 활용  
        <img src="images/rdbms-word-05.png" width=500 style='margin:1rem'>
  - Foreign Key (외래 키, FK)
    - 테이블의 필드 중 다른 테이블의 레코드를 식별할 수 있는 키
    - 다른 테이블의 기본 키를 참조
    - 각 레코드에서 `서로 다른 테이블 간의 관계를 만드는 데` 사용  
        <img src="images/rdbms-word-06.png" width=500 style='margin:1rem'>


## RDBMS
- 📌 DBMS; Database Management System
  - 데이터베이스를 관리하는 소프트웨어 프로그램
  - 데이터 저장 및 관리를 용이하게 하는 시스템
  - 데이터베이스와 사용자 간의 인터페이스 역할
  - 사용자가 데이터 구성, 업데이트, 모니터링, 백업, 복구 등을 할 수 있도록 도움
- 📌 RDBMS; Relational Database Management System
  - 관계형 데이터베이스를 관리하는 소프트웨어 프로그램
  - RDBMS 서비스 종류
    - SQLite, MySQL, PostgreSQL, Oracle Database ...
  - SQLite
    - 경량의 오픈 소스 데이터베이스 관리 시스템
    - 컴퓨터나 모바일 기기에 내장되어 간단하고 효율적인 데이터 저장 및 관리를 제공

💡 데이터 베이스 정리
- Table은 데이터가 기록되는 곳
- Table에는
  - 행에서 고유하게 식별 가능한 `기본 키`라는 속성이 있으며,
  - `외래 키`를 사용하여 각 행에서 서로 다른 테이블 간의 관계를 만들 수 있음
- 데이터는 기본 키 또는 외래 키를 통해 결합(join)될 수 있는 여러 테이블에 걸쳐 구조화 됨

# SQL
- Structure Query Language
  - 데이터베이스에 정보를 저장하고 처리하기 위한 프로그래밍 언어
  - 테이블의 형태로 구조화(`Structure`)된 관계형 데이터베이스에게 요청을 질의(요청)(`Query`)
- 관계형 데이터베이스와의 대화를 위해 사용하는 프로그래밍 언어    
   <img src="images/sql.png" width=350 style='margin:1rem'>
- SQL syntax  
   <img src="images/sql-syntax.png" width=350 style='margin:1rem'>
  1. SQL 키워드는 대소문자를 구분하지 않음
     - 하지만 대문자로 작성하는 것을 권장(명시적 구분)  
  2. 각 SQL statements의 끝에는 세미콜론(';')이 필요
     - 세미콜론은 각 SQL statements를 구분하는 방법(명령어의 마침표)

💡 요약  
<img src="images/sql-summary.png" width=350 style='margin:1rem'>

## SQL Statements
- SQL statements
  - SQL을 구성하는 가장 기본적인 코드 블록
  - 예시   
     <img src="images/sql-syntax.png" width=350 style='margin:1rem'>
    - 해당 예시 코드는 SELECT Statement라 부름
    - 이 Statement는 SELECT, FROM 2개의 keyword로 구성 됨
- 수행 목적에 따른 SQL Statement 4가지 유형
  1. DDL - 데이터 정의 
  2. DQL - 데이터 검색
  3. DML - 데이터 조작 
  4. DCL - 데이터 제어 

|유형|역할|SQL 키워드|
|:----:|:----:|:----:|
|DDL<br>(Data Definition Language)|데이터의 기본 구조 및 형식 변경|CREATE <br> DROP <br> ALTER|
|DQL<br>(Data Query Language)|데이터 검색|SELECT|
|DML<br>(Data Manipulation Language)|데이터 조작<br>(추가, 수정, 삭제)|INSERT <br> UPDATE <br> DELETE|
|DCL <br> (Data Control Language)|데이터 및 작업에 대한 사용자 권한 제어|COMMIT <br> ROLLBACK <br> GRANT <br> REVOKE|

- SQL 학습
  - 단순히 SQL 문법을 암기하고 상황에 따라 실행만 하는 것이 아닌 SQL을 통해 관계형 데이터베이스를 잘 이해하고 다루는 방법을 학습
- 참고
  - Query
    - "데이터베이스로부터 정보를 요청" 하는 것
    - 일반적으로 SQL로 작성하는 코드를 쿼리문(SQL문)이라 함
  - SQL 표준
    - SQL은 미국 국립 표준 협회(ANSI)와 국제 표준화 기구(ISO)에 의해 표준이 채택됨
    - 모든 RDBMS에서 SQL 표준을 지원
    - 다만, 각 RDBMS마다 독자적인 기능에 따라 표준을 벗어나는 문법이 존재하니 주의


# Single Table Queries
## Querying data
- SELECT statement
  - 테이블에서 데이터를 조회
- SELECT syntax  
     <img src="images/select.png" width=400 style='margin:1rem'>
  - SELECT 키워드 이후 데이터를 선택하려는 필드를 하나 이상 지정
  - FROM 키워드 이후 데이터를 선택하려는 테이블의 이름을 지정
- SELECT 활용
  - 테이블 employees에서 LastName 필드의 모든 데이터를 조회   
     <img src="images/select03.png" width=300 style='margin:1rem'>
     <img src="images/select02.png" width=100 style='margin:1rem'>
  - 테이블 employees에서 LastName, FirstName 필드의 모든 데이터를 조회  
     <img src="images/select05.png" width=300 style='margin:1rem'>
     <img src="images/select04.png" width=150 style='margin:1rem'>
  - 테이블 employees에서 모든 필드 데이터를 조회   
     <img src="images/select07.png" width=300 style='margin:1rem'>
     <img src="images/select06.png" width=600 style='margin:1rem'>
  - 테이블 employees에서 FirstName 필드의 모든 데이터를 조회
    - 단, 조회 시 FirstName이 아닌 '이름'으로 출력 될 수 있도록 변경    
     <img src="images/select09.png" width=300 style='margin:1rem'>
     <img src="images/select08.png" width=100 style='margin:1rem'>
  - 테이블 tracks에서 Name, Milliseconds 필드의 모든 데이터 조회
    - 단, Milliseconds 필드는 60000으로 나눠 분 단위 값으로 출력  
     <img src="images/select11.png" width=300 style='margin:1rem'>
     <img src="images/select10.png" width=400 style='margin:1rem'>

- SELECT 정리 
  - 테이블의 데이터를 조회 및 반환
  - `*` (asterisk)를 사용하여 모든 필드 선택

## Sorting data
### ORDER BY
- ORDER BY statement
  - 조회 결과의 레코드를 정렬
  - ORDER BY syntax
    - FROM clause 뒤에 위치
    - 하나 이상의 컬럼을 기준으로 결과를 오름차순(ASC, 기본값), 내림차순(DESC)으로 정렬  
       <img src="images/order-by-01.png" width=300 style='margin:1rem'>
- ORDER BY 활용
  - 테이블 employees에서 FirstName 필드의 모든 데이터를 오름차순으로 조회  
       <img src="images/order-by-03.png" width=300 style='margin:1rem'>
       <img src="images/order-by-02.png" width=150 style='margin:1rem'>
  - 테이블 employees에서 FirstName 필드의 모든 데이터를 내림차순으로 조회  
       <img src="images/order-by-05.png" width=400 style='margin:1rem'>
       <img src="images/order-by-04.png" width=150 style='margin:1rem'>
  - 테이블 customers에서 Country 필드를 기준으로 내림차순 정렬한 다음 City 필드 기준으로 오름차순 정렬하여 조회  
       <img src="images/order-by-07.png" width=400 style='margin:1rem'>
       <img src="images/order-by-06.png" width=250 style='margin:1rem'>
  - 테이블 tracks에서 Millieseconds 필드를 기준으로 내림차순 정렬한 다음 Name, Milliseconds 필드의 모든 데이터를 조회
    - 단, Milliseconds 필드는 60,000으로 나눠 분 단위 값으로 출력  
       <img src="images/order-by-09.png" width=400 style='margin:1rem'>
       <img src="images/order-by-08.png" width=300 style='margin:1rem'>
- 정렬에서의 NULL
  - NULL 값이 존재할 경우 오름차순 정렬 시 결과에 NULL이 먼저 출력  
       <img src="images/order-by-10.png" width=500 style='margin:1rem'>
- 💡 SELECT statement 실행 순서
  - FROM ➡️ SELECT ➡️ ORDER BY
    - 테이블에서 FROM
    - 조회하여 SELECT
    - 정렬 ORDER BY


## Filtering data
- 📌 Filtering data 관련 Keywords
  - Clause
    - DISTINCT
    - WHERE
    - LIMIT
  - Operator
    - BETWEEN
    - IN
    - LIKE
    - Comparison
    - Logical

### DISTINCT
- DISTINCT statement    
  - 조회 결과에서 중복된 레코드를 제거  
     <img src="images/distinct-01.png" width=500 style='margin:1rem'>
  - SELECT 키워드 바로 뒤에 작성해야 함
  - SELECT DISTINCT 키워드 다음에 고유한 값을 선택하려는 하나 이상의 필드를 지정
- 활용
  - 테이블 customers에서 Country 필드의 모든 데이터를 오름차순 조회  
    <img src="images/distinct-03.png" width=400 style='margin:1rem'>
    <img src="images/distinct-02.png" width=150 style='margin:1rem'>
  - 테이블 customers에서 Country 필드의 모든 데이터를 중복없이 오름차순 조회  
    <img src="images/distinct-05.png" width=400 style='margin:1rem'>
    <img src="images/distinct-04.png" width=150 style='margin:1rem'>

### WHERE
- WHERE statement
  - 조회 시 특정 검색 조건을 지정  
    <img src="images/where.png" width=500 style='margin:1rem'>  
  - FROM clause 뒤에 위치
  - search_condition은 비교연산자 및 논리연산자(AND, OR, NOT 등)를 사용하는 구문이 사용됨
- 활용
  - 테이블 customers에서 City 필드 값이 'Prague'인 데이터의 LastName, FirstName, City 조회  
    <img src="images/where03.png" width=500 style='margin:1rem'>
    <img src="images/where02.png" width=300 style='margin:1rem'>
  - 테이블 customers에서 City 필드 값이 'Prague'가 아닌 데이터의 LastName, FirstName, City 조회  
    <img src="images/where05.png" width=500 style='margin:1rem'>
    <img src="images/where04.png" width=300 style='margin:1rem'>
  - 테이블 customers에서 Company 필드 값이 NULL이고 Country 필드 값이 'USA'인 데이터의 LastName, FirstName, Company, Country 조회  
    <img src="images/where07.png" width=500 style='margin:1rem'>
    <img src="images/where06.png" width=300 style='margin:1rem'>
  - 테이블 customers에서 Company 필드 값이 NULL이거나 Country 필드 값이 'USA'인 데이터의 LastName, FirstName, Company, Country 조회  
    <img src="images/where09.png" width=500 style='margin:1rem'>
    <img src="images/where08.png" width=300 style='margin:1rem'>
  - 테이블 tracks에서 Bytes 필드 값이 10,000 이상 500,000 이하인 데이터의 Name, Bytes 조회  
    <img src="images/where11.png" width=500 style='margin:1rem'>
    <img src="images/where10.png" width=250 style='margin:1rem'>
  - 테이블 tracks에서 Bytes 필드 값이 10,000 이상 500,000 이하인 데이터의 Name, Bytes를 Bytes 기준으로 오름차순 조회  
    <img src="images/where13.png" width=500 style='margin:1rem'>
    <img src="images/where12.png" width=250 style='margin:1rem'>
  - 테이블 customers에서 Country 필드 값이 'Canada' 또는 'Germany' 또는 'France'인 데이터의 LastName, FirstName, Country 조회  
    <img src="images/where15.png" width=500 style='margin:1rem'>
    <img src="images/where14.png" width=300 style='margin:1rem'>
  - 테이블 customers에서 Country 필드 값이 'Canada' 또는 'Germany' 또는 'France'가 아닌 데이터의 LastName, FirstName, Country 조회  
    <img src="images/where17.png" width=500 style='margin:1rem'>
    <img src="images/where16.png" width=250 style='margin:1rem'>
  - 테이블 customers에서 LastName 필드 값이 'son'으로 끝나는 데이터의 LastName, FirstName 조회  
    <img src="images/where19.png" width=500 style='margin:1rem'>
    <img src="images/where18.png" width=200 style='margin:1rem'>
  - 테이블 customers에서 FirstName 필드 값이 4자리면서 'a'로 끝나는 데이터의 LastName, FirstName 조회  
    <img src="images/where21.png" width=500 style='margin:1rem'>
    <img src="images/where20.png" width=200 style='margin:1rem'>

### Operator
- 📌 Comparison Operators 비교 연산자
  - =, >=, <=, !=, IS, LIKE, IN, BETWEEN, ..., AND
- 📌 Logical Operators 논리 연산자
  - AND(&&), OR(||), NOT(!)

- IN Operator : 값이 특정 목록 안에 있는지 확인
- LIKE Operator : 값이 특정 패턴에 일치하는지 확인(Wildcards와 함께 사용) 
  - Wildcard Characters
    - `%` : 0개 이상의 문자열과 일치 하는지 확인
    - `_` : 단일 문자와 일치하는지 확인

### LIMIT
- LIMIT clause : 조회하는 레코드 수를 제한  
   <img src="images/limit.png" width=500 style='margin:1rem'>
  - 하나 또는 두 개의 인자를 사용(0 또는 양의 정수)
  - row_count는 조회하는 최대 레코드 수를 지정
- LIMIT & OFFSET 예시  
  <img src="images/limit02.png" width=500 style='margin:1rem'>
- 활용
  - 테이블 tracks에서 TrackId, Name, Bytes 필드 데이터를 Bytes 기준 내림차순으로 7개만 조회  
    <img src="images/limit04.png" width=500 style='margin:1rem'>
    <img src="images/limit03.png" width=400 style='margin:1rem'>
  - 테이블 tracks에서 TrackId, Name, Bytes 필드 데이터를 Bytes 기준 내림차순으로 4번째 부터 7번째 데이터만 조회  
    <img src="images/limit06.png" width=500 style='margin:1rem'>
    <img src="images/limit05.png" width=400 style='margin:1rem'>

## Grouping data

### GROUP BY
- 📌 GROUP BY clause
  - 레코드를 그룹화하여 요약본 생성('집계 함수'와 함께 사용)
- 📌 Aggregation Functions 집계 함수
  - 값에 대한 계산을 수행하고 단일한 값을 반환하는 함수
  - SUM, AVG, MAX, MIN, COUNT
- GROUP BY syntax  
   <img src="images/group-by.png" width=500 style='margin:1rem'>
  - FROM 및 WHERE 절 뒤에 배치
  - GROUP BY 절 뒤에 그룹화 할 필드 목록을 작성
- 예시
  1. Country 필드를 그룹화  
      <img src="images/group-by02.png" width=300 style='margin:1rem'>
      <img src="images/group-by03.png" width=150 style='margin:1rem'>
  2. COUNT 함수가 각 그룹에 대한 집계된 값을 계산  
      <img src="images/group-by04.png" width=300 style='margin:1rem'>
      <img src="images/group-by05.png" width=150 style='margin:1rem'>
- 활용
  - 테이블 tracks에서 Composer 필드를 그룹화하여 각 그룹에 대한 Bytes의 평균 값을 내림차순 조회  
    <img src="images/group-by06.png" width=500 style='margin:1rem'>  
    <img src="images/group-by07.png" width=400 style='margin:1rem'>  
    <img src="images/group-by08.png" width=400 style='margin:1rem'>
  - 테이블 tracks에서 Composer 필드를 그룹화하여 각 그룹에 대한 Milliseconds의 평균 값이 10 미만인 데이터 조회
    - 단, Milliseconds 필드는 60,000으로 나눠 분 단위 값의 평균으로 계산  
      <img src="images/group-by09.png" width=500 style='margin:1rem'>
      <img src="images/group-by10.png" width=450 style='margin:1rem'>
    - HAVING clause  
        <img src="images/group-by11.png" width=500 style='margin:1rem'>
      - 집계 항목에 대한 세부 조건을 지정
      - 주로 GROUP BY와 함께 사용되며 GROUP BY가 없다면 WHERE 처럼 동작

💡 SELECT statement 실행순서    
<img src="images/group-by11.png" width=500 style='margin:1rem'>
  
1. 테이블에서 (FROM)
2. 특정 조건에 맞추어 (WHERE)
3. 그룹화 하고 (GROUP BY)
4. 만약 그룹 중에서 조건이 있다면 맞추고 (HAVING)
5. 조회하여 (SELECT)
6. 정렬하고 (ORDER BY)
7. 특정 위치의 값을 가져옴 (LIMIT)

# Managing Tables (DDL)
## Create a table
- 📌 CREATE TABLE statement : 테이블 생성  
    <img src="images/create.png" width=500 style='margin:1rem'>
  - 각 필드에 적용할 데이터 타입 작성
  - 테이블 및 필드에 대한 제약조건(constraints) 작성
- 활용
  - examples 테이블 생성 및 확인  
      <img src="images/create02.png" width=500 style='margin:1rem'>
- PRAGMA
  - 테이블 schema(구조) 확인  
     <img src="images/create03.png" width=500 style='margin:1rem'>
  - 'cid'
    - Column ID를 의미하며 각 컬럼의 고유한 식별자를 나타내는 정수 값
    - 직접 사용하지 않으며 PRAGMA 명령과 같은 메타데이터 조회에서 출력 값으로 활용됨
- 데이터 타입  
      <img src="images/create04.png" width=400 style='margin:1rem'>
  - SQLite 데이터 타입
    1. NULL : 아무런 값도 포함하지 않음을 나타냄
    2. INTEGER : 정수
    3. REAL : 부동 소수점
    4. TEXT : 문자열
    5. BLOB  : 이미지, 동영상, 문서 등의 바이너리 데이터
- 제약조건  
      <img src="images/create05.png" width=400 style='margin:1rem'>
  - 테이블의 필드에 적용되는 규칙 또는 제한 사항
  - 데이터의 무결성을 유지하고 데이터베이스의 일관성을 보장
  - 대표 제약 조건 3가지
    1. PRIMARY KEY 
       - 해당 필드를 기본 키로 지정
       - INTEGER 타입에만 적용되며 INT, BIGINT 등과 같은 다른 정수 유형은 적용되지 않음 
    2. NOT NULL
       - 해당 필드에 NULL 값을 허용하지 않도록 지정 
    3. FOREIGN KEY 
       - 다른 테이블과의 외래 키 관계를 정의
- AUTOINCREMENT 키워드  
      <img src="images/create06.png" width=400 style='margin:1rem'>
  - 자동으로 고유한 정수 값을 생성하고 할당하는 필드 속성
  - 특징
    - 필드의 자동 증가를 나타내는 특수한 키워드
    - 주로 primary key 필드에 적용
    - INTEGER PRIMARY KEY AUTOINCREMENT가 작성된 필드는 항상 새로운 레코드에 대해 이전 최대 값보다 큰 값을 할당
    - 삭제된 값은 무시되며 재사용할 수 없게 됨


## Modifying table fields
- 📌 ALTER TABLE statement : 테이블 및 필드 조작
  - ALTER TABLE의 역할
     |명령어|역할|
     |:----|:----:|
     |ALTER TABLE `ADD COLUMN`| 필드 추가|
     |ALTER TABLE `RENAME COLUMN`| 필드 이름 변경|
     |ALTER TABLE `DROP COLUMN`|필드 삭제|
     |ALTER TABLE `RENAME TO`|테이블 이름 변경|
- ALTER TABLE ADD COLUMN syntax  
      <img src="images/alter-table.png" width=500 style='margin:1rem'>
  - ADD COLUMN 키워드 이후 추가하고자 하는 새 필드 이름과 데이터 타입 및 제약 조건 작성
  - 단, 추가하고자 하는 필드에 NOT NULL 제약 조건이 있을 경우 NULL이 아닌 기본 값 설정 필요
  - 활용
    - examples 테이블에 다음 조건에 맞는 Country 필드 추가     
        <img src="images/alter-table03.png" width=500 style='margin:1rem'>
        <img src="images/alter-table02.png" width=500 style='margin:1rem'>
      - 테이블 생성시 정의한 필드는 기본 값이 없어도 NOT NULL 제약 조건으로 생성되며 내부적으로 Default value는 NULL로 설정됨  
    - examples 테이블에 다음 조건에 맞는 Age, Address 필드 추가  
        <img src="images/alter-table05.png" width=500 style='margin:1rem'>
        <img src="images/alter-table04.png" width=500 style='margin:1rem'>
      - SQLite는 단일 문을 사용하여 한 번에 여러 필드를 추가할 수 없음 
- ALTER TABLE RENAME COLUMN syntax  
   <img src="images/alter-table06.png" width=500 style='margin:1rem'>
  - RENAME COLUMN 키워드 뒤에 이름을 바꾸려는 필드의 이름을 지정하고 TO 키워드 뒤에 새 이름을 지정
  - 활용
    - examples 테이블 Address 필드의 이름을 PostCode로 변경  
      <img src="images/alter-table08.png" width=500 style='margin:1rem'>
      <img src="images/alter-table07.png" width=500 style='margin:1rem'>
- ALTER TABLE DROP COLUMN syntax  
   <img src="images/alter-table09.png" width=500 style='margin:1rem'>
  - DROP COLUMN 키워드 뒤에 삭제 할 필드 이름 지정
  - 활용
    - examples 테이블의 PostCode 필드를 삭제   
      <img src="images/alter-table10.png" width=500 style='margin:1rem'>
- ALTER TABLE RENAME TO syntax  
   <img src="images/alter-table11.png" width=500 style='margin:1rem'>
  - RENAME TO 키워드 뒤에 새로운 테이블 이름 지정
  - 활용
    - examples 테이블 이름을 new_examples로 변경  
   <img src="images/alter-table13.png" width=500 style='margin:1rem'>
   <img src="images/alter-table12.png" width=300 style='margin:1rem'>

## Delete a table
- 📌 DROP TABLE statement : 테이블 삭제  
   <img src="images/drop-table.png" width=500 style='margin:1rem'>
  - DROP TABLE statement 이후 삭제할 테이블 이름 작성
- 활용
  - new_examples 테이블 삭제  
   <img src="images/drop-table02.png" width=300 style='margin:1rem'>

## 참고
- 타입 선호도(Type Affinity)  
   <img src="images/type-affinity.png" width=500 style='margin:1rem'>
  - 컬럼에 데이터 타입이 명시적으로 지정되지 않았거나 지원하지 않을 때 SQLite가 자동으로 데이터 타입을 추론하는 것
  - 참고 자료 : https://www.sqlite.org/datatype03.html
  - 목적
    1. 유연한 데이터 타입 지원
       - 데이터 타입을 명시적으로 지정하지 않고도 데이터를 저장하고 조회할 수 있음
       - 컬럼에 저장되는 값의 특성을 기반으로 데이터 타입을 유추 
    2. 간편한 데이터 처리
       - INTEGER Type Affinity를 가진 열에 문자열 데이터를 저장해도 SQLite는 자동으로 숫자로 변환하여 처리
    3. SQL 호환성 
       - 다른 데이터베이스 시스템과 호환성 유지
- 반드시 NOT NULL 제약을 사용해야 할까?
  - "NO"
  - 하지만 데이터베이스를 사용하는 프로그램에 따라 NULL을 저장할 필요가 없는 경우가 많으므로 대부분 NOT NULL을 정의
  - "값이 없다"라는 표현을 테이블에 기록하는 것은 "0"이나 "빈 문자열" 등을 사용하는 것으로 대체하는 것을 권장

# Modifying Data

## Insert data
- 사전 준비 : 실습 테이블 생성    
   <img src="images/insert.png" width=400 style='margin:1rem'>
- 📌 INSERT statement : 테이블 레코드 삽입   
   <img src="images/insert02.png" width=400 style='margin:1rem'>
  - INSERT INTO 절 다음에 테이블 이름과 괄호 안에 필드 목록 작성
  - VALUES 키워드 다음 괄호 안에 해당 필드에 삽입할 값 목록 작성
- 활용
  - articles 테이블에 다음과 같은 데이터 입력  
    <img src="images/insert04.png" width=400 style='margin:1rem'>
    <img src="images/insert03.png" width=300 style='margin:1rem'>
  - articles 테이블에 다음과 같은 데이터 추가 입력    
    <img src="images/insert06.png" width=400 style='margin:1rem'>
    <img src="images/insert05.png" width=300 style='margin:1rem'>
  - DATE 함수를 사용해 articles 테이블에 다음과 같은 데이터 추가 입력  
    <img src="images/insert08.png" width=400 style='margin:1rem'>
    <img src="images/insert07.png" width=300 style='margin:1rem'>

## Update data
- 📌 UPDATE statement : 테이블 레코드 수정  
   <img src="images/update.png" width=400 style='margin:1rem'>
  - SET 절 다음에 수정 할 필드와 새 값을 지정
  - WHERE 절에서 수정 할 레코드를 지정하는 조건 작성
  - WHERE 절을 작성하지 않으면 모든 레코드를 수정
- 활용
  - articles 테이블 1번 레코드의 title 필드 값을 'update Title'로 변경   
    <img src="images/update03.png" width=400 style='margin:1rem'>
    <img src="images/update02.png" width=300 style='margin:1rem'>
  - articles 테이블 2번 레코드의 title, content 필드 값을 각각 'update Title', 'update Content'로 변경  
    <img src="images/update05.png" width=400 style='margin:1rem'>
    <img src="images/update04.png" width=300 style='margin:1rem'>

## Delete data
- 📌 DELETE statement : 테이블 레코드 삭제  
    <img src="images/delete.png" width=400 style='margin:1rem'>
  - DELETE FROM 절 다음에 테이블 이름 작성
  - WHERE 절에서 삭제할 레코드를 지정하는 조건 작성
  - WHERE 절에서 작성하지 않으면 모든 레코드를 삭제
- 활용
  - articles 테이블의 1번 레코드 삭제   
    <img src="images/delete03.png" width=400 style='margin:1rem'>
    <img src="images/delete02.png" width=300 style='margin:1rem'>
  - articles 테이블에서 작성일이 오래된 순으로 레코드 2개 삭제  
    <img src="images/delete05.png" width=500 style='margin:1rem'>
    <img src="images/delete04.png" width=300 style='margin:1rem'>

## 참고
- SQLite의 날짜와 시간
  - SQLite에는 날짜 및/또는 시간을 저장하기 위한 별도 데이터 타입이 없음
  - 대신 날짜 및 시간에 대한 함수를 사용해 표기 형식에 따라 TEXT, REAL, INTEGER 값으로 저장
  - https://www.sqlite.org/datatype3.html

# Multi table queries

## Join
- 관계
  - 여러 테이블 간의 (논리적) 연결
- 관계의 필요성
  - step 1 : 커뮤니티 게시판에 필요한 데이터 생각해보기  
    <img src="images/join.png" width=400 style='margin:1rem'>
  - step 2  
    - '하석주'가 작성한 모든 게시글을 조회하기
    - 어떤 문제점이 있을까? 동명이인이 있다면 혹은 특정 데이터가 수정된다면?  
      <img src="images/join02.png" width=500 style='margin:1rem'>
  - step 3  
    - 테이블을 나누어 분류하자  
      <img src="images/join03.png" width=500 style='margin:1rem'>
    - 각 게시글은 누가 작성했는지 알 수 있을까?
    - 작성자들의 역할은 무엇일까?
  - step 4  
    - articles와 users 테이블에 각각 userId, roleId 왜래 키 필드 작성  
        <img src="images/join04.png" width=500 style='margin:1rem'>
    - 관리자인 사람만 보고싶다면? ➡️ roleId가 1인 데이터 조회
    - 하석주라는 사람이 권미숙으로 개명한다면? ➡️ users에서 한 번만 변경하면 자동으로 모두 변경
- Join이 필요한 순간
  - 테이블을 분리하면 데이터 관리는 용이해질 수 있으나 출력시에는 문제가 있음
  - 테이블 한 개만을 출력할 수 밖에 없어 다른 테이블과 결합하여 출력하는 것이 필요해짐 ➡️ 이때 사용하는 것이 "JOIN"

## Joining tables
- 📌 JOIN clause : 둘 이상의 테이블에서 데이터를 검색하는 방법
  - 종류
    - INNER JOIN
    - LEFT JOIN
- 사전 준비
  - users 및 articles 테이블 생성  
    <img src="images/joining-tables.png" width=500 style='margin:1rem'>
  - 각 테이블에 실습 데이터 입력  
    <img src="images/joining-tables02.png" width=800 style='margin:1rem'>
- 📌 INNER JOIN clause  
  - 두 테이블에서 값이 일치하는 레코드에 대해서만 결과를 반환  
    <img src="images/inner-join.png" width=200 style='margin:1rem'>
  - INNER JOIN syntax  
    <img src="images/inner-join02.png" width=200 style='margin:1rem'>
    - FROM 절 이후 메인 테이블 지정(table_a)
    - INNER JOIN 절 이후 메인 테이블과 조인할 테이블을 지정(table_b)
    - ON 키워드 이후 조인 조건을 작성
    - 조인 조건은 table_a와 table_b 간의 레코드를 일치시키는 규칙을 지정
  - 예시
    - 작성자가 있는 (존재하는 회원) 모든 게시글을 작성자 정보와 함께 조회  
      <img src="images/inner-join03.png" width=600 style='margin:1rem'>  
      <img src="images/inner-join04.png" width=600 style='margin:1rem'>  
      <img src="images/inner-join05.png" width=600 style='margin:1rem'>  
      <img src="images/inner-join06.png" width=400 style='margin:1rem'>
  - 활용
    - 1번 회원(하석주)가 작성한 모든 게시글의 제목과 작성자명을 조회  
      <img src="images/inner-join08.png" width=400 style='margin:1rem'>
      <img src="images/inner-join07.png" width=150 style='margin:1rem'>
- 📌 LEFT JOIN clause
  - 오른쪽 테이블의 일치하는 레코드와 함께 왼쪽 테이블의 모든 레코드 반환  
    <img src="images/left-join.png" width=200 style='margin:1rem'>
  - LEFT JOIN syntax  
    <img src="images/left-join02.png" width=500 style='margin:1rem'>
    - FROM 절 이후 왼쪽 테이블 지정(table_a)
    - LEFT JOIN 절 이후 오른쪽 테이블 지정(table_b)
    - ON 키워드 이후 조인 조건을 작성
      - 왼쪽 테이블의 각 레코드를 오른쪽 테이블의 모든 레코드와 일치시킴
  - 에시
    - 모든 게시글을 작성자 정보와 함께 조회  
      <img src="images/left-join03.png" width=500 style='margin:1rem'>  
      <img src="images/left-join04.png" width=500 style='margin:1rem'>  
      <img src="images/left-join05.png" width=500 style='margin:1rem'>  
      <img src="images/left-join06.png" width=400 style='margin:1rem'>
  - 특징
    - 왼쪽 테이블의 모든 레코드를 표기
    - 오른족 테이블과 맻이되는 레코드가 없으면 NUL을 표시
  - 활용
    - 게시글을 작성한 이력이 없는 회원 정보 조회  
      <img src="images/left-join08.png" width=400 style='margin:1rem'>
      <img src="images/left-join07.png" width=100 style='margin:1rem'>
