# 12강 DML - WHERE 조건식

# DML 종류

- SELECT
    - 데이터 조회
- INSERT
    - 데이터 삽입
- UPDATE
    - 데이터 갱신
- DELETE
    - 데이터 삭제

# 조건식이란?

- 참 또는 거짓 둘 중 하나의 결과가 나오는 식

# WHERE 조건식 종류

- >, <
    - 크다(초과), 작다(미만)
- >=, <=
    - 크거나 같다(이상), 작거나 같다(이하)
- =
    - 같다
- <>, !=, ^=
    - 같지 않다
- AND
    - 두 조건식 모두 참이면 참
- OR
    - 둘 중 하나라도 참이면 참

# 추가 및 삭제 주의점

- 추가 :
    - 부모와 자식 중 부모 테이블에 값을 먼저 추가해야 한다.
- 삭제 :
    - 부모와 자식 중 자식 테이블에서 참조하는 값들을 먼저 삭제해야 한다.

# DELETE와 TRUNCATE 차이

- DELETE
    - 데이터 복구 가능
- TRUNCATE
    - 데이터 복구 불가능

# 실습

```sql
SELECT FLOWERNAME, FLOWERCOLOR, FLOWERPRICE FROM FLOWER;

-- 추가 : 부모와 자식 중 부모 테이블에 값을 먼저 추가해야 한다.

INSERT INTO FLOWER
(FLOWERNAME, FLOWERCOLOR, FLOWERPRICE)
VALUES('장미', 'RED', 3000);

INSERT INTO FLOWER
(FLOWERNAME, FLOWERCOLOR, FLOWERPRICE)
VALUES('해바라기', 'YELLOW', 5000);

INSERT INTO FLOWER
(FLOWERNAME, FLOWERCOLOR, FLOWERPRICE)
VALUES('할미꽃', 'WHITE', 9000);

-- 삭제 : 부모와 자식 중 자식 테이블에서 참조하는 값들을 먼저 삭제해야 한다.
DELETE FROM FLOWER
WHERE FLOWERNAME = '장미';

SELECT * FROM POT;

INSERT INTO POT
(POTID, POTCOLOR, POTSHAPE, NAME)
VALUES('20240505001', 'WHITE', '물레방아', '장미');

INSERT INTO POT
(POTID, POTCOLOR, POTSHAPE, NAME)
VALUES('20240505002', 'BLACK', '타원형', '해바라기');

INSERT INTO POT
(POTID, POTCOLOR, POTSHAPE, NAME)
VALUES('20240505004', 'RED', '타원형', '할미꽃');

DELETE FROM POT
WHERE NAME = '장미';

-- DELETE 와 TRUNCATE 차이
-- DELETE는 복구 가능
-- TRUNCATE는 복구 불가능

-- UPDATE

UPDATE POT 
SET POTCOLOR = 'WHITE'
WHERE NAME = '할미꽃' AND POTSHAPE = '타원형';
```