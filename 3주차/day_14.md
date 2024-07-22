## 14일차
수업 시작하자마자 OOP 복습 !!!

```
using System.Data;
using System.Runtime.CompilerServices;

namespace ConsoleApp56
{
    class Calculator
    {
        public int Plus(int a, int b)
        {
            return a + b;
        }
        public int Minus(int a, int b)
        {
            return a - b;
        }
    }
    internal class Program
    {
        delegate int Compute(int a , int b);
        static void Main(string[] args)
        {
            Calculator calculator = new Calculator();
            //calculator.Plus(1, 2);
            Compute compute = calculator.Plus;
            Console.WriteLine(compute(5, 7));

            compute = calculator.Minus;
            Console.WriteLine(compute(5, 7));

        }
    }
}
```
## quiz
```
신고하기 위한 클래스를 만든다.
1. 경찰서에 신고하다 -> 메소드
Console.WriteLine("경찰서에 신고하다");
2. 소방서에 신고하다 -> 메소드
3. 국세청에 신고하다 -> 메소드
-----------------------------
"신고하다"라는 델리게이트를 만들어 각각 동작시켜보자
```

## 예제
```
using System.Data;
using System.Runtime.CompilerServices;

namespace ConsoleApp56
{
    class Station
    {
        public string Policestation()
        {
            return "경찰서에 신고하다";
        }
        public string Firestaion()
        {
            return "소방서에 신고하다";
        }
        public string Tax()
        {
            return "국세청에 신고하다";
        }
    }
    internal class Program
    {
        delegate string Report();
        static void Main(string[] args)
        {
            Station st = new Station();
            Report report = st.Policestation;
            Console.WriteLine(report());

            report = st.Firestaion;
            Console.WriteLine(report());

            report= st.Tax;
            Console.WriteLine(report());

        }
    }
}
```

## 배열에서 벗어나 리스트 사용해버리기
```
namespace ConsoleApp57
{
    internal class Program
    {
        static void Main(string[] args)
        {

            char[] chars = new char[3];
            chars[0] = 'A';
            chars[1] = 'B';
            chars[2] = 'C';

            List<char> chrlist = new List<char>();
            chrlist.Add('A');
            chrlist.Add('B');
            chrlist.Add('C');

            foreach (char c in chars)
            {
                Console.WriteLine(c);
            }

            List<int> intList = new List<int>();
            intList.Add(10);
            intList.Add(20);
            intList.Add(30);

            foreach(int i in intList)
            {
                Console.WriteLine(i);
            }
        }
    }
}
```
## List 연습
```
namespace ConsoleApp58
{
    internal class Program
    {
        static void Main(string[] args)
        {
            //1. 리스트를 만들고 10,20,,,50 까지 넣기, 정수형 list 이름은 numberList
            List<int> numberList = new List<int>();
            int num = 10;
            for(int i = 0; i < 5; i++)
            {
                numberList.Add(num);
                num += 10;
            }

            Console.WriteLine($"배열요소의 수 : {numberList.Count}");
            Console.WriteLine($"배열의 크기 : {numberList.Capacity}");
            numberList.RemoveAt(3); //index 제거, 전체크기가 하나 줄어듦
            numberList.Remove(20);  //값으로 제거, 전체크기 줄지않음
            numberList.Insert(0, 5);


            numberList.Sort();
            numberList.Reverse(); //값을 역순으로.

            //출력
            foreach(int i in numberList)
            {
                Console.WriteLine(i);
            }
        }
    }
}
```

## List 퀴즈
```
Q) 1~100 사이의 랜덤한 수 7개를 생성하여 정수형 list에 삽입합니다.
정렬한 다음 다시 내림차순으로 출력해 봅니다.
-------------------------------------------------
가장 첫째 값에 -7을 삽입합니다.
가장 마지막 값에 -100을 삽입합니다.
다시 출력 해 봅니다.
-------------------------------------------------
-7 값을 삭제 후 다시 출력해 봅니다.
```
## 풀이
```
namespace ConsoleApp59
{
    internal class Program
    {
        static void Main(string[] args)
        {

            List<int> numlist = new List<int>();
            Random randNum = new Random();
            int[] intList = new int[7];

            for(int i = 0; i < 7; i++)
            {
                numlist.Add(randNum.Next(1, 100));
            }
            numlist.Sort();
            numlist.Reverse();
            foreach (int i in numlist)
            {
                Console.WriteLine(i);
            }
            Console.WriteLine();
            numlist.RemoveAt(0);
            numlist.Insert(0, -7);
            numlist.Insert(7, -100); 
            foreach (int i in numlist)
            {
                Console.WriteLine(i);
            }
            Console.WriteLine();

            numlist.Remove(-7);

            foreach(int i in numlist)
            {
                Console.WriteLine(i);
            }
        }
    }
}
```

## QUIZ2
```
﻿1단계 프로그램  



ADDR_ID  NAME         HP          

1         홍길동    010-1111-1111

2         강호동    010-2222-2222

3         유재석    010-3333-3333



Java 을 이용하여 다음과 같은 프로그램을 만들어 주세요.



콘솔 메뉴를 만든 후 번호를 누르면 해당 작업을 수행하여 주세요.



------------------------------------------------------------

1. 데이터 삽입

2. 데이터 삭제

3. 데이터 조회

4. 데이터 수정



메뉴 : 1



ID를 입력해 주세요 : 1

이름을 입력해 주세요 : 홍길동

전화번호를 입력해 주세요 : 010-1111-1111



데이터가 정상적으로 입력되었습니다.

-----------------------------------------------------------------

1. 데이터 삽입

2. 데이터 삭제

3. 데이터 조회

4. 데이터 수정



메뉴 : 3 



ADDR_ID  NAME         HP         

1         홍길동    010-1111-1111
```

## 풀이
```
using System.Security.Cryptography;

namespace ListQuiz2
{
    class AdressBook
    {
        //ID
        public int Id { get; set; }
        //Name
        public string Name { get; set; }
        //Hp
        public string Hp { get; set; }
    }
    class ADDRBOOK : AdressBook
    {
        public ADDRBOOK() { }
        public ADDRBOOK(int id, string name, string hp)
        {
            Id = id;
            Name = name;
            Hp = hp;
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {

            List<AdressBook> addressBook = new List<AdressBook>();
            int choice = 0;

            do
            {
                Console.WriteLine("1. 데이터 삽입");
                Console.WriteLine("2. 데이터 삭제");
                Console.WriteLine("3. 데이터 조회");
                Console.WriteLine("4. 데이터 수정");
                Console.WriteLine("5. 종료");
                Console.Write("메뉴 : ");
                choice = Int32.Parse(Console.ReadLine());


                switch (choice)
                {
                    case 1:
                        AdressBook ab = new AdressBook();
                        Console.Write("\nID를 입력 해 주세요 : ");
                        ab.Id = Int32.Parse(Console.ReadLine());
                        Console.Write("이름을 입력 해 주세요 : ");
                        ab.Name = Console.ReadLine();
                        Console.Write("전화번호를 입력 해 주세요 : ");
                        ab.Hp = Console.ReadLine();
                        addressBook.Add(ab);
                        Console.WriteLine("\n데이터가 정상적으로 입력되었습니다.\n");
                        break;
                    case 2:
                        Console.WriteLine("\n삭제 할 데이터를 선택하시오.");
                        int delete = Int32.Parse(Console.ReadLine());
                        for(int i = 0; i < addressBook.Count; i++)
                        {
                            if(addressBook[i].Id == delete)
                            {
                                addressBook.RemoveAt(i);
                            }
                        }
                        Console.WriteLine("\n데이터가 정상적으로 삭제 되었습니다.\n");
                        break;
                    case 3:
                        Console.Write("\nADDR_ID         NAME            HP\n");
                        foreach (AdressBook address in addressBook)
                        {
                            
                            Console.WriteLine($"{address.Id}              {address.Name}      {address.Hp}");
                        }
                        Console.WriteLine();
                        break;
                    case 4:
                        Console.WriteLine("\n수정 할 데이터를 선택 하시오");
                        int update = Int32.Parse(Console.ReadLine());
                        for (int i = 0; i < addressBook.Count; i++)
                        {
                            if (addressBook[i].Id == update)
                            {
                                Console.Write("\n수정 할 ID를 입력 해 주세요 : ");
                                addressBook[i].Id = Int32.Parse(Console.ReadLine());
                                Console.Write("수정 할 이름을 입력 해 주세요 : ");
                                addressBook[i].Name = Console.ReadLine();
                                Console.Write("수정 할 전화번호를 입력 해 주세요 : ");
                                addressBook[i].Hp = Console.ReadLine();
                            }
                        }
                        Console.WriteLine("\n 데이터가 정상적으로 수정 되었습니다.\n");

                        break;
                    case 5:
                        Console.WriteLine("\n프로그램 종료");
                        break;
                    default:
                        Console.WriteLine("다시 입력하세요\n");
                        break;
                }
            }
            while (choice != 5);
        }
    }
}
```

## QUIZ 3
```
﻿유로2024 나라별 팀도 좋고



K리그도 좋습니다.



축구팀에 해당하는 클래스를 만들고 해당 멤버로 사용할 데이터 후보



5가지를 정한 다음 클래스를 만들고 다음과 같이 만들어 주세요.



1. 클럽 선수 삽입

2. 클럽 선수 삭제

3. 클럽 선수 조회

4. 클럽 선수 수정

5. 프로그램 종료



메뉴 : ____
```

## 풀이
```
namespace LISTQUIZ3
{
    class SquadMaker
    {
        public int number { get; set; }
        public string name { get; set; }
        public string position { get; set; }
        public string country { get; set; }
        public int age { get; set; }
    }
    internal class Program
    {
        static void Main(string[] args)
        {

            List<SquadMaker> squad = new List<SquadMaker>();
            int choice = 0;

            do
            {
                Console.WriteLine("----------스쿼드 메이커----------");
                Console.WriteLine("1. 스쿼드에 선수 추가");
                Console.WriteLine("2. 스쿼드에 선수 삭제");
                Console.WriteLine("3. 스쿼드 조회");
                Console.WriteLine("4. 스쿼드 수정");
                Console.WriteLine("5. 프로그램 종료");
                Console.Write("메뉴 : ");
                choice = Int32.Parse(Console.ReadLine());

                switch (choice)
                {
                    case 1:
                        SquadMaker team = new SquadMaker();
                        Console.Write("\n선수 번호를 입력하시오 : ");
                        team.number = Int32.Parse(Console.ReadLine());
                        Console.Write("선수 이름을 입력하시오 : ");
                        team.name = Console.ReadLine();
                        Console.Write("선수 포지션을 입력하시오 : ");
                        team.position = Console.ReadLine();
                        Console.Write("선수 국적을 입력하시오 : ");
                        team.country = Console.ReadLine();
                        Console.Write("선수 나이를 입력하시오 : ");
                        team.age = Int32.Parse(Console.ReadLine());
                        Console.WriteLine("\n선수가 정상적으로 추가되었습니다.\n");
                        squad.Add(team);
                        break;
                    case 2:
                        Console.WriteLine("\n스쿼드에서 삭제 할 선수의 등번호를 입력하시오");
                        Console.Write("선택 : ");
                        int delete = Int32.Parse(Console.ReadLine());
                        for(int i = 0; i < squad.Count; i++)
                        {
                            if(squad[i].number == delete)
                            {
                                squad.RemoveAt(i);
                            }
                        }
                        Console.WriteLine("\n선수가 정상적으로 삭제되었습니다.\n");
                        break;
                    case 3:
                        Console.Write("\n 등번호    이름      포지션    국적     나이 \n");
                        foreach(SquadMaker player in squad)
                        { 
                            Console.WriteLine($"   {player.number}      {player.name}      {player.position}     {player.country}   {player.age} ");
                        }
                        Console.WriteLine();
                        break;
                    case 4:
                        Console.WriteLine("\n수정 할 선수의 등번호를 선택 하시오");
                        Console.Write("선택 : ");
                        int update = Int32.Parse(Console.ReadLine());
                        for (int i = 0; i < squad.Count; i++)
                        {
                            if( squad[i].number == update)
                            {
                                Console.Write("\n수정 할 등번호를 입력해주세요 : ");
                                squad[i].number = Int32.Parse(Console.ReadLine());
                                Console.Write("수정 할 이름을 입력해주세요 : ");
                                squad[i].name = Console.ReadLine();
                                Console.Write("수정 할 포지션을 입력해주세요 : ");
                                squad[i].position = Console.ReadLine();
                                Console.Write("수정 할 국적을 입력해주세요 : ");
                                squad[i].country = Console.ReadLine();
                                Console.Write("수정 할 나이를 입력해주세요 : ");
                                squad[i].age = Int32.Parse(Console.ReadLine());
                            }
                        }
                        Console.WriteLine("\n선수가 정상적으로 수정 되었습니다.\n");
                        break;
                    case 5:
                        Console.WriteLine("\n프로그램 종료");
                        break;
                    default:
                        Console.WriteLine("숫자를 다시 입력하시오\n");
                        break;
                }
            }
            while (choice != 5);
        }
    }
}

```
