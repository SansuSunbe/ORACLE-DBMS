# 28강 테이블 복사, VIEW 생성

# 테이블 복사 실습

```sql
-- SCOTT 계정의 EMP 테이블을 복사해서 비등가 조인으로 등급별 ENAME, SAL 검색하기
CREATE TABLE EMP AS SELECT * FROM SCOTT.EMP;

SELECT * FROM EMP;
SELECT * FROM SALGRADE;

SELECT S."LEVEL", E.ENAME, E.SAL FROM EMP E JOIN SALGRADE S
ON E.SAL BETWEEN S.LOSAL AND S.HISAL ORDER BY 1;
```

```sql
-- HR 계정의 DEPT 테이블을 복사, 복사한 테이블에서 LOC별 평균 급여 검색(단, LOC 모두 검색)
CREATE TABLE COPY_DEPT AS SELECT * FROM HR.DEPT;
CREATE TABLE COPY_EMP AS SELECT * FROM HR.DEPT;

SELECT LOC, NVL(AVG(E.SAL), 0) 평균급여  FROM COPY_DEPT D LEFT OUTER JOIN COPY_EMP E
ON D.DEPTNO = E.DEPTNO
GROUP BY LOC;

SELECT * FROM COPY_DEPT;
```

# VIEW

- 기존의 테이블은 그대로 놔둔 채 필요한 컬럼들 및 새로운 컬럼을 만든 가상 테이블
- 실제 데이터가 저장되는 것은 아니지만 VIEW를 통해서 데이터를 관리할 수 있다.

# VIEW 특징

- 독립성 :
    - 다른 계정에서 데이터를 변경하지 못함
- 편리성 :
    - 긴 쿼리문을 짧게 줄일 수 있다.
- 보안성 :
    - 짧게 만들기 때문에 기존의 쿼리는 보이지 않는다.

# VIEW 연습

```sql
CREATE VIEW PLAYER_AGE
AS(SELECT ROUND((SYSDATE - BIRTH_DATE) / 365) AGE, P. * FROM COPY_PLAYER P);

SELECT * FROM PLAYER_AGE;

DROP VIEW PLAYER_AGE;

-- 30살이 넘은 선수들 검색
SELECT * FROM PLAYER_AGE WHERE AGE > 30;
```