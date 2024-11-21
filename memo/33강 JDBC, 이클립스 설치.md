# 33강 JDBC, 이클립스 설치

# JDBC란?

- Java DataBase Conectivity
- 자바 애플리케이션에서 다양한 종류의 데이터베이스에 접속하고 SQL 쿼리를 실행하여 데이터를 주고받을 수 있도록 해주는 자바 API

# 실습 테이블 생성

```sql
-- JDBC(Java DataBase Conectivity)
CREATE SEQUENCE MEMBER_SEQ
INCREMENT BY 1
START WITH 1
MINVALUE 1
MAXVALUE 1000;

CREATE TABLE TBL_MEMBER(
	NUM NUMBER,
	ID VARCHAR2(200),
	PW VARCHAR2(200),
	NAME VARCHAR(200),
	AGE NUMBER,
	CONSTRAINT MEMBER_PK PRIMARY KEY(NUM)
);

SELECT * FROM TBL_MEMBER;
```

# IDE 설치 및 설정하러가기

- [설치 및 환경설정하러 가기](https://blog.naver.com/coding_music/223616144644)