# Day02 오라클 DBMS 계정 설정

# 오라클 DBMS 버전(알파벳 의미)

- i : internet
- g : grid
- c : cloud

# 계정

- sys :
    - 모든 권한
- system :
    - 계정 관리
- 일반 계정 :
    - 해당 스키마 관리(hr, op, he, scott…)

# 스키마

- 정리가 잘 되어 있는 표들의 묶음, 상태

# RDBMS(관계형 데이터베이스 시스템)

- 테이블끼리 서로 관계를 맺는다.
- R의 의미 : 릴레이션
    - 릴레이션 : 관계

# DBA 접속

1. cmd 실행
2. ‘sqlplus system/초기 설정한 비밀번호 입력’

# 계정 정보 변경

1. cmd 실행
2. ‘sqlplus sys as sysdba’ 입력
3. 초기 설정한 비밀번호 입력
4. ‘alter user 유저명(system, hr 등) identified by 변경할 비밀번호;(세미콜론)’

# 계정 로그인

1. cmd 실행
2. ‘conn 계정명/비밀번호’
3. ‘show user’ 명령어로 현재 접속 중인 계정 확인

# 계정 언락

1. cmd 실행
2. ‘alter user ~의 계정(hr account 등) unlock;’

# Tip

- cmd 창에서 이전에 썼던 명령어를 다시 쓸려면 화살표(↑) 입력
- 다른 계정의 권한이나 정보를 수정할 때는 “system” or “sys” 연결이 먼저
- ‘exit’ 명령어로 계정 로그아웃 또는 cmd 창 종료

# 정리

1. CMD 실행
2. ‘sqlplus sys as sysdba’ 입력
3. ‘ORACLE 설치 시 설정한 비밀번호 입력’
4. ‘alter user system(계정명) identified by 설정할 비밀번호;(세미콜론)’ 입력
5. ‘conn system(계정명)/설정한 비밀번호’ 입력
6. ‘alter user hr account(hr의 account) unlock;(세미콜론)’ 입력
7. ‘alter user hr(계정명) identified by hr(비밀번호);(세미콜론)’ 입력\
8. ‘conn hr(계정명/hr(비밀번호)’