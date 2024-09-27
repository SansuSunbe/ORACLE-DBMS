# Day09 모델링 이론 - 회원, 상품, 주문

# 모델링

- 추상적인 주제를 DB(DataBase)에 맞게 설계하는 것

## 1. 요구사항 분석

- 회원, 주문, 상품 3가지를 관리하고자 함

## 2. 개념적 설계(개념 모델링)

| 회원 | 주문 | 상품 |
| --- | --- | --- |
| ——————— | ——————— | ——————— |
| ID | 주문 번호 | 상품 번호 |
| PW | 주문 일 | 상품명 |
| 이름 | ID | 가격 |
| 주소 | 상품 번호 | 재고량 |
| 이메일 |  |  |
| 생일 |  |  |

## 3. 논리적 설계(논리 모델링)

| 회원 | 주문 | 상품 | 결제 정보 |
| --- | --- | --- | --- |
| ID(PK) | 주문 번호(PK) | 상품 번호(PK) | 계좌 번호(PK) |
| ——————— | ——————— | ——————— | ——————— |
| PW | 주문 일 | 상품명 | 은행명(PK) |
| 이름 | ID(FK) | 가격 | 예금주 |
| 주소 | 상품 번호(FK) | 재고량 | CVC |
| 이메일 | 계좌 번호(FK) |  |  |
| 생일 |  |  |  |

## 4. 물리적 설계(물리 모델링)

| USER |
| --- |
| USER_ID : VARCHAR2(100) |
| ——————————————— |
| USER_PW : VARCHAR2(100) |
| USER_NAME : VARCHAR2(100) |
| USER_ADDRESS : VARCHAR2(300) |
| USER_EMAIL : VARCHAR2(300) |
| USER_BIRTH : DATE |

| PRODUCT |
| --- |
| PRODUCT_NUM : NUMBER |
| ——————————————— |
| PRODUCT_NAME : VARCHAR2(300) |
| PRODUCT_PRICE : NUMBER |
| PRODUCT_COUNT : NUMBER |

| ORDER |
| --- |
| ORDER_NUM : NUMBER |
| ——————————————— |
| ORDER_DATE : DATE |
| USER_ID : VARCHAR2(100) |
| PRODUCT_NUM : NUMBER |

## 5. 구현
