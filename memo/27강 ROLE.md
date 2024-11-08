# 27강 ROLE

# ROLE

- 권한이 뭉쳐 있는(모여 있는) 상태
- 데이터베이스에서 특정 사용자에게 부여할 수 있는 권한의 집합
- CONNECT, RESOURCE, DBA

```sql
GRANT 권한명(ROLE 이름), 권한명2... TO 계정명
```

```sql
REVOKE 권한명(ROLE 이름) FROM 계정명
```

# ROLE 예시

```sql
-- ROLE 생성
CREATE ROLE manager;

-- ROLE에 권한 부여
GRANT ALL PRIVILEGES ON employees TO manager;

-- 사용자에게 ROLE 부여
GRANT manager TO user3;
```

# ROLE, DML 실습

```sql
-- SCOTT 테이블에서 SALGRADE를 복사한 후 GRADE 컬럼명을 LEVEL로 변경, 값을 반대로 바꾸기
-- 5 -> 1
-- 4 -> 2
-- ...
-- 1 -> 5
CREATE TABLE SALGRADE AS SELECT * FROM SCOTT.SALGRADE;
SELECT * FROM SALGRADE;
ALTER TABLE SALGRADE RENAME COLUMN GRADE TO "LEVEL";
-- 5 4 3 2 1
-- 1 2 3 4 5
UPDATE SALGRADE
SET "LEVLE" = 6 - "LEVEL";
```