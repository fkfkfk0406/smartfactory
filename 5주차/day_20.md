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

## 제약사항에 이름을 지정 할 수 있다고 ~~~?? 이름 지정은 'CONSTRAINT'
![화면 캡처 2024-07-22 111726](https://github.com/user-attachments/assets/5aa637ee-e9a0-46b0-8159-681f26afd1ea)
***

## 제약이 없는 칼럼에 제약을 줄 수도 있음~~~ NOT NULL 을 줬다가 NULL을 주면 제약을 뺄 수 있음~~~
![화면 캡처 2024-07-22 112146](https://github.com/user-attachments/assets/ea426c4a-3a7c-4c92-9676-135fb1556baf)
![화면 캡처 2024-07-22 112156](https://github.com/user-attachments/assets/7f2da55c-4395-4565-997a-2b1259cde11a)



물론 이름 지정 해줄 수도 있음
![화면 캡처 2024-07-22 112326](https://github.com/user-attachments/assets/5900cb49-3414-4e7c-8adb-40958e95167c)



물론 삭제도 됨
![화면 캡처 2024-07-22 112636](https://github.com/user-attachments/assets/1815b6aa-384a-4cc7-ad0a-390a0bfdd267)



물론 이름도 바꿔짐
![화면 캡처 2024-07-22 112809](https://github.com/user-attachments/assets/d6ee33ef-641f-4a78-9911-a927ce42ce62)
***







