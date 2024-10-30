# 20강 집계 함수, ORDER BY, CASE

# 집계 함수

- 여러 개의 값을 하나의 값으로 집계하여 나타낸다.
- WHERE 절에서는 사용 불가능
- NULL 값은 포함하지 않음

| 함수 | 설명 |
| --- | --- |
| AVG() | 평균 |
| MAX() | 최대 값 |
| MIN() | 최소 값 |
| SUM() | 총 합 |
| COUNT() | 개 수 |

# 집계 함수 예시

```sql
SELECT AVG(HEIGHT), MAX(HEIGHT), MIN(HEIGHT), SUM(HEIGHT), COUNT(HEIGHT) FROM PLAYER;
SELECT ROUND(AVG(HEIGHT), 2), MAX(HEIGHT), MIN(HEIGHT), SUM(HEIGHT), COUNT(HEIGHT) FROM PLAYER;

-- PLAYER 테이블에서 HEIGHT 개수 검색(NULL 포함해서 COUNT 하기)
SELECT COUNT(HEIGHT) FROM PLAYER;
SELECT * FROM PLAYER;
SELECT COUNT(NVL(HEIGHT, 0)) FROM PLAYER;
```

# ORDER BY

- 정렬 명령어

| 명령어 | 설명 |
| --- | --- |
| ASC | 오름차순 |
| DESC | 내림차순 |

# ORDER BY 예시

```sql
SELECT * FROM PLAYER ORDER BY HEIGHT;
SELECT * FROM PLAYER ORDER BY HEIGHT DESC;
SELECT * FROM PLAYER ORDER BY 12 DESC; -- 12번째 컬럼을 기준으로 정렬

-- PLAYER 테이블에서 키 순, 몸무게 순(오름차순)으로 검색
-- NULL이 아닌 값만 검색
-- 첫 번째 컬럼 값이 같으면 두 번째 정렬을 한다.
SELECT PLAYER_NAME, HEIGHT, WEIGHT FROM PLAYER
WHERE HEIGHT IS NOT NULL AND WEIGHT IS NOT NULL
ORDER BY 2, 3;
```

# CASE 문

- SQL의 조건문

```sql
CASE WHEN 조건식 WHERE THEN '참 값' ELSE '거짓 값' END
```

# CASE문 예시

```sql
-- EMP 테이블에서 SAL 3000 이상이면 HIGH 1000이상이면 MID, 다 아니면 LOW
SELECT * FROM EMP;
SELECT ENAME 사원명, SAL 급여,
	CASE 
		WHEN SAL >= 3000 THEN 'HIGH'
		WHEN SAL >= 1000 THEN 'MID'
		ELSE 'LOW'
	END
FROM EMP;
```

```sql
-- STADIUM 테이블에서 SEAT_COUNT가 0 이상 30000이하면 'S'
-- 300001 이상 50000이하면 'M' 다 아니면 'L'
-- 중첩 케이스문
SELECT STADIUM_NAME 경기장, SEAT_COUNT 좌석수,
	CASE 
		WHEN SEAT_COUNT BETWEEN 0 AND 30000 THEN 'S'
		ELSE (
			CASE 
				WHEN SEAT_COUNT BETWEEN 30001 AND 50000 THEN 'M'
				ELSE 'L'
			END
			)
	END
FROM STADIUM;
```

```sql
-- PLAYER 테이블에서 WEIGHT가 50이상 70이하면 'L'
-- 71 이상 80 이하면 'M' NULL이면 '미등록' 다 아니면 'H'
SELECT PLAYER_NAME 선수이름, WEIGHT || 'kg' 몸무게,
	CASE
		WHEN WEIGHT BETWEEN 50 AND 70 THEN 'L'
		WHEN WEIGHT BETWEEN 71 AND 80 THEN 'M'
		ELSE
			(
			CASE WHEN WEIGHT IS NULL THEN '미등록'
			ELSE 'H'
			END 
			)
	END 체급
FROM PLAYER;
```