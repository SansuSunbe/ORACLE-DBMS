# 18강 정규화 - 이상현상, NULL

# 이상현상의 종류

## 삽입 이상

- 새 데이터를 삽입하기 위해 불필요한 데이터도 삽입해야 하는 문제

## 갱신 이상

- 중복 행 중 일부만 변경하여 데이터가 불일치하게 되는 모순의 문제 발생

## 삭제 이상

- 행을 삭제하면 꼭 필요한 데이터까지 함께 삭제되는 문제

# 이상 현상의 발생 이유

- 테이블이 정규화가 되어 있지 않기 때문
- 정규화를 진행하기 위해서는 각 컬럼간의 관련성을 파악해야 하고, 이 관련성을 “함수적 종속성(Functional Dependecy)” 라고 한다.
- 따라서 하나의 테이블에서는 하나의 함수적 종속성만 존재하도록 정규화를 한다.

# 예시

- 함수 X → Y
- X는 결정자 → X가 Y를 결정
- Y는 종속자 → Y가 X에 종속

# NULL

- 정의되지 않은 값
- 빈 값 대신 미정 값을 부여할 때 사용(PK는 불가능, FK는 가능)

# NOT NULL 제약 조건

```sql
ALTER TABLE 테이블명 MODIFY 컬럼명 NOT NULL;
```

# 제약 조건 삭제

```sql
ALTER TABLE 테이블명 DROP CONSTRAINT 제약 조건 이름;
```

# 조건식

- 컬럼명 IS NULL :
    - 컬럼 값이 NULL 이면 참
- 컬럼명 IS NOT NULL :
    - 컬럼 값이 NULL이 아니면 참

## NULL 값을 다른 값으로 변경

- NVL() :
    - NULL 값 대신 다른 값으로 변경 후 검색
- NVL2() :
    - NULL 일 때의 값, NULL이 아닐 때의 값을 각각 설정

# 실습

```sql
DROP TABLE TBL_CAR;
SELECT * FROM TBL_CAR;

CREATE TABLE TBL_CAR(
	ID NUMBER,
	BRAND VARCHAR2(300),
	COLOR VARCHAR2(150),
	PRICE NUMBER(10),
	CONSTRAINT CAR_PK PRIMARY KEY(ID)
);

ALTER TABLE TBL_CAR MODIFY BRAND NOT NULL;
ALTER TABLE TBL_CAR DROP CONSTRAINT SYS_C007245;

-- PLAYER 테이블에서 POSITION이 NULL인 선수 검색
SELECT * FROM PLAYER WHERE "POSITION" IS NULL;
SELECT * FROM PLAYER WHERE "POSITION" IS NOT NULL;

```