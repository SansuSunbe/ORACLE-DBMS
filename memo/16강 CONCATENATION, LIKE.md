# 16강 CONCATENATION, LIKE

# CONCATENATION(연결)

- 조회된 테이블을 문장과 연결시키는 키워드
- “||”를 컬럼 사이에 넣음으로써 사용한다.
- ~의 포지션은 ??이다. 식으로 조회를 할 수 있다.

# 실습

```sql
SELECT * FROM STADIUM;
SELECT * FROM TEAM;

SELECT T.TEAM_ID AS "팀 아이디", S.ADDRESS "주소", T.TEL FROM STADIUM S, TEAM T;

-- CONCATENATION(연결) : || 
-- ~의 별명은 ??이다.
SELECT PLAYER_NAME ||'의 별명은' || NICKNAME ||'이다.' AS 자기소개 FROM PLAYER;

SELECT * FROM PLAYER;

-- ~의 포지션은 ??이다.
SELECT E_PLAYER_NAME ||'의 포지션은'|| "POSITION" || '이다' AS 포지션 FROM PLAYER;
```

# LIKE

- 포함된 문자열의 값을 찾으며 문자의 개수에도 제한을 주어 조회할 수 있음
- % : 모든 값
- %A : A로 끝나는 모든 값
- %_A : A로 끝나면서 두 자리 값

# 실습

```sql
-- LIKE : 포함된 문자열의 값을 찾음, 문자의 개수도 제한을 줄 수 있음.
-- % : 모든 것
-- '%A' : A로 끝나는 모든 값
-- '_A' : A로 끝나면서 두 자리인 값

SELECT * FROM TEAM WHERE TEAM_NAME LIKE '%천마';
SELECT * FROM PLAYER WHERE PLAYER_NAME LIKE '김%';
SELECT * FROM PLAYER WHERE PLAYER_NAME LIKE '김_';

-- PLAYER 테이블에서 이씨 찾기
SELECT * FROM PLAYER WHERE PLAYER_NAME LIKE '이%';
SELECT * FROM PLAYER WHERE PLAYER_NAME LIKE '이_';

-- PLAYER 테이블에서 김씨와 이씨 찾기
SELECT * FROM PLAYER
WHERE PLAYER_NAME LIKE '김%' OR 
PLAYER_NAME LIKE '이%';

-- PLAYER 테이블에서 이씨가 아닌 사람 찾기
-- NOT
SELECT * FROM PLAYER 
WHERE NOT PLAYER_NAME LIKE '이%';

-- PLAYER 테이블에서 세자리 김씨가 아닌 사람 찾기
SELECT * FROM PLAYER WHERE NOT PLAYER_NAME LIKE '김__';
```