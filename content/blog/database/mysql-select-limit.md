---
title: MySQL SELECT 문장에서 Limit 사용법
date: 2019-03-07 01:03:06
category: database
---

Limit 단어는 ‘한계’, ‘한도’ 라는 단어 뜻을 갖고 있습니다. MySQL 데이터베이스 Select 문장에서 ```Limit``` 키워드를 사용하면 테이블 데이터 조회 시 한계를 지정할 수 있습니다.

예를 들어, 테이블에서 10개의 데이터만 가져오는 SELECT 문장을 만들기 위해서는 아래처럼 사용하면 됩니다.

```sql
-- 행 데이터 10개만 조회하기
SELECT title, content, writer FROM board LIMIT 10;
```

그리고 ```Offset``` 옵션을 이용하면, 가져오고자 하는 행 데이터의 <b>시작 지점을 지정</b>할 수 있습니다.

아래 쿼리를 실행하면 테이블의 11행부터 20행까지의 데이터를 가져옵니다.

```sql
-- 11번째 ~ 20번째 행 데이터 조회
SELECT title, content, writer FROM board LIMIT 10, 10;
```

```Offset``` 값은 0부터 시작하므로 첫 번째 행 데이터를 가리키는 값은 0 입니다.