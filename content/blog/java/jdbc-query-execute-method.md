---
title: JDBC execute, executeQuery, executeUpdate 메서드 특징
date: 2019-03-07 01:03:62
category: java
---

# execute, executeQuery, executeUpdate 메서드
JDBC Type 4 드라이버는 쿼리를 실행 할 수 있도록 ```execute```, ```executeQuery```, ```executeUpdate``` 3개의 메서드를 제공합니다.

이번 글에서는 각 메서드의 차이점과 특징에 대해 알아보겠습니다.

## 1. execute
```execute``` 메서드는 모든 유형의 SQL 문장과 함께 사용할 수 있으며, ```boolean``` 값을 반환합니다. 반환 값이 ‘true’이면, ```getResultSet``` 메서드를 사용함으로써 결과 집합을 얻을 수 있습니다. 반대로 반환 값이 ‘false’이면, 업데이트 개수 또는 결과가 없는 경우입니다.

```execute``` 메서드는 <b>Select, Insert, Update, Delete, DDL 문을 모두 실행</b>할 수 있는 특징이 있습니다.

### execute 메서드

```java
public boolean execute(String sql) throws SQLException;
```

### 반환 값
- true : result
- false : update count or no result

## 2. executeUpdate
```executeUpdate``` 메서드는 데이터베이스에서 <b>데이터를 추가(Insert), 삭제(Delete), 수정(Update)하는 SQL 문을 실행</b>합니다. 메서드의 반환 값은 해당 SQL 문 실행에 영향을 받는 행 수를 반환합니다.

데이터베이스 개발 툴([SQLGate](https://www.sqlgate.com/), Toad, Sequel Pro)를 사용하다 보면, 쿼리 실행 후 메시지로 affectedRows 값을 사용자에게 보여줍니다. affectedRows 값은 사용자가 수행한 DML 문이 영향을 끼친 행 수를 나타내는데, 바로 ```executeUpdate``` 메서드의 반환 값입니다.

### executeUpdate 메서드

```java
public int executeUpdate(String sql) throws SQLException;
```

### 반환 값
- int : row count

## 3. executeQuery
```executeQuery``` 메서드는 데이터베이스에서 데이터를 가져와서 결과 집합을 반환합니다. 이 메서드는 <b>Select 문에서만 실행</b>하는 특징이 있습니다.

### executeQuery 메서드

```java
public ResultSet executeQuery(String sql) throws SQLException;
```

### 반환 값
- ResultSet : object that contains the data produced by the given query