## 16일차!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
오라클을 사용해서 좀 더 자료를 검색 해봤다.

***
![화면 캡처 2024-07-16 094313](https://github.com/user-attachments/assets/74657377-25a0-43f4-9519-f5f486fb64de)
***

~~해보니까 SQLD 자격증도 따볼까 라는 생각이 들었다~~

## 11g Express SCOTT 계정 작업순서
```
[SQLPLUS]

1. scott 계정을 만들어 봅니다.

2. 권한 있는 계정 (system, sysdba)

   conn system/패스워드

3. 만들면서 패스워드는 tiger 합니다.

   CREATE USER scott IDENTIFIED BY tiger;



  잘되는지 확인 --> conn scott/tiger 성공하면 잘된 것임!!!!

4. 기초 권한주기

   GRANT CONNECT, RESOURCE TO scott;

------------------------------------------------------------------------------



[SQL Develper]

1.오라클 DB 폴더 안에 scott.sql 파일 참고합니다.

  C:\oraclexe\app\oracle\product\11.2.0\server\rdbms\admin



2. system 권한으로 아래를 실행합니다.

GRANT CONNECT,RESOURCE,UNLIMITED TABLESPACE TO SCOTT IDENTIFIED BY TIGER;

ALTER USER SCOTT DEFAULT TABLESPACE USERS;

ALTER USER SCOTT TEMPORARY TABLESPACE TEMP;



3. 테이블 내용을 삽입합니다.

DROP TABLE DEPT;

CREATE TABLE DEPT

       (DEPTNO NUMBER(2) CONSTRAINT PK_DEPT PRIMARY KEY,

	DNAME VARCHAR2(14) ,

	LOC VARCHAR2(13) ) ;

DROP TABLE EMP;

CREATE TABLE EMP

       (EMPNO NUMBER(4) CONSTRAINT PK_EMP PRIMARY KEY,

	ENAME VARCHAR2(10),

	JOB VARCHAR2(9),

	MGR NUMBER(4),

	HIREDATE DATE,

	SAL NUMBER(7,2),

	COMM NUMBER(7,2),

	DEPTNO NUMBER(2) CONSTRAINT FK_DEPTNO REFERENCES DEPT);

INSERT INTO DEPT VALUES

	(10,'ACCOUNTING','NEW YORK');

INSERT INTO DEPT VALUES (20,'RESEARCH','DALLAS');

INSERT INTO DEPT VALUES

	(30,'SALES','CHICAGO');

INSERT INTO DEPT VALUES

	(40,'OPERATIONS','BOSTON');

INSERT INTO EMP VALUES

(7369,'SMITH','CLERK',7902,to_date('17-12-1980','dd-mm-yyyy'),800,NULL,20);

INSERT INTO EMP VALUES

(7499,'ALLEN','SALESMAN',7698,to_date('20-2-1981','dd-mm-yyyy'),1600,300,30);

INSERT INTO EMP VALUES

(7521,'WARD','SALESMAN',7698,to_date('22-2-1981','dd-mm-yyyy'),1250,500,30);

INSERT INTO EMP VALUES

(7566,'JONES','MANAGER',7839,to_date('2-4-1981','dd-mm-yyyy'),2975,NULL,20);

INSERT INTO EMP VALUES

(7654,'MARTIN','SALESMAN',7698,to_date('28-9-1981','dd-mm-yyyy'),1250,1400,30);

INSERT INTO EMP VALUES

(7698,'BLAKE','MANAGER',7839,to_date('1-5-1981','dd-mm-yyyy'),2850,NULL,30);

INSERT INTO EMP VALUES

(7782,'CLARK','MANAGER',7839,to_date('9-6-1981','dd-mm-yyyy'),2450,NULL,10);

INSERT INTO EMP VALUES

(7788,'SCOTT','ANALYST',7566,to_date('13-JUL-87')-85,3000,NULL,20);

INSERT INTO EMP VALUES

(7839,'KING','PRESIDENT',NULL,to_date('17-11-1981','dd-mm-yyyy'),5000,NULL,10);

INSERT INTO EMP VALUES

(7844,'TURNER','SALESMAN',7698,to_date('8-9-1981','dd-mm-yyyy'),1500,0,30);

INSERT INTO EMP VALUES

(7876,'ADAMS','CLERK',7788,to_date('13-JUL-87')-51,1100,NULL,20);

INSERT INTO EMP VALUES

(7900,'JAMES','CLERK',7698,to_date('3-12-1981','dd-mm-yyyy'),950,NULL,30);

INSERT INTO EMP VALUES

(7902,'FORD','ANALYST',7566,to_date('3-12-1981','dd-mm-yyyy'),3000,NULL,20);

INSERT INTO EMP VALUES

(7934,'MILLER','CLERK',7782,to_date('23-1-1982','dd-mm-yyyy'),1300,NULL,10);

DROP TABLE BONUS;

CREATE TABLE BONUS

	(

	ENAME VARCHAR2(10)	,

	JOB VARCHAR2(9)  ,

	SAL NUMBER,

	COMM NUMBER

	) ;

DROP TABLE SALGRADE;

CREATE TABLE SALGRADE

      ( GRADE NUMBER,

	LOSAL NUMBER,

	HISAL NUMBER );

INSERT INTO SALGRADE VALUES (1,700,1200);

INSERT INTO SALGRADE VALUES (2,1201,1400);

INSERT INTO SALGRADE VALUES (3,1401,2000);

INSERT INTO SALGRADE VALUES (4,2001,3000);

INSERT INTO SALGRADE VALUES (5,3001,9999);

COMMIT;

```
***
![화면 캡처 2024-07-16 101330](https://github.com/user-attachments/assets/c8a6599e-2801-412a-b1f8-2ca397d5b6eb)
***

![화면 캡처 2024-07-16 101504](https://github.com/user-attachments/assets/6181388e-ff14-4c0a-a7df-332de29d93e4)
***

![화면 캡처 2024-07-16 102224](https://github.com/user-attachments/assets/677885ea-51d6-4122-a356-70d1f49647ff)
***



![화면 캡처 2024-07-16 102628](https://github.com/user-attachments/assets/c1a3d670-17ea-4e9d-9b32-e3f018064391)
***

## SCOTT 에서 예제 실습~~
***
![화면 캡처 2024-07-16 104356](https://github.com/user-attachments/assets/7ee2ca51-2e59-4d5e-980f-a7e67014f984)
***

## SQL DEVELOPER 예제 실습
```
SELECT * FROM EMP;

SELECT EMPNO, ENAME, DEPTNO FROM EMP;

-- 중복이 있는 경우
SELECT JOB, DEPTNO FROM EMP;
SELECT DISTINCT JOB, DEPTNO FROM EMP;

-- 연산식 사용하기
SELECT *  FROM EMP;
SELECT ENAME 이름, SAL 월급, SAL+SAL+SAL+COMM 분기급여 FROM EMP;

-- QUIZ
-- 이름(ENAME), 월급(SAL), 연봉(SAL*12) 검색해 보세요
SELECT ENAME 이름, SAL 월급, SAL*12 연봉 FROM EMP;
```
## QUIZ 검색결과
***
![화면 캡처 2024-07-16 112637](https://github.com/user-attachments/assets/b5cc1a24-6e6f-4087-9f79-83cbea8b3959)
***
내림차순으로 꾸며봤다. // 오름차순은 ASC
***
![화면 캡처 2024-07-16 112921](https://github.com/user-attachments/assets/8186ec4e-f02d-4487-99bd-891d58d8a2f4)
***

## 테이블을 만들어보았따.

***
![화면 캡처 2024-07-16 114538](https://github.com/user-attachments/assets/180be7dc-5271-4072-b08a-13cac3eaa0c2)
***

***
![화면 캡처 2024-07-16 133059](https://github.com/user-attachments/assets/34c91e30-6c2a-4a2c-8531-58e08986a04a)
***

## 무한 실습 !!
***
![화면 캡처 2024-07-16 134327](https://github.com/user-attachments/assets/5b620e0d-51b4-4291-bb4d-ce294f0484f6)
***

***
![화면 캡처 2024-07-16 143557](https://github.com/user-attachments/assets/57ce4000-448f-4a4d-88ad-97e13fa1ba6f)
***

***
![화면 캡처 2024-07-16 143621](https://github.com/user-attachments/assets/54a7960a-6113-445a-9f38-0cd28bafa671)
***

***
![화면 캡처 2024-07-16 144559](https://github.com/user-attachments/assets/94d11e3f-8ea4-435c-9d4b-3a64abc8890a)
***

## 기습 퀴즈

![화면 캡처 2024-07-16 144733](https://github.com/user-attachments/assets/38c3f3d4-628d-4495-ab17-5a6d6870d69f)

***

## 퀴즈 2

![화면 캡처 2024-07-16 151738](https://github.com/user-attachments/assets/6291f060-b947-482e-a04c-5f61ba4705e8)

***

## 다시 실습

![화면 캡처 2024-07-16 152103](https://github.com/user-attachments/assets/593e9d5c-1d2b-4b94-b906-14c5097a5ac4)

***

![화면 캡처 2024-07-16 152222](https://github.com/user-attachments/assets/fdcab42c-515e-41a7-bc53-c0326d483ea5)

***

![화면 캡처 2024-07-16 153552](https://github.com/user-attachments/assets/33e1d984-7a66-4062-aa1c-027f08ef1162)

***
두개가 같은거삼
![화면 캡처 2024-07-16 154432](https://github.com/user-attachments/assets/01a88dc7-a861-4a4b-97bd-b6ef6c019230)

## VISUAL STUDIO 에서 SQLDEVELOPER 머시기 해버리기
```
using Oracle.ManagedDataAccess.Client;

namespace ORACLETEST01
{
    internal class Program
    {
        static void Main(string[] args)
        {

            //1. 외부 프로그램 연결 모듈 받기 -- Nuget
            //2. 연결 스크립트를 사용
            string strConn = "Data Source=(DESCRIPTION=" +
                "(ADDRESS_LIST=(ADDRESS=(PROTOCOL=TCP)" +
                "(HOST=localhost)(PORT=1521)))" +
                "(CONNECT_DATA=(SERVER=DEDICATED)" +
                "(SERVICE_NAME=xe)));" +
                "User Id=SCOTT;Password=TIGER;";

            //1. 연결객체 만들기
            OracleConnection conn = new OracleConnection(strConn);

            //2. 연결 객체 만들기 -> client
            conn.Open();

            //3. 서버랑 놀기
            //3.1 Query 명령객체 만들기
            OracleCommand cmd = new OracleCommand();
            cmd.Connection = conn;

            //3.2 명령하기, 테이블 생성하기
            cmd.CommandText = "Create Table PhoneBook" +
                "(ID number(4) PRIMARY KEY, " +
                "NAME varchar(20), " +
                "HP varchar(20))";

            ////3.2.1 테이블 삭제하기
            //cmd.CommandText = "Drop Table PhoneBook";


            //3.3 쿼리 실행하기
            cmd.ExecuteNonQuery();


            //4. 리소스 반환 및 종료
            conn.Close();

        }
    }
}
```
정상적으로 테이블이 들어왔다가 나갔다가 한다.

***




