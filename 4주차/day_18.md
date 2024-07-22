## 18일차,,!!! ~~빠르다빨라빠르다빨라~~

어제 했던거 복습 퀴즈



![화면 캡처 2024-07-18 093259](https://github.com/user-attachments/assets/072eb58c-8a86-4004-ac07-2eda73e0a4b3)
***

## 실습 !
![화면 캡처 2024-07-18 095117](https://github.com/user-attachments/assets/3d1e17e9-9713-451f-ae93-06af1ebb1ddc)
***
케이스 문을 써보자~~~



![화면 캡처 2024-07-18 095412](https://github.com/user-attachments/assets/4cc43f22-0149-4831-ba39-5ebafaa174d7)
***

![화면 캡처 2024-07-18 111628](https://github.com/user-attachments/assets/7db119eb-61b4-4792-88d1-87c7ad8b1751)
***

## GROUP BY 실습
![화면 캡처 2024-07-18 112111](https://github.com/user-attachments/assets/fab8531a-ae3e-4840-aeba-005b9269e531)
## SAMLL QUIZ!
![화면 캡처 2024-07-18 112305](https://github.com/user-attachments/assets/a2d5d9fc-d3b9-4c26-9b8c-51f3248fbd6d)
***
## 다시 실습
![화면 캡처 2024-07-18 112730](https://github.com/user-attachments/assets/257aea6e-adf6-4cb2-9554-bd635a15f274)
***
![화면 캡처 2024-07-18 113950](https://github.com/user-attachments/assets/6b1c4df6-0049-4311-b676-fd00a3165978)
***
![화면 캡처 2024-07-18 114119](https://github.com/user-attachments/assets/b4dc6e08-2d8c-4183-91b4-2f80eeff7588)
***
![화면 캡처 2024-07-18 114210](https://github.com/user-attachments/assets/9c71ee1e-6824-4f14-9ffb-01d289c271e9)
***
![화면 캡처 2024-07-18 114725](https://github.com/user-attachments/assets/98225dff-92c2-4b33-a44d-85dedeb9bc60)
***
![화면 캡처 2024-07-18 115124](https://github.com/user-attachments/assets/cbd54fea-151d-41d8-9c32-1913dd28e439)
***

## 연습문제 풀이
```
﻿P212 연습문제

Q1) 부서별 평균급여(AVG), 최고급여(MAX),

     최저급여(MIN), 사원수(COUNT)를 

     출력해 주세요.

     단, 급여 표현 시 소수점은 제외합니다.


Q2) 같은 직종(JOB)에 종사하는 사원이  

      3명 이상인 직책과 인원수를 파악하세요.


Q3) 입사연도(HIRE_YEAR)를 기준으로

      부서별로 몇 명이 입사했는지 출력하세요.
```
## 풀이
```
-- 1번
SELECT DEPTNO,
       ROUND(AVG(SAL), 0) AS AVG_SAL,
       MAX(SAL) AS MAX_SAL,
       MIN(SAL) AS MIN_SAL,
       COUNT(*) AS CNT
FROM EMP
GROUP BY DEPTNO;
       
-- 2번
SELECT JOB, COUNT(*) FROM EMP
GROUP BY JOB
HAVING COUNT(*) >= 3;

-- 3번
SELECT TO_CHAR(HIREDATE, 'YYYY') AS HIRE_YEAR, DEPTNO,
    COUNT(*) AS  CNT
FROM EMP
GROUP BY TO_CHAR(HIREDATE, 'YYYY'), DEPTNO;
```

## QUIZZZ
```
Q) MOVIES 테이블
    1. 장르별로 영화 편수를 알려주세요.

    2. 러닝 타임 130 이상인 영화를 제목은?

    3. 2015전과 2015후 영화는 몇 편인가?
       <--2014  2015--> 

     4. 평균 러닝 타임은 얼마인가?

     5. 가장 긴 영화와 가장 러닝 타임이 짧은
        영화의 각각의 제목은? (9장 서브쿼리)
```
## 풀이
```
-- Q1)
SELECT GENRE, COUNT(*)
FROM MOVIES
GROUP BY GENRE;

-- Q2)
SELECT TITLE, RUNTIME FROM MOVIES
GROUP BY TITLE, RUNTIME
HAVING RUNTIME >= 130;

-- Q3)
SELECT SUM(
        CASE
            WHEN RELEASE_DATE < TO_DATE('2014-12-31', 'YYYY-MM-DD')
            THEN 1
            ELSE 0
        END
        ) AS "2014년이전",
        SUM( 
        CASE
            WHEN RELEASE_DATE > TO_DATE('2014-12-31', 'YYYY-MM-DD')
            THEN 1
            ELSE 0
        END
        ) AS "2015년이후"
FROM MOVIES;

-- Q4)
SELECT AVG(RUNTIME) FROM MOVIES;

-- Q5)
SELECT TITLE, RUNTIME FROM MOVIES
WHERE RUNTIME = (SELECT MIN(RUNTIME) FROM MOVIES) 
OR RUNTIME = (SELECT MAX(RUNTIME) FROM MOVIES);
```

## ROLLUP 함수 실습
![화면 캡처 2024-07-18 154003](https://github.com/user-attachments/assets/190fe4a9-26fb-4fe4-b0d4-8b87eaec4cd1)
***

## CUBE 함수 실습
![화면 캡처 2024-07-18 154058](https://github.com/user-attachments/assets/18eacffa-9550-4c67-ae08-3cf814a1dc00)
***

## PIVOT 함수 실습
![화면 캡처 2024-07-18 154851](https://github.com/user-attachments/assets/52977927-352b-4d2a-b80c-511e3ca73b1d)



으악 이게 뭐야 무슨 소리야;;;
-- PIVOT = 피봇 연산자는 행으로 나열되어 있는 데이터를 열로 나열하여 보기 쉽게 가공하는 것입니다.
-- 진짜 농구 피벗 생각하면 될듯 ㅋㅋ
***
![화면 캡처 2024-07-18 155658](https://github.com/user-attachments/assets/da0652a1-b605-4ca4-aaa3-f091b4fe8ecd)



확실한건, 코드가 주어지지않고 작성 해보라고하면 절대로 못할듯 ;;;;;;;;;;
좀 더 공부해야겠네
***

## JOIN
![화면 캡처 2024-07-18 163616](https://github.com/user-attachments/assets/70940a3e-d2bc-4e6f-aead-85a92ef77655)
***
![화면 캡처 2024-07-18 163708](https://github.com/user-attachments/assets/16ef919d-08b2-49fc-aab2-0597cdc69885)
***
![화면 캡처 2024-07-18 164147](https://github.com/user-attachments/assets/a4e52a44-8646-4e9a-b1d5-27040015ab50)



이때 나온 테이블은 실제하지 않는(파일로 존재하지 않는) 테이블임. 만들어진 테이블이다~!   
강사님曰 : JOIN 은 최소한의 정보로 뭘 만든다고 생각하면 쉽다~~~~~!   
JOIN = 여러 테이블을 하나의 테이블처럼 사용하는것이다~!   
***
![화면 캡처 2024-07-18 164947](https://github.com/user-attachments/assets/88427463-7e7b-4571-bb58-cd33cbaa4a1c)
***
## 뀌즈
![화면 캡처 2024-07-18 165651](https://github.com/user-attachments/assets/d825ba3b-7d2e-498f-b583-52d3277648b6)
***
![화면 캡처 2024-07-18 170427](https://github.com/user-attachments/assets/2de24e7a-1885-403f-a839-bccdf8b8d664)



테이블 커밋 모르고 두번 넣었더니 값이 2개가 나온다 ;;;;
***






