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

## DEFAULT 옵션
![화면 캡처 2024-07-23 131006](https://github.com/user-attachments/assets/055a1997-4e7c-4a27-8abb-7f155e57111a)



DEFUALT로 설정을 해주면 값을 안넣어도 된다~~~~. 디폴트가 1234로 되어있기 때문이다앗~~~~
***
![화면 캡처 2024-07-23 131559](https://github.com/user-attachments/assets/3ab154ea-9edf-4130-b20e-6a732ee81ffb)



이런식으로 지정을 해준다면 저렇게해도 데이터가 들어간다~~
***
## 권한을 넣었다 뺐다
여러권한을 한번에 부여하려면 ROLE을 만들어야함~~~~
GRANT로 권한부여 REVOKE로 권한제거~~~~



![화면 캡처 2024-07-23 135415](https://github.com/user-attachments/assets/a85e6b07-fcc3-4170-b2b2-37ee0d9508a0)
***
## 계정과 권한 함께 제거
![화면 캡처 2024-07-23 135552](https://github.com/user-attachments/assets/47861047-7927-4c49-a463-5f20fa0528a4)
***

## PL/ SQL
![화면 캡처 2024-07-23 143732](https://github.com/user-attachments/assets/76318769-ec6b-4906-9e89-90474213c4c9)

## 한줄 주석 사용하기
![화면 캡처 2024-07-23 144433](https://github.com/user-attachments/assets/92bf506b-18ad-47e1-918c-15632c18a8f8)
***

## 실습

```
Q) 부서테이블을 만들어서
DEPTNO  10
DNAME  '홍길동'
LOC    '안동'
----------------------------
변수 선언은 DECLARE에서 하고 변수값 초기화는 BEGIN에서 하세요~~~
```

## 풀이
![화면 캡처 2024-07-23 145643](https://github.com/user-attachments/assets/bf4b9e24-9bc8-453e-babc-57f99d0434e7)
***

## 실습
![화면 캡처 2024-07-23 151604](https://github.com/user-attachments/assets/334f5afd-16e3-4ffe-9af1-9f8bfb6966aa)
***
![화면 캡처 2024-07-23 151728](https://github.com/user-attachments/assets/49143a36-40b5-4407-9575-cae0be81b043)
***
![화면 캡처 2024-07-23 151759](https://github.com/user-attachments/assets/1d70169d-3004-45c7-bbd6-292ea1b621c5)
***
![화면 캡처 2024-07-23 151958](https://github.com/user-attachments/assets/ca6514b3-f344-4526-869a-bc0a51a41bfa)
***
![화면 캡처 2024-07-23 152145](https://github.com/user-attachments/assets/4ccf1d21-8a23-4e22-b26d-c4ff0760256e)
***
![화면 캡처 2024-07-23 152959](https://github.com/user-attachments/assets/2baa660f-2c2c-4f41-bb0c-e2f051cdb5c3)
***
![화면 캡처 2024-07-23 153941](https://github.com/user-attachments/assets/d0a66d96-877b-46c8-9f68-27c0ce1b2706)
***
![화면 캡처 2024-07-23 154404](https://github.com/user-attachments/assets/383f1ceb-c046-459f-b150-a981e3d1a39b)
***
![화면 캡처 2024-07-23 154426](https://github.com/user-attachments/assets/f7c94759-17cc-401f-9aee-1e225d52431e)
***
![화면 캡처 2024-07-23 154856](https://github.com/user-attachments/assets/9410fb2f-9604-4181-a5e7-074e26d9126e)
***
![화면 캡처 2024-07-23 154943](https://github.com/user-attachments/assets/f595868c-0c83-41b5-b9bb-4f6f1ff7264b)
***
![화면 캡처 2024-07-23 155543](https://github.com/user-attachments/assets/14dc1d0b-9c8d-4eb4-b574-9f9a1f845893)
***
![화면 캡처 2024-07-23 161332](https://github.com/user-attachments/assets/15e12372-6801-47b0-aad1-4ab93750693a)
***
![화면 캡처 2024-07-23 161633](https://github.com/user-attachments/assets/c8de8340-cab0-4e14-bc56-d125941c6244)
***
![화면 캡처 2024-07-23 161754](https://github.com/user-attachments/assets/fe4e40d4-0672-4f61-b570-06c573ff4aed)
***









