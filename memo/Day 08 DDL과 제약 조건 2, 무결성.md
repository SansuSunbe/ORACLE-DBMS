# Day 08 DDL과 제약 조건 2, 무결성

# 생성한 테이블에 데이터 INSERT 하기

1. 다이어그램 들어가서 테이블 우클릭 하기
2. SQL 생성 → INSERT 클릭
3. COPY 클릭 후 Script 파일에 붙여넣기(Ctrl + V)

![image.png](image.png)

![image.png](image%201.png)

# 무결성

- 데이터의 정확성, 일관성, 유효성이 유지되는 것

## 정확성

- 데이터는 애매하지 않아야 한다.

## 일관성

- 각 사용자가 일관된 데이터를 볼 수 있도록 해야 한다.

## 유효성

- 데이터가 실제 존재하는 데이터여야 한다.

### 1. 개체 무결성

- 모든 테이블이 PK로 선택된 컬럼을 가져야 한다.
- PK로 선택된 컬럼은 고유한 값을 가져야 하며, 빈 값, NULL 값은 허용하지 않는다.

### 2. 참조 무결성

- 두 테이블의 데이터가 항상 일관된 값을 가지도록 유지하는 것

### 3. 도메인 무결성

- 컬럼의 타입, NULL 값의 허용 등에 대한 사항을 정의하고, 올바른 데이터가 입력되었는지를 확인 하는것

# 테이블 제약 조건 생성 예시

```sql
-- 제약 조건 DEFAULT와 CHECK
-- 학생 테이블 생성
CREATE TABLE TBL_STUDENT(
	ID NUMBER,
	NAME VARCHAR2(100),
	MAJOR VARCHAR2(100),
	GENDER CHAR(1) DEFAULT 'W' NOT NULL CONSTRAINT BAN_CHAR CHECK(GENDER IN('M', 'W')),
	BIRTH DATE CONSTRAINT BAN_DATE CHECK(BIRTH >= TO_DATE('1980-01-01', 'YYYY-MM-DD')),
	CONSTRAINT STD_PK PRIMARY KEY(ID)
);

SELECT * FROM TBL_STUDENT;

INSERT INTO TBL_STUDENT
(ID, NAME, MAJOR, GENDER, BIRTH)
VALUES(1, '홍길동', '코딩학과', 'M', TO_DATE('1980-01-01', 'YYYY-MM-DD')); -- 위에 생성한 테이블과 다른 형식을 입력하면 에러 발생

INSERT INTO TBL_STUDENT
(ID, NAME, MAJOR, BIRTH)
VALUES(2, '홍길동', '전자과', TO_DATE('2000-05-05', 'YYYY-MM-DD'));

TRUNCATE TABLE TBL_STUDENT; -- 테이블안에 있는 데이터 삭제
```