---
title: MySQL 테이블, 뷰, 프로시저, 함수, 트리거 생성 스크립트 조회
date: 2019-03-16 13:03:10
category: database
---

MySQL 데이터베이스에서 사용되는 테이블, 뷰, 프로시저, 함수 등 오브젝트의 스크립트 정보가 필요한 경우가 있습니다. 사실 데이터베이스 접속 및 관리를 도와주는 프로그램인 [SQLGate](https://www.sqlgate.com/), [Workbench](https://www.mysql.com/products/workbench/)를 사용하면 손쉽게 정보를 얻을 수 있습니다.

프로그램 내부적으로 어떤 SQL 문장을 데이터베이스에 요청해서 생성 스크립트 정보를 가져오는지 알아보도록 하겠습니다.

## MySQL SHOW 명령어 
MySQL에서는 데이터베이스, 테이블, 컬럼, 뷰, 상태 정보 등을 제공하기 위해서 ```SHOW```를 지원합니다. 예를 들어 현재 데이터베이스에서 테이블 목록을 출력하고 싶다면 다음과 같은 쿼리를 실행하면 됩니다.

```sql
SHOW TABLES;
```

<br/>

테이블 목록을 출력한 것처럼 테이블 생성 스크립트를 조회하기 위해서는 ```SHOW```를 사용합니다. 다만, SHOW 명령어 뒤에 정보가 달라지게 됩니다.

테이블 생성 스크립트 조회는 다음과 같은 쿼리를 실행하면 됩니다. ```SHOW``` 명령어 뒤에 ```CREATE TABLE```을 쓰고 ```테이블 이름(actor)```를 작성합니다.

```sql
SHOW CREATE TABLE actor;
```

<br/>

 이와 유사하게 프로시저 생성 스크립트를 가져오기 위해서는 ```SHOW``` 명령어 뒤에 ```CREATE PROCEDURE```를 쓰고 ```프로시저 이름```을 작성하면 됩니다.

```SHOW``` 명령어는 특정 정보를 보여주기 위해서 사용합니다. 이번 글에서 설명한 오브젝트 목록, 오브젝트 생성 스크립트 이외에도 다양한 정보를 볼 수 있습니다. 자세한 정보는 [공식 문서](https://dev.mysql.com/doc/refman/8.0/en/show.html)를 참고해주시기 바랍니다.

## 테이블 생성 스크립트 조회
```sql
SHOW CREATE TABLE 테이블_이름;
```

## 뷰 생성 스크립트 조회
```sql
SHOW CREATE TABLE 뷰_이름;
```

## 함수 생성 스크립트 조회
```sql
SHOW CREATE FUNCTION 함수_이름;
```

## 프로시저 생성 스크립트 조회
```sql
SHOW CREATE PROCEDURE 프로시저_이름;
```

## 트리거 생성 스크립트 조회
```sql
SHOW CREATE TRIGGER 트리거_이름;
```

## 이벤트 생성 스크립트 조회
```sql
SHOW CREATE EVENT 이벤트_이름;
```