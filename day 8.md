## 어제 한 오버로딩, 오버라이딩 복습~~~~!!!!

```
namespace ConsoleApp29
{
    class Shape
    {
        public int vertex; //멤버 변수

        public Shape() //매개변수가 없고 클래스랑 이름이 같음 = 디폴트 생성자
        {
            vertex = 0;
        }

        public void ShowVertex()
        {
            Console.WriteLine(vertex);
        }
        public void ShowVertex(string msg)
        {
            Console.WriteLine(msg + " " + vertex);
        }
        public void ShowVertex(string msg, string position, int repeat)
        {
            Console.WriteLine(msg + " " + vertex + " 현재 지역은 : " + position + " 반복 횟수는 : " + repeat);
        }
        public virtual void ShowName()
        {
            Console.WriteLine("도형입니다");
        }
    }
    class Triangle : Shape
    {
        public Triangle()
        {
            vertex = 3;
        }
        public override void ShowName()
        {
            Console.WriteLine("삼각형 입니다.");
        }

    }
    class Circle : Shape
    {
        public override void ShowName()
        {
            Console.WriteLine("원 입니다.");
        }
    }

    internal class Program
    {
        static void Main(string[] args)
        {

            Triangle triangle = new Triangle();
            triangle.ShowVertex();
            triangle.ShowVertex("꼭지점의 개수는 : ");
            triangle.ShowVertex("꼭지점의 개수는 : ", "안동", 4);
            triangle.ShowName();

            Circle circle = new Circle();
            circle.ShowName();

        }
    }
}
```

***

## 기습 복습퀴즈
## 상속, 다형성을 응용하라~~~!!
```
Car

Bus : Car
Taxi : Car
Truck : Car 
---------------------------------
﻿클래스들에 적합한 메소드의 오버로딩 메소드  3개정도 
오버라이딩 메소드는 1개 이상
----------------------------------


캡슐화
다형성(Polymorphism)
오버로딩(overloading)
오버라이딩(overriding)
상속(Inheritance)
```
## 풀이
```
namespace OOPPraactice01
{
    class Car
    {
        public string brand;
        public int speed;
        public int cost;

        public void ShowBrand()
        {
            Console.WriteLine(brand);
        }

        public void Speed()
        {
            speed = 0;
        }
        public void Speed(int n1, int n2)
        {
            Console.WriteLine($"마력은 : {n1}, 최고속도는 :  {n2}");
        }
        public virtual void ShowCost()
        {
            cost = 0;
        }
    }

    class Bus : Car
    {
        public Bus()
        {
            brand = "Benz";
        }
        public override void ShowCost()
        {
            Console.WriteLine($"{3} 억 입니다.");
        }
        public void Speed()
        {
            Console.WriteLine("100km 입니다.");
        }
    }

    class Taxi : Car
    {
        public Taxi()
        {
            brand = "Lamborghini";
        }
        public override void ShowCost()
        {
            Console.WriteLine($"{5} 억 입니다.");
        }
        public void Speed()
        {
            Console.WriteLine("200km 입니다.");
        }
    }

    class Truck : Car
    {
        public Truck()
        {
            brand = "Ford";
        }
        public override void ShowCost()
        {
            Console.WriteLine($"{1} 억 입니다.");
        }
        public void Speed()
        {
            Console.WriteLine("100km 입니다.");
        }

    }
    internal class Program
    {
        static void Main(string[] args)
        {
            Bus bus = new Bus();
            bus.ShowBrand();
            bus.Speed();
            bus.Speed(100, 200);
            bus.ShowCost();

            Taxi taxi = new Taxi();
            taxi.ShowBrand();
            taxi.Speed();
            taxi.Speed(200, 300);
            taxi.ShowCost();

            Truck truck = new Truck(); 
            truck.ShowBrand();
            truck.Speed();
            truck.Speed(500, 200);
            truck.ShowCost();
        }
    }
}
```
***
## 인터페이스의 사용
## 예제 코드
```
namespace interfaceOOP
{

    //다중상속
    //유니콘~~~! 날개가 있는 말~~~!!
    class Horse
    {
        public void Run()
        {
            Console.WriteLine("말이 달립니다.");
        }
    }

    class Angel { }

    interface IWing //abstract 클래스에서 영향을 받음, interface = 상속이아니라 구현 이라고함
    {
        public void Fly(); //abstract method에서 영향을 받음

    }

    interface IWing2
    {
        public void Fly();
    }

    class Unicon : Horse, IWing
    {
        //interface의 메소드 구현
        public void Fly()
        {
            Console.WriteLine("유니콘이 날고 있습니다.");
        }
        //유니콘의 멤버메소드
        public void PerformMagic()
        {
            Console.WriteLine("유니콘이 마법을 사용합니다.");
        }
    }



    class Program
    {
        static void Main(string[] args)
        {

            Unicon jack = new Unicon();
            jack.Fly();
            jack.Run();
            jack.PerformMagic();

        }
    }
}
```
### 인터페이스 연습
```
using System.Security.Cryptography;



namespace InterfaceApp02

{
    //다중상속
    //치킨

    class Chicken
    {
        public void fried()
        {
            Console.WriteLine("기본 맛입니다");
        }
    }
    interface ISpice
    {
        public void soy();
        public void spicy();
        public void garlic();
    }
    class SoyChicken : Chicken, ISpice
    {
        public void soy()
        {
            Console.WriteLine("치킨이 간장 맛입니다.");
        }
        public void spicysoy()
        {
            Console.WriteLine("치킨이 매운 간장 맛입니다.");
        }
        public void spicy()
        {
            Console.WriteLine("치킨이 양념 맛입니다.");
        }
        public void garlic()
        {
            Console.WriteLine("치킨이 마늘 맛입니다.");
        }
    }
    class Program
    {
        static void Main(string[] args)
        {
            SoyChicken nene = new SoyChicken();
            nene.fried();
            nene.soy();
            nene.spicysoy();
            nene.spicy();
            nene.garlic();
        }
    }
}

치킨 맛있겠다.
```

***

## 오후 코딩 퀴즈
```
완전수란 자신을 제외한 약수의 합이 자신이 되는 수를 완전수라고 합니다. 6은 완전수입니다.

6의 약수는 1 2 3 6 이 중 자신을 제외한 약수의 합 1 + 2 + 3 = 6 즉, 6은 완전수입니다.

1000 이하의 완전수를 입력 받아 yes, no로 표현해 주세요.



----------------------------------------

6

yes

8

no
```

## 풀이

```
namespace ConsoleApp30
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int n = Int32.Parse(Console.ReadLine());
            int result = 0;
            for(int i = 1; i < n; i++)
            {
                if(n % i == 0)
                result += i;
            }
            if(result == n)
            {
                Console.WriteLine("yes");
            }
            else
            {
                Console.WriteLine("no");
            }
        }
    }
}
```

## 퀴즈 2
```
프로그램 명: prime
제한시간: 1 초
1 보다 큰 정수 N 가 1 과 N 자신 이외의 양의 약수를 가지지 않을 때의 N 을 소수라고 부른다.
이를테면, 2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31 등은 모두 소수이다.
4, 6, 16 등과 같이 소수가 아니면서 2 이상인 자연수를 합성수라고 정의하며,
1 은 소수도 아니고 합성수도 아닌 수이다.


1 ~ 100 사이의 소수를 구하라

--------------------------------------------------------------------------------------------------

2 3 5 7 11 13 17 19 23 29 31 37 41 43 47 53 59 61 67 71 73 79 83 89 97
```

## 풀이
```
using System;

namespace ConsoleApp32
{
    internal class Program
    {
        static void Main(string[] args)
        {
            // 소수인지 판별할 때 사용할 변수 초기화
            int answer = 0;
            
            // 2부터 99까지의 수를 확인합니다.
            for (int i = 2; i < 100; i++)
            {
                // 2부터 i-1까지의 수로 i를 나눠 봅니다.
                for (int j = 2; j < i; j++)
                {
                    // i가 j로 나누어 떨어지면 소수가 아닙니다.
                    if (i % j == 0)
                    {
                        // answer를 증가시키고 루프를 종료합니다.
                        answer++;
                        break;
                    }
                }

                // answer가 0이면 소수입니다.
                if (answer == 0)
                {
                    // 소수를 출력합니다.
                    Console.WriteLine($"{i} ");
                }
                
                // 다음 수를 확인하기 위해 answer를 0으로 초기화합니다.
                answer = 0;
            }
        }
    }
}

```
```
부울을 사용해 보았다.
using System;
using System.Diagnostics.CodeAnalysis;
using static System.Runtime.InteropServices.JavaScript.JSType;

namespace ConsoleApp32
{
    internal class Program
    {
        static void Main(string[] args)
        {
            bool flag = false;

            int answer = 0;
            for (int i = 2; i < 100; i++)
            {
                for (int j = 2; j < i; j++)
                {
                    if (i % j == 0)
                    {
                        flag = true;
                        break;
                    }
                }
                if (flag == false)
                {
                    Console.Write($"{i} ");
                }
                flag = false;
            }
        }
    }
}
```

수학이 약해서인지 이런문제는 생각하는데부터 오래 걸린다 ㅜㅜ
어렵다 슬슬 더 어려워질것이다.

***




