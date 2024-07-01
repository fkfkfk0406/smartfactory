## 5일차 (2주차 시작!!!)
***
```
저번주의 요약
- 구조적인 프로그래밍
1. [변수] 변수와 상수
2. 문법, 기술의 고도화 -> 실습, 2년 실무경험 -> 기능, (미니)프로젝트, 공동프로젝트(core)
3. 제어문 (if, else if, else, switch case)
4. 반복문 (for, while, do ~ while, foreach ... )
5. 메소드 (static, non-static / return Type, Parameter(파라미터, 매개변수, 인자값,,,)
   - 모듈화 -> 복잡도 감소, 명확한 기능, 이름이 중요(애자일!!)
```

***

```
Mordern Programming
1. 객체지향 프로그래밍 (OOP)
2. 함수형 프로그래밍.
```

***

```
Framework
- .Net Framework, .Net Core
```

***


## 아침 코딩
```
namespace ConsoleApp15
{
    internal class Program
    {
        static void Main(string[] args)
        {

            int a = Int32.Parse(Console.ReadLine());
            int b = Int32.Parse(Console.ReadLine());

            Console.WriteLine($"{a} {b}");

            //변수 교환
            int temp = a;
            a = b;
            b = temp;

            //코딩

            Console.WriteLine($"{a} {b}");

        }
    }
}

//변수 = 공간~~!!
```

***

```
뇌 풀기 코딩
namespace ConsoleApp15
{
    internal class Program
    {
        static void Main(string[] args)
        {

            double PI = 3.14159;
            char c = 'A';   //ASCII --> 65
            char d = (char)65;  

            Console.WriteLine($"{PI} {c} {d}");

            //홀수 짝수 구분
            int e = 7;
            if (e % 2 == 0)
            {
                Console.WriteLine("짝수");
            }
            else
            {
                Console.WriteLine("홀수");
            }
            //
            int s1 = 1, s2 = 2, s3 = 3;
            int value = 100;

            switch(value)
            {
                case 1:
                    Console.WriteLine(value);
                    break;
                case 2:
                    Console.WriteLine(value);
                    break;
                default:
                    Console.WriteLine(value);
                    break;
            }
        }
    }
}
```

***

```
잠깨기 미니 퀴즈
namespace ConsoleApp16
{
    internal class Program
    {
        static void Main(string[] args)
        {
            //while 문으로 77~ 700 까지 출력해보세요.
            // 77, 78, 79, ,,,, 700

            int a = 77;

            while (a <= 700)
            {
                Console.WriteLine(a);
                a++;
            }

        }
    }
}
```

***

```
사칙연산 메소드 코딩
using System.Numerics;

namespace ConsoleApp16
{
    internal class Program
    {
        static int Plus(int a, int b)
        {
            return a + b;
        }
        static int Minus(int a, int b)
        {
            return a - b;
        }
        static int Multiple(int a, int b)
        {
            return a * b;
        }
        static double Devide(int a , int b)
        {
            return (double)a / b;
        }
        static void Main(string[] args)
        {
            //사칙연산 +-/* 를 메소드로 만들어라.
            //PLUS( , ), MINUS( , ), Multiple( , ), ___Devide( , )
            //Main 메소드 1개 4칙연산 메소드 4개

            Console.WriteLine(Plus(1, 2));
            Console.WriteLine(Minus(1, 2));
            Console.WriteLine(Multiple(1, 2));
            Console.WriteLine(Devide(1, 2));
        }   
    }
}
```

***

## 메소드 연습 퀴즈

```
using System.Numerics;

namespace ConsoleApp16
{
    internal class Program
    {
        static int NumberAdd()
        {
            int result = 0;
            for (int i = 1; i <= 100; i++)
            {
                result += i;
            }
            return result;
        }
        static void Main(string[] args)
        {
            //1부터 100까지 계속 더한 결과값은 5050이다.
            //이를 메소드로 만들어서 main에서는 결과만 출력하고
            // 5050결과는 NumberAdd 메소드를 만들어서 동작시키자.

            Console.WriteLine(NumberAdd());

        } 
    } 
}
```





