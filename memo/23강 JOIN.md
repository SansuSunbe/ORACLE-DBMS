# 23강 JOIN

# JOIN

- 여러 테이블에 흩어져 있는 정보 중 사용자가 필요한 정보만 가져와서
가상의 테이블처럼 만들고 결과를 보여주는 것
- 조회 테이블이 너무 많이 쪼개져 있으면 느리기 때문에
입력, 수정, 삭제의 성능을 향상시키기 위해 사용한다.

# 내부 조인(INNER JOIN)

- INNER 생략 가능
- 조건이 일치하는 값이 두 테이블에 모두 존재할 때 조회

```sql
테이블명A INNER JOIN 테이블명B ON 조건식
```

```sql
테이블명A JOIN 테이블명B ON 조건식
```

## 등가 조인

- ON절에 등호(비교)가 있을 때

## 비등가 조인

- ON절에 등호(비교)가 없을 때

# ON절과 WHERE절 차이

- ON절의 조건은 JOIN이 되면서 실행되고
WHERE절의 조건은 JOIN이 모두 끝나고 나서 실행된다.
- ON과 WHERE를 같이 사용할 때와, ON만 사용할 때의 결과가 같다면
ON만 사용하는 것이 좋다.

# ON절 실습

```sql
-- EMP 테이블 사용번호로 DEPT 테이블의 지역 검색하기
SELECT * FROM EMP;
SELECT * FROM DEPT;

SELECT EMP.DEPTNO, EMP.ENAME, EMP.JOB, DEPT.LOC FROM EMP JOIN DEPT
ON EMP.DEPTNO = DEPT.DEPTNO;
```

```sql
-- PLAYER 테이블에서 송종국 선수가 속한 팀의 전화번호 검색하기
SELECT * FROM PLAYER;
SELECT * FROM TEAM;

SELECT P.TEAM_ID, P.PLAYER_NAME, T.TEL FROM PLAYER P JOIN TEAM T
ON P.TEAM_ID = T.TEAM_ID AND P.PLAYER_NAME = '송종국';
```

```sql
-- JOBS 테이블에서 JOB_ID로 EMPLOYEES의JOB_TITLE, EMAIL, 성, 이름 검색
SELECT * FROM JOBS;
SELECT * FROM EMPLOYEES;

SELECT J.JOB_ID, J.JOB_TITLE, E.EMAIL, E.LAST_NAME ||' '||E.FIRST_NAME 이름
FROM JOBS J JOIN EMPLOYEES E
ON J.JOB_ID = E.JOB_ID;
```

```sql
-- 급여로 등급 나누기
SELECT * FROM SALGRADE;
SELECT * FROM EMP;
SELECT * FROM DEPT;

SELECT E.EMPNO, E.ENAME, S.GRADE, E.SAL FROM 
SALGRADE S JOIN EMP E
ON E.SAL BETWEEN S.LOSAL AND S.HISAL;

-- cardinality : 158
SELECT E.EMPNO, D.DNAME, E.ENAME, S.GRADE, E.SAL FROM 
SALGRADE S JOIN EMP E
ON E.SAL BETWEEN S.LOSAL AND S.HISAL
JOIN DEPT D
ON E.DEPTNO = D.DEPTNO;

-- cardinality : 158
SELECT E.EMPNO, D.DNAME, E.ENAME, S.GRADE, E.SAL FROM
SALGRADE S, EMP E, DEPT D
WHERE E.SAL BETWEEN S.LOSAL AND S.HISAL AND E.DEPTNO = D.DEPTNO;
```