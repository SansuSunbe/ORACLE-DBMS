# Day06 DDL과 자료형

# SQL(structured query language)문 종류

- DDL : 데이터 정의어
- DML : 데이터 조작어
- TCL : 트랜잭션 제어어
- DCL : 데이터 제어어

# DDL(Data Definition Laguage)

- 데이터 정의어
- 테이블 조작, 제어 관련 쿼리문
1. CREATE : 테이블 생성
2. DROP : 테이블 삭제
3. ALTER : 테이블 수정
    1. 테이블 명 수정 : 
        
        ```sql
        RENAME TO [새로운 테이블명];
        ```
        
    2. 컬럼 추가 : 
        
        ```sql
        ADD([새로운 컬럼명] [컬럼 타입]);
        ```
        
    3. 컬럼명 변경 : 
        
        ```sql
        RENAME COLUMN [새로운 컬럼명] TO [새로운 컬럼명];
        ```
        
    4. 컬럼 삭제
        
        ```sql
        DROP COLUMN [새로운 컬럼명];
        ```
        
4. TRUNCATE : 테이블 내용 전체 삭제

# 자료형(Type)

- 숫자
    
    ```sql
    NUMBER(precision) -- 정수
    NUMBER(precision, 소수점 자리수) -- 실수
    NUMBER -- 생략 시 22byte까지 입력 가능(38자리 정수)
    ```
    
- 문자열
    
    ```sql
    CHAR(길이); -- 고정형
    	CHAR(4); -- 에 'A'를 넣으면 A^^^ 빈 자리가 공백으로 채워짐
    	-- 형식을 정한 날짜, 주민등록번호처럼 글자 수가 절대 변하지 않는 값을 넣는다.
    	
    VARCHAR(길이), VARCHAR2(길이) -- 가변형
    -- 값의 길이 만큼 공간이 배정된다. 글자 수에 변화가 있는 값을 넣는다.
    
    DATE -- FORMAT에 맞춰서 날짜를 저장하는 타입
    ```
    

# 테이블 생성 예시

- 세미콜론에 마우스를 갖다 대고 Ctrl + Enter 를 입력하면 테이블이 생성된다.
- 테이블 생성 후 밑에 결과창에 테이블 생성 알림을 통해 테이블이 정상적으로 생성 됐음을 확인할 수 있다.
- 계정을 한번 클릭 후 F5 버튼을 눌려 새로 고침하면 계정에 테이블이 추가된 것을 확인할 수 있다.

![image](https://github.com/user-attachments/assets/e10205f5-05f7-444e-a7af-5d8c0ee5c549)
