## 20일차 (5주차 시작,,,!)

## 오전 뇌풀기 복습퀴즈
```
﻿ID        Number(5)
NAME   Varchar2(30)
----------------------------------------
Add로 컬럼을 추가해 주세요.
HP        Varchar2(20)    
HP ---> 테이블 이름을 TEL로 변경해 주세요.
-----------------------------------------------------
TEL ----> 열의 타입을 Varchar2(13) 로 타입을 변경해 주세요.
------------------------------------------------------
TEL ---> 컬럼을 삭제해 주세요.

Hint ) Alter Table
```
## 풀이
```
CREATE TABLE PERSON (
    ID      NUMBER(5),
    NAME    VARCHAR(30)
    );
    

ALTER TABLE PERSON
ADD HP VARCHAR(20);

ALTER TABLE PERSON
RENAME COLUMN HP TO TEL;

ALTER TABLE PERSON
MODIFY TEL VARCHAR2(13);

ALTER TABLE PERSON
DROP COLUMN TEL;
```
***

## 시퀀스 만들어보기
![화면 캡처 2024-07-22 103356](https://github.com/user-attachments/assets/210c9074-81a8-4595-af48-32306ad151a9)
***

## 제약조건 실습
![화면 캡처 2024-07-22 104620](https://github.com/user-attachments/assets/79fa212d-37c7-43c5-b380-78270ede27aa)
***





