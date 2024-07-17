## 17일차 ㄷㄷㄷㄷ

어제 했던 SQLDEVELOPER 실습을 다시 복습 한 다음
퀴즈도 풀어봤다. ~~어제 한건데~~

![화면 캡처 2024-07-17 095036](https://github.com/user-attachments/assets/f57b4ba3-b26d-4d78-b868-1e04d4db3d12)

***

![화면 캡처 2024-07-17 102021](https://github.com/user-attachments/assets/77019943-8241-4ff4-9357-8f37097a1360)

***
이런식으로 더 쉽게 할 수도 있따.


![화면 캡처 2024-07-17 102058](https://github.com/user-attachments/assets/013f83ef-f43a-42e0-a051-be2a2ab60d6e)

***

## 교재 예제
![화면 캡처 2024-07-17 102543](https://github.com/user-attachments/assets/5be0d86e-b61b-4d3c-b477-8565f9f429da)
***

살짝 변형


![화면 캡처 2024-07-17 102613](https://github.com/user-attachments/assets/67968c28-0e2e-47d7-9cba-05e1b7c0c93a)
***

![화면 캡처 2024-07-17 103053](https://github.com/user-attachments/assets/5160f5a9-f484-42ee-a997-fa5630f67d7d)
***
![화면 캡처 2024-07-17 103821](https://github.com/user-attachments/assets/ae61c8ff-de87-4522-bfda-7ba1de1ec414)
***
![화면 캡처 2024-07-17 103834](https://github.com/user-attachments/assets/d6f63eaa-3507-43f0-ae24-95dfad908395)
***
![화면 캡처 2024-07-17 104047](https://github.com/user-attachments/assets/d0e3f754-fe92-4644-9720-7aa052fa189e)
***
![화면 캡처 2024-07-17 104226](https://github.com/user-attachments/assets/0d862964-2cc4-4f33-a760-c1b4269c928f)
***
![화면 캡처 2024-07-17 111531](https://github.com/user-attachments/assets/717a70c3-3d0a-4079-99d1-abd8fe5c68aa)



UNION을 사용해서 DEPTNO = 10 인것과 20인 데이터를 합쳐서 출력했음. 순서나 갯수가 다르면 안돼 ~~~
***
![화면 캡처 2024-07-17 112124](https://github.com/user-attachments/assets/8064f922-f93f-40e8-9c26-157998649511)



개수가 같으면 합쳐짐 ~~~~
***

![화면 캡처 2024-07-17 112321](https://github.com/user-attachments/assets/4dd783f2-badd-4601-952b-63a4cb2c10e3)
***

![화면 캡처 2024-07-17 112504](https://github.com/user-attachments/assets/aff5fb20-1c5d-425b-b318-092f11bcca56)
***

## 교제 예제 (P125)
```
-- 1번
SELECT * FROM EMP
WHERE ENAME LIKE '%S';

-- 2번
SELECT * FROM EMP
WHERE JOB = 'SALESMAN';

-- 3-1번
SELECT * FROM EMP
WHERE SAL > 2000;

-- 3-2번
SELECT * FROM EMP
MINUS
SELECT * FROM EMP
WHERE SAL < 2000;

-- 4번
SELECT * FROM EMP
WHERE SAL >= 2000
AND SAL <= 3000;

-- 5번
SELECT * FROM EMP
WHERE ENAME LIKE '%E%'
AND DEPTNO = 30
AND SAL NOT BETWEEN 1000 AND 2000;

-- 6번
SELECT * FROM EMP
WHERE COMM IS NULL
AND JOB IN ('MANAGER', 'CLERK')
AND ENAME NOT LIKE '_L%';
```
***
![화면 캡처 2024-07-17 133110](https://github.com/user-attachments/assets/527db286-a575-45ff-b351-d65e6c6431ed)



가상으로 테이블을 만들 수도 있다.
***

![화면 캡처 2024-07-17 133241](https://github.com/user-attachments/assets/92afe95a-961a-44f5-a2db-49b49649d2bd)

***
![화면 캡처 2024-07-17 133831](https://github.com/user-attachments/assets/ceb2f40e-e145-4230-b89f-7fb9d960c450)
***
![화면 캡처 2024-07-17 134025](https://github.com/user-attachments/assets/5a82d21c-3d8f-456c-92e6-e4521e76693b)
***
![4](https://github.com/user-attachments/assets/f3e59260-638a-4949-bad7-e2c16e9a5fec)
***

## 위에 했던거 응용 퀴즈

![화면 캡처 2024-07-17 141834](https://github.com/user-attachments/assets/1313ccc4-b231-4cca-8955-445e396c2e06)



재밌다
***
## 교제 실습
![화면 캡처 2024-07-17 143004](https://github.com/user-attachments/assets/3d1ab072-92fd-466c-9154-772fde1d9a18)
***
![화면 캡처 2024-07-17 143026](https://github.com/user-attachments/assets/171a7006-26a6-4686-babf-b0b027ca61d7)
***
![화면 캡처 2024-07-17 143115](https://github.com/user-attachments/assets/2faf1216-9f18-4192-b263-2b5dba9840c9)
***
![화면 캡처 2024-07-17 143825](https://github.com/user-attachments/assets/6127ffd5-b320-4df9-95ac-02f04abffc35)
***
![화면 캡처 2024-07-17 143847](https://github.com/user-attachments/assets/91350eaf-a082-42b4-957b-05f65128269a)
***
![화면 캡처 2024-07-17 144806](https://github.com/user-attachments/assets/80f72be7-291f-4b79-a02a-707ffe8a7c88)
***
![화면 캡처 2024-07-17 144824](https://github.com/user-attachments/assets/570656b9-a13c-4a28-8673-0b1083507b46)
***
![화면 캡처 2024-07-17 145013](https://github.com/user-attachments/assets/efc2aab6-83b3-438d-b4ef-40be51203684)
***
![화면 캡처 2024-07-17 145104](https://github.com/user-attachments/assets/12f7bd07-09c5-46af-bbbf-2849632d8d5d)
***





