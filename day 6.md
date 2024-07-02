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
재미따

***

## 오후 퀴즈 !

```
﻿1. 1 ~ 100까지 홀수만 출력합니다. 



2. 알파벳 A ~ Z / a ~ z 까지 출력합니다.



3. 12와 18의 최대공약수(GCD)를 구해봅니다.



4. 프로그램을 종료합니다.



선택 : 1

---------------------------------------

1 3 5 7 9 .... 99

---------------------------------------

﻿1. 1 ~ 100까지 홀수만 출력합니다. 



2. 알파벳 A ~ Z / a ~ z 까지 출력합니다.



3. 12와 18의 최대공약수(GCD)를 구해봅니다.



4. 프로그램을 종료합니다.



선택 : 2

-------------------------------------------

A B C D ... Z

a b c d ... z

--------------------------------------------

```

## 풀이

```
using System.ComponentModel;
using System.Security.Cryptography;

namespace ConsoleApp21
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int i;
            do
            {
                Console.WriteLine("\n[  문  제  ]");
                Console.WriteLine("1. 1 ~ 100까지 홀수만 출력합니다.");
                Console.WriteLine("2. 알파벳 A ~ Z / a ~ z 까지 출력합니다.");
                Console.WriteLine("3. 12와 18의 최대공약수(GCD)를 구해봅니다.");
                Console.WriteLine("4. 프로그램을 종료합니다.");
                Console.Write("선택 : ");
                i = Int32.Parse(Console.ReadLine());

                switch(i)
                {
                    case 1:
                        for(int n = 0; n <= 100; n++)
                        {
                            if (n % 2 == 1)
                                Console.Write($"{n++} ");
                        }
                        break;
                    case 2:
                        for(char ch = 'A'; ch <= 'Z'; ch++)
                        {
                            Console.Write($"{ch} ");
                        }
                        Console.WriteLine();
                        for(char ch = 'a'; ch <= 'z'; ch++)
                        {
                            Console.Write($"{ch} ");
                        }
                        break;
                    case 3:
                        int n1 = 12;
                        int n2 = 18;

                        int gcd = getgcd(n1, n2);

                        int getgcd(int a,int b)
                        {
                            if (a % b == 0)
                                return b;
                            else
                            {
                                return getgcd(b, a % b);
                            }
                        }
                        Console.WriteLine($"12와 18의 최대공약수는 : {getgcd(n1, n2)} 입니다");
                        break;
                    case 4:
                        Console.WriteLine("프로그램을 종료합니다.");
                        break;
                    default:
                        Console.WriteLine("다시 입력하시오.");
                        break;
                }
            }
            while (i < 4);
        }
    }
}
```

```
최대 공약수를 구할 때 사용한건 "유클리드 호제법" ㄷ ㄷ ㄷ ㄷ
```

## 예제 실습 코드
```
namespace ConsoleApp22
{
    class Car
    {
        //멤버 변수
        private int speed;
        public String brand;
        //생성자
        public Car()
        {
            this.speed = 0;
            this.brand = "Hyundai";
        }

        public Car(string brand)
        {
            this.speed = 100;
            this.brand = brand;
        }
        //멤버 메소드
        public string Run(int speed)
        {
            this.speed = speed;

            return this.speed + "km 속도로 달립니다.";
        }
        public string Run()
        {
            return this.speed + " km 속도로 달립니다.";
        }
        public string ShowBrand()
        {
            return "제 브랜드 명은 " + this.brand + "입니다.";
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {

            Car tony = new Car();
            Console.WriteLine(tony.ShowBrand());
            Console.WriteLine(tony.Run());
            Console.WriteLine(tony.Run(80));

            Car jack = new Car("제네시스");
            Console.WriteLine(jack.ShowBrand());
            //jack.speed = 500;
            Console.WriteLine(jack.Run(500));
            Console.WriteLine();

        }
    }
}
```

## 클래스 작성 연습 
```
class --> Cat, Dog, Person, Student, Shape, Car, Tiger, Lion ... ~~~

멤버 변수

생성자

멤버 메소드
```

## 풀이

```
using System.ComponentModel.DataAnnotations;

namespace ConsoleApp23
{
    class Cat
    {
        private string name;
        private int age;

        public Cat()
        {
            this.name = "뽀삐";
            this.age = 3;
        }
        public Cat(string name)
        {
            this.name = name;
            this.age = age;
        }
        public string Name()
        {
            return "고양이 이름은 " + this.name + " 입니다.";
        }
        public string Age(int age)
        {
            this.age = age;
            return "고양이 나이는 " + this.age + "입니다.";
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {

            Cat tom = new Cat("JOHNSON");
            Console.WriteLine(tom.Name());
            Console.WriteLine(tom.Age(30));

        }
    }
}
```
