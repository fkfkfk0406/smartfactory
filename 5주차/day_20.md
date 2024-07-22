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

## 그누보드5 미니콘솔 명함관리프로그래밍
## 풀이
```
using System.Net;
using System.Net.Sockets;
using System.Xml.Linq;
using System.Xml.Serialization;
using Oracle.ManagedDataAccess.Client;

namespace miniconsole
{
    class BusinessCard
    {
        public string name { get; set; }
        public string pnum { get; set; }
        public string email { get; set; }
        public string office { get; set; }
        public string address { get; set; }
    }
    internal class Program
    {
        static void Main(string[] args)
        {
            string strConn = "Data Source=(DESCRIPTION=" +
                "(ADDRESS_LIST=(ADDRESS=(PROTOCOL=TCP)" +
                "(HOST=localhost)(PORT=1521)))" +
                "(CONNECT_DATA=(SERVER=DEDICATED)" +
                "(SERVICE_NAME=xe)));" +
                "User Id=SCOTT;Password=TIGER;";

            OracleConnection conn = new OracleConnection(strConn);
            conn.Open();

            OracleCommand cmd = new OracleCommand();
            cmd.Connection = conn;

            //cmd.CommandText = "CREATE TABLE BusinessCards(" +
            //    "CardID NUMBER PRIMARY KEY," +
            //    "Name VARCHAR2(50) NOT NULL," +
            //    "PNUM VARCHAR2(20) NOT NULL," +
            //    "Email VARCHAR2(50)," +
            //    "OFFICE VARCHAR2(100)," +
            //    "ADDRESS VARCHAR2(200))";
            //cmd.ExecuteNonQuery();
            //cmd.Parameters.Clear();

            //cmd.CommandText =
            //   "CREATE SEQUENCE SEQ_BUSINESSCARDS" +
            //   " START WITH 1" +
            //   " INCREMENT BY 1" +
            //   " MAXVALUE 9999" +
            //   " MINVALUE 0" +
            //   " NOCYCLE" +
            //   " NOCACHE";
            //cmd.ExecuteNonQuery();
            //cmd.Parameters.Clear();

            List<BusinessCard> buisneseCards = new List<BusinessCard>();
            int choice = 0;

            do
            {
                Console.WriteLine("============================");
                Console.WriteLine("    명함   관리   시스템    ");
                Console.WriteLine("============================");
                Console.WriteLine("1. 명함 추가");
                Console.WriteLine("2. 명함 목록 보기");
                Console.WriteLine("3. 명함 수정");
                Console.WriteLine("4. 명함 삭제");
                Console.WriteLine("5. 명함 검색");
                Console.WriteLine("6. 명함 종료");
                Console.WriteLine("============================");
                Console.Write("선택 : ");
                choice = Int32.Parse(Console.ReadLine());


                switch (choice)
                {
                    case 1:
                        Console.WriteLine("\n============================");
                        Console.WriteLine("   명함     추가   ");
                        Console.WriteLine("============================\n");

                        BusinessCard BC = new BusinessCard();

                        Console.Write("이름 : ");
                        BC.name = Console.ReadLine();
                        Console.Write("전화번호 : ");
                        BC.pnum = Console.ReadLine();
                        Console.Write("이메일 : ");
                        BC.email = Console.ReadLine();
                        Console.Write("회사 : ");
                        BC.office = Console.ReadLine();
                        Console.Write("주소 : ");
                        BC.address = Console.ReadLine();

                        cmd.CommandText = "INSERT INTO BUSINESSCARDS (CARDID, NAME, PNUM, EMAIL, OFFICE, ADDRESS) VALUES (SEQ_BUSINESSCARDS.NEXTVAL, :NAME, :PNUM, :EMAIL, :OFFICE, :ADDRESS)";
                        cmd.Parameters.Add(new OracleParameter("NAME", BC.name));
                        cmd.Parameters.Add(new OracleParameter("PNUM", BC.pnum));
                        cmd.Parameters.Add(new OracleParameter("EMAIL", BC.email));
                        cmd.Parameters.Add(new OracleParameter("OFFICE", BC.office));
                        cmd.Parameters.Add(new OracleParameter("ADDRESS", BC.address));
                        cmd.ExecuteNonQuery();
                        cmd.Parameters.Clear();

                        Console.WriteLine("\n명함이 정상적으로 추가 되었습니다.\n");
                        break;
                    case 2:
                        Console.WriteLine("\n============================");
                        Console.WriteLine("   명함     목록   ");
                        Console.WriteLine("============================\n");
                        cmd.CommandText = "SELECT * FROM BUSINESSCARDS";
                        OracleDataReader reader = cmd.ExecuteReader();
                        while (reader.Read())
                        {
                            Console.WriteLine($"{reader["cardid"]}. {reader["name"]} | {reader["pnum"]} | {reader["email"]} | {reader["office"]} | {reader["address"]}");
                        }
                        reader.Close();
                        Console.WriteLine();
                        break;
                    case 3:
                        Console.WriteLine("\n============================");
                        Console.WriteLine("   명함     수정   ");
                        Console.WriteLine("============================\n");

                        reader = cmd.ExecuteReader();
                        while (reader.Read())
                        {
                            Console.WriteLine($"{reader["CARDID"]}. {reader["name"]} | {reader["pnum"]} | {reader["email"]} | {reader["office"]} | {reader["address"]}");
                        }
                        reader.Close();
                        Console.WriteLine();

                        Console.Write("수정할 명함의 번호를 입력하세요. : ");
                        int update = Int32.Parse(Console.ReadLine());
                        Console.Write("새로운 이름 : ");
                        string newname = Console.ReadLine();
                        Console.Write("새로운 전화번호 : ");
                        string newpnum = Console.ReadLine();
                        Console.Write("새로운 이메일 : ");
                        string newemail = Console.ReadLine();
                        Console.Write("새로운 회사 : ");
                        string newoffice = Console.ReadLine();
                        Console.Write("새로운 주소 : ");
                        string newaddress = Console.ReadLine();

                        cmd.CommandText = "UPDATE BUSINESSCARDS SET NAME = :NAME, PNUM = :PNUM, EMAIL = :EMAIL, OFFICE = :OFFICE, ADDRESS =  :ADDRESS WHERE CARDID = :CARDID";
                        cmd.Parameters.Clear();
                        cmd.Parameters.Add(new OracleParameter("NAME", newname));
                        cmd.Parameters.Add(new OracleParameter("PNUM", newpnum));
                        cmd.Parameters.Add(new OracleParameter("EMAIL", newemail));
                        cmd.Parameters.Add(new OracleParameter("OFFICE", newoffice));
                        cmd.Parameters.Add(new OracleParameter("ADDRESS", newaddress));
                        cmd.Parameters.Add(new OracleParameter("CARDID", update));

                        cmd.ExecuteNonQuery();
                        cmd.Parameters.Clear();
                        Console.Write("\n명함이 정상적으로 수정 되었습니다.\n");

                        break;
                    case 4:
                        Console.WriteLine("\n============================");
                        Console.WriteLine("   명함     삭제   ");
                        Console.WriteLine("============================\n");


                        reader = cmd.ExecuteReader();
                        while (reader.Read())
                        {
                            Console.WriteLine($"{reader["CARDID"]}. {reader["name"]} | {reader["pnum"]} | {reader["email"]} | {reader["office"]} | {reader["address"]}");
                        }
                        reader.Close();
                        Console.WriteLine();

                        Console.Write("삭제 하려는 명함의 번호를 입력하시오 : ");
                        int delete = Int32.Parse(Console.ReadLine());
                        cmd.CommandText = "DELETE FROM BUSINESSCARDS WHERE CARDID = :CARDID";
                        cmd.Parameters.Add(new OracleParameter("CARDID", delete));
                        cmd.ExecuteNonQuery();
                        cmd.Parameters.Clear();
                        break;

                    case 5:
                        Console.WriteLine("\n============================");
                        Console.WriteLine("   명함     검색   ");
                        Console.WriteLine("============================\n");
                        Console.Write("검색할 이름을 입력하세요. : ");
                        string sname = Console.ReadLine();
                        Console.WriteLine("\n검색 결과\n");
                        cmd.CommandText = "SELECT * FROM BUSINESSCARDS WHERE NAME LIKE :NAME";
                        cmd.Parameters.Clear();
                        cmd.Parameters.Add(new OracleParameter("NAME", "%" + sname + "%"));

                        reader = cmd.ExecuteReader();
                        while (reader.Read())
                        {
                            Console.WriteLine($"{reader["CARDID"]}. {reader["name"]} | {reader["pnum"]} | {reader["email"]} | {reader["office"]} | {reader["address"]}");
                        }
                        reader.Close();
                        Console.WriteLine();

                        break;
                    case 6:
                        Console.WriteLine("\n\n프로그램 종료\n\n");
                        break;
                    default:
                        Console.WriteLine("\n\n다시 입력하시오.\n\n");
                        break;
                }
            }
            while (choice != 6);
            conn.Close();
        }
    }
}
```
~~진짜 개힘들었다 너무 어려웠다~~
***








