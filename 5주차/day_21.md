## 21일차~~~
어제 토스를 들었더니 피곤하다,,

## 복습
![화면 캡처 2024-07-23 091738](https://github.com/user-attachments/assets/d1c39b14-7226-405f-b67c-3b294c89bf39)
***
![화면 캡처 2024-07-23 093853](https://github.com/user-attachments/assets/7c81eb46-d660-48b3-8598-00de6080c6b7)



중복해서 넣었을 때 (제약을 걸어놨잖슴~~)
![화면 캡처 2024-07-23 093931](https://github.com/user-attachments/assets/defe4b63-71e3-4071-a0e7-0a360407c60b)
***

## 제약조건 이름바꾸기
![화면 캡처 2024-07-23 094526](https://github.com/user-attachments/assets/7b09d04b-5f0e-4401-93f8-9534445c02f9)
***

## 제약조건 삭제하기
![화면 캡처 2024-07-23 094936](https://github.com/user-attachments/assets/14c0c8b6-e54b-4ce7-b63b-9af6096c884d)
***

## 프라이머리 키
![화면 캡처 2024-07-23 101257](https://github.com/user-attachments/assets/bdf689f7-dbc1-4ab5-84c4-082283cba196)
***

## 인덱스 확인
![화면 캡처 2024-07-23 101338](https://github.com/user-attachments/assets/aca6b598-870f-4adf-996b-91a231801ee2)
***

## 테이블 작성 방법
![화면 캡처 2024-07-23 102555](https://github.com/user-attachments/assets/655b3754-4b9c-48fd-b929-ba9a74a3c6e2)




이렇게 작성해도 된다,,,~~~!
***

## 테이블간의 관계연산 만들기
![화면 캡처 2024-07-23 104103](https://github.com/user-attachments/assets/ba035f3b-83e7-4b60-925a-f2fae0bd29de)



참조하는 값을 가지는 데이터를 DROP 하려면 참조값을 먼저 DROP 해야 DROP 할 수 있음 (무결성)
***
## 삭제를 해보자
![화면 캡처 2024-07-23 111432](https://github.com/user-attachments/assets/37ef8fb6-6b9a-41bd-8380-6e40140d45d8)



참조값을 삭제하지 않아서 삭제가 안된다~~~~
***
## ON DELETE CASCADE
하지만 ON DELETE CASCADE를 달아준다면????



![화면 캡처 2024-07-23 112538](https://github.com/user-attachments/assets/03383fa6-cebe-4f09-bb9a-b5ebb7eb840e)



이렇게 부모테이블을 바로 삭제를 할 수 있다~~~~~
??? : ON DELETE CASCADE 옵션을 적용하면 부모 테이블에서 row 를 삭제할 경우 연결된 자식 테이블의 row 가 함께 삭제됩니다. 연결된 데이터를 한 번에 지울 수 있어 데이터의 관리가 편리해지고 일관성을 유지할 수 있습니다.
***
## CHECK 제약조건
![화면 캡처 2024-07-23 114821](https://github.com/user-attachments/assets/7a00cec9-9dbd-4684-82a9-54ff58b8466e)



PWD 값을 3자 이상 넣어야 된다~~



![화면 캡처 2024-07-23 114853](https://github.com/user-attachments/assets/a03e622c-fc4a-4a5a-8389-ded1fb48785d)
***
