# 15강 TCL, AS

# TCL(Transaction Control Language)

- 트랜젝션 제어 언어
- DML을 위한 명령어

## 트랜젝션

- 하나의 작업 단위

## COMMIT

- 모든 작업을 확정하는 명령어

## ROLLBACK

- 이전 커밋한 지점으로 이동

## TRUNCATE

- 테이블 내용을 전체 삭제하므로, DELETE보다 빠르게 처리할 수 있다.
- 대용량 데이터 처리에 유리하다. 하지만 복구가 불가능하기 때문에 복구가 가능한 ‘DELETE’를 많이 사용한다.

# 트랜젝션 설정

- DBEAVER를 실행하면 상단에  T 모양의 버튼을 클릭

![image](https://github.com/user-attachments/assets/5394f6bf-f6c1-44ce-b0ea-c095e3490748)

- T 모양 클릭 후 변화

![image 1](https://github.com/user-attachments/assets/4233c7f2-cc0a-407c-84cf-7130a083e790)

- 명령어 두 개를 실행 후 확정 대기 카운트가 뜨고 커밋 버튼을 누르면 명령어가 확정된다.

![image 2](https://github.com/user-attachments/assets/9bd076ad-cabc-4e3f-a8d1-b960a666c8fa)

- 롤백 버튼을 누르자 확정 대기 명령어 카운트가 사라지고 명령어는 이전 커밋하기 전으로 돌아간다.

![image 3](https://github.com/user-attachments/assets/a736a59a-fbfb-4e47-a689-21ad3843959d)

# 실습

```sql
-- PLAYER 테이블에서 TEAM_ID가 'K01'인 선수 이름을 내 이름으로 바꾸기
UPDATE PLAYER 
SET PLAYER_NAME = 'LJW'
WHERE TEAM_ID = 'K01'; 

SELECT PLAYER_NAME FROM PLAYER 
WHERE TEAM_ID = 'K01';
```

- 결과

![image 4](https://github.com/user-attachments/assets/94730023-948d-4fa0-9d3b-21833934e9f7)

- 롤백으로 되돌린 후

![image 5](https://github.com/user-attachments/assets/49d981c8-0298-426b-b1a8-80b87a030a72)

# AS(ALIAS)

- 별칭 또는 별명이라는 뜻
- SELECT 절 : AS 뒤에 별칭 작성, 한 칸 띄우고 작성
- FROM 절 : 한 칸 띄우고 작성

# AS 실습

- 테이블과 컬럼에 별칭을 주어 가독성과 코드의 길이를 줄일 수 있다.

```sql
SELECT PLAYER_ID AS "선수 번호" FROM PLAYER;
SELECT PLAYER_ID "선수 번호" FROM PLAYER;
SELECT PLAYER_ID "선수 번호", PLAYER_NAME AS "선수 이름" FROM PLAYER;

-- PLAYER 테이블에서 BACK_NUM를 "등 번호"로, NICKNAME을 "선수 별명"으로 바꿔서 검색
SELECT BACK_NO AS "등 번호", NICKNAME "선수 별명" FROM PLAYER;

SELECT P.TEAM_ID "선수 테이블", T.TEAM_ID "팀 테이블" FROM PLAYER P, TEAM T;
```
