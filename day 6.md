## 어제 안한거 오늘 하기

```
1. for 구문
2. while
3. do ~ while
```

```
앞으로 필요할것들
1. 타자 영타 250 ~ 300 이상
2. 오타와의 싸움 (대소문자, 스펠링, 내어쓰기, 들여쓰기 (ctrl + k + f)
```

## 기습 퀴즈

```
구구단 3단을 do ~ while 문으로 작성하시오
```

## 풀이

```
namespace ConsoleApp20
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int i = 1;
            do
            {
                Console.WriteLine($"3 * {i} = {3 * i}");
                i++;
            }while ( i < 10);
        }
    }
}
```

## 기습 퀴즈 2
```
﻿-------------------------------------

[ 메뉴 선택 ]

1. 데이터베이스 입력

2. 데이터베이스 검색

3. 데이터베이스 수정

4. 데이터베이스 삭제

5. 프로그램 종료

선택 : ___



--------------------------

데이터베이스 검색을 선택하셨습니다.

--------------------------

프로그램을 종료합니다.



hint) do~while / 무한루프 이용 / switch ~ case
```

## 풀이

```
namespace ConsoleApp20
{
    internal class Program
    {
        static void Main(string[] args)
        {

            int i;

            do
            {
                
                Console.WriteLine($"[  메  뉴  선  택  ]");
                Console.WriteLine("1. 데이터베이스 입력");
                Console.WriteLine("2. 데이터베이스 검색");
                Console.WriteLine("3. 데이터베이스 수정");
                Console.WriteLine("4. 데이터베이스 삭제");
                Console.WriteLine("5. 프로그램 종료");

                Console.Write("선택 : ");
                i = Int32.Parse(Console.ReadLine());


                switch (i)
                {
                    case 1:
                        Console.WriteLine("데이터베이스 입력을 선택하셨습니다.");
                        Console.WriteLine();
                        break;
                    case 2:
                        Console.WriteLine("데이터베이스 검색을 선택하셨습니다.");
                        Console.WriteLine();
                        break;
                    case 3:
                        Console.WriteLine("데이터베이스 수정을 선택하셨습니다.");
                        Console.WriteLine();
                        break;
                    case 4:
                        Console.WriteLine("데이터베이스 삭제를 선택하셨습니다.");
                        Console.WriteLine();
                        break;
                    case 5:
                        Console.WriteLine("프로그램을 종료합니다.");
                        break;
                    default:
                        Console.WriteLine("잘못 입력 하셨습니다");
                        Console.WriteLine();
                        break;
                }
            }
            while (i != 5);
        }
    }
}
```

## 간단한 게임 만들기 퀴즈

```
namespace ConsoleApp20
{
    internal class Program
    {
        int n;
        static void Main(string[] args)
        {

            Console.WriteLine("[ 시 작 ]");
            Console.Write("플레이어의 이름을 입력하시오 : ");
            string player = Console.ReadLine();
            Thread.Sleep(1000);

            Console.WriteLine($"\n안녕하세요, 용감한 탐험가 [{player}]");
            Thread.Sleep(1000);

            Console.WriteLine("\n드디어 떠나는 모험의 첫 걸음을 내딛게 되었군요.");
            Thread.Sleep(1000);

            Console.WriteLine("먼 길을 험난한 여정을 앞두고 있지만,용기와 지혜로 모든 위기를 헤쳐나가길 바랍니다.\n\n");
            Thread.Sleep(1000);

            int n;

            do
            {
                Console.WriteLine("[  메  뉴  선  택]");
                Console.WriteLine("1. 낡은 마을 탐험");
                Console.WriteLine("2. 숲 속 오두막 방문");
                Console.WriteLine("3. 게임 종료");
                Console.Write("선택 : ");
                n = Int32.Parse(Console.ReadLine());

                switch(n)
                {
                    case 1:
                        Console.WriteLine("\n\n1. 낡은 마을 탐험 : ");
                        Thread.Sleep(500);
                        Console.WriteLine("플레이어가 낡은 마을에 도착합니다.");
                        Thread.Sleep(500);
                        Console.WriteLine("마을 주민들과 대화하고, 마을의 비밀을 파헤칠 수 있는 단서를 얻습니다.");
                        Thread.Sleep(500);
                        Console.WriteLine("마을의 문제를 해결하기 위해 퀘스트를 수행해야 할 수도 있습니다.");
                        Thread.Sleep(500);
                        Console.WriteLine("퀘스트를 완료하면 보상을 받을 수 있습니다.\n\n");
                        Thread.Sleep(500);
                        break;
                    case 2:
                        Console.WriteLine("\n\n2. 숲 속 오두막 방문 : ");
                        Thread.Sleep(500);
                        Console.WriteLine("플레이어가 숲 속 오두막에 도착합니다.");
                        Thread.Sleep(500);
                        Console.WriteLine("오두막에는 은둔하는 마법사가 살고 있습니다.");
                        Thread.Sleep(500);
                        Console.WriteLine("마법사로부터 새로운 기술을 배우거나, 아이템을 구입할 수 있습니다.");
                        Thread.Sleep(500);
                        Console.WriteLine("마법사는 플레이어의 여정에 중요한 조언을 해줄 수도 있습니다.\r\n\r");
                        Thread.Sleep(500);
                        break;
                    case 3:
                        Console.WriteLine("\r\n\r\n게임을 종료합니다.");
                        break;
                    default:
                        Console.WriteLine("숫자를 다시 입력하시오.");
                        break;
                }
            }
            while (n != 3);
        } 
    }
}
```
재밌따

***

