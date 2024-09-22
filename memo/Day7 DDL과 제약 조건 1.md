# Day7 DDL과 제약 조건 1

# 테이블 삭제

```sql
DROP TABLE 테이블명;
```

# 제약 조건 삭제

```sql
ALTER TABLE 테이블명 DROP CONSTRAINT 제약 조건명;
```

# 제약 조건 추가

```sql
ALTER TABLE 테이블명 ADD CONSTRAINT 제약 조건명 PRIMARY KEY(제약조건을 걸 컬럼);
```

# 예시 1

```sql
-- TBL_MEMBER 삭제
DROP TABLE TBL_MEMBER;

-- 해당 영역 전체화면 : 클릭 후 CTRL + M
-- 주석 : 컴퓨터가 해석하지 못하게 하는 문법
-- 1. 쿼리문(소스 코드)에 설명글을 달 때
-- 2. 지금 당장 사용하지 않는 소스 코드를 해석하고 싶지 않을 때

-- 자동차 테이블 생성
-- 제약 조건 : 테이블을 생성할 때 특정 컬럼에 조건을 부여하여 들어오는 데이터를 검사
CREATE TABLE TBL_CAR(
	ID NUMBER,
	BRAND VARCHAR2(100),
	COLOR VARCHAR2(100),
	PRICE NUMBER,
	CONSTRAINT CAR_PK PRIMARY KEY(ID)
);

DROP TABLE TBL_CAR;

-- 제약 조건 삭제
ALTER TABLE TBL_CAR DROP CONSTRAINT CAR_PK;

-- 제약 조건 추가
ALTER TABLE TBL_CAR ADD CONSTRAINT CAR_PK PRIMARY KEY(ID);

SELECT * FROM TBL_CAR;
-----------------------------------------------------------
-- 동물 테이블 생성
CREATE TABLE TBL_ANIMAL(
	ID NUMBER PRIMARY KEY,
	"TYPE" VARCHAR2(100), -- 오라클의 예약어를 컬럼명으로 쓰고 싶다면 ""를 붙여 쓸 수 있다.
	AGE NUMBER(3),
	FEED VARCHAR2(100)
);
-- 기존 제약조건 삭제(PK)
ALTER TABLE TBL_ANIMAL DROP CONSTRAINT SYS_C007066;
-- 제약 조건추가(PK)
ALTER TABLE TBL_ANIMAL ADD CONSTRAINT ANIMAL_PK PRIMARY KEY(ID);

DROP TABLE TBL_ANIMAL;

SELECT * FROM TBL_ANIMAL;
```