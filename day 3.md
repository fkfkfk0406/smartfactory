## 3일차

***

## 수업 시작하자마자 기습 실습
```
  Q) 1~100 까지의 3의배수와 7의배수만 출력하라
  EX) 3 6 9 ,,,,
      7 14 21,,,,
  HINT) 배수? % 나머지가 0 이면 해당 배수 ,,
```

## 풀이

```
namespace whileapp01
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int sum1 = 0;
            int sum2 = 0;

            for (int i = 1; i <= 100; i++)
            {
                if (i % 3 == 0)
                {
                    Console.Write($"{i} ");
                }
            }
            Console.WriteLine();
            Console.WriteLine();
            for (int i = 1; i <= 100; i++)
            {
                if (i % 7 == 0)
                {
                    Console.Write($"{i} ");
                }
            }
        }
    }
}
```
머리가 굳었나보다 ;;;; 어렵다 ㅜㅜ

***

```
1. C# --> java를 기반으로 MS에서 만든 언어
2. .Net Platform, .Net Framework
3. 코딩 - 변수와 상수(고정된 변수 ex)3.141592)
        - Type(자료형) -> int, byte, short, long, double,,,,,
        - 기본 타입
        - 사용자 정의 타입 (class)
        - 변수 교환 -> 3개의 변수 사용 !!!
        - 제어문 (if-else if-else) (switch)
        - 반복문 (for, while, do~while)
        - 함수 (Call by Value, Call by Reference)
        - 자료구조 (배열(Array))
```

***

## 예제 실습

```
Q1) for문 100 ~ 1 까지 거꾸로 출력해보세요
- 짝수만 출력
100 98 96 94 ..... 2

Q2) while문 100 ~ 1 까지 거꾸로 출력
- 홀수만 출력
99 97 95 ..... 1

```

## 풀이

```
A1)
namespace EXAMAPP01
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int sum;

            for(int i = 100; i > 0; i -= 2)
            {
                Console.Write($"{i} ");
            }

        }
    }
}

A2)
namespace EXAMAPP01
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int i = 100;

            while(i >= 0)
            {
                if (i % 2 == 1)
                    Console.Write($"{i} ");
                i--;
            }
        }
    }
}
```

***

## 중첩 IF문 문제

```
﻿성적을 입력하면 학점을 출력합니다. 



90 ~ 100 까지 A학점

80 ~ 89 까지 B학점

70 ~ 79 까지 C학점

60 ~ 69 까지 D학점

59점이하    F학점



----------------------------------------

점수 : 93

A 학점입니다.

-------------------------------------------------------

﻿점수 : 89 

B 학점입니다.

----------------------------------------

.

.

------------------------------------------

점수 : 59

F 학점입니다.
```

## 풀이

```
namespace EXAMAPP01
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.Write("점수 : ");
            int num = Int32.Parse(Console.ReadLine());


            if (90 <= num && num <= 100)
            {
                Console.WriteLine("A 학점입니다.");
            }
            else if (80 <= num && num <= 89)
            {
                Console.WriteLine("B 학점입니다.");
            }
            else if (70 <= num && num <= 79)
            {
                Console.WriteLine("C 학점입니다.");
            }
            else if (60 <= num && num <= 69)
            {
                Console.WriteLine("D 학점입니다.");
            }
            else 
            {
                Console.WriteLine("F 학점 입니다.");
            }
        }
    }
}
```
***

## switch - case 구문 예제

```
namespace EXAMAPP01
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("입력을 해주세요. (1.사과, 2.배, 3.오렌지)... : ");
            int number = int.Parse(Console.ReadLine()); 

            switch (number)
            {
                case 1:
                    Console.WriteLine("사과 입니다.");
                    break;
                case 2:
                    Console.WriteLine("배 입니다.");
                    break;
                case 3:
                    Console.WriteLine("오렌지 입니다.");
                    break;
                default:
                    Console.WriteLine("메뉴가 없습니다.");
                    break;
            }
        }
    }
}
```

***

## 심화 문제
```
[1단계]

﻿첫 번째 숫자를 입력하세요: 10 



연산자 (+, -, *, /)를 입력하세요: + 



두 번째 숫자를 입력하세요: 5 

결과는 15입니다.
```
## 풀이
```
if를 사용 했을때)

namespace EXAMAPP01
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.Write("첫 번째 숫자를 입력하세요 : ");
            int num1 = Int32.Parse(Console.ReadLine());

            Console.Write("연산자를 입력하세요 (+, -, *, /) : ");
            string math = Console.ReadLine();

            Console.Write("두 번째 숫자를 입력하세요 : ");
            int num2 = int.Parse(Console.ReadLine());

            if (math == "+")
            {
                Console.WriteLine($"결과는 {num1 + num2} 입니다.");
            }
            else if (math == "-")
            {
                Console.WriteLine($"결과는 {num1 - num2} 입니다.");
            }
            else if (math == "*")
            {
                Console.WriteLine($"결과는 {num1 * num2} 입니다.");
            }
            else if (math == "/")
            {
                Console.WriteLine($"결과는 {num1 / num2} 입니다.");
            }
                Console.Write("계산을 계속하시겠습니까? (y/n) : ");
                string re = Console.ReadLine();

            if (re == "y")
            {

            }
            else if (re == "n")
            {
                Console.Write("계산기를 종료합니다.");
            }
        }
    }
}

switch - case 를 사용 했을 때)

namespace EXAMAPP01
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.Write("첫 번째 숫자를 입력하세요 : ");
            int num1 = Int32.Parse(Console.ReadLine());

            Console.Write("연산자를 입력하세요 (+, -, *, /) : ");
            string math = Console.ReadLine();

            Console.Write("두 번째 숫자를 입력하세요 : ");
            int num2 = int.Parse(Console.ReadLine());

            switch (math)
                {
                case "+":
                    Console.WriteLine($"결과는 {num1 + num2} 입니다.");
                    break;
                case "-":
                    Console.WriteLine($"결과는 {num1 - num2} 입니다.");
                    break;
                case "*":
                    Console.WriteLine($"결과는 {num1 * num2} 입니다.");
                    break;
                case "/":
                    Console.WriteLine($"결과는 (double){num1 / num2} 입니다.");
                    break;0
            }
        }
    }
}
```
## 심화문제 2 단계
```
[2단계]

첫 번째 숫자를 입력하세요: 10 



연산자 (+, -, *, /)를 입력하세요: + 



두 번째 숫자를 입력하세요: 5 

결과는 15입니다. 



계산을 계속하시겠습니까? (y/n): y 

첫 번째 숫자를 입력하세요: 20 

연산자 (+, -, *, /)를 입력하세요: - 

두 번째 숫자를 입력하세요: 3 



결과는 17입니다. 

계산을 계속하시겠습니까? (y/n): n 

계산기를 종료합니다.
```
## 풀이
```
namespace EXAMAPP01
{
    internal class Program
    {
        static void Main(string[] args)
        {

            while (true) {

                Console.Write("첫 번째 숫자를 입력하세요 : ");
                int num1 = Int32.Parse(Console.ReadLine());

                Console.Write("연산자를 입력하세요 (+, -, *, /) : ");
                string math = Console.ReadLine();

                Console.Write("두 번째 숫자를 입력하세요 : ");
                int num2 = int.Parse(Console.ReadLine());

                if (math == "+")
                {

                    Console.WriteLine($"결과는 {num1 + num2} 입니다.");
                }
                else if (math == "-")
                {
                    Console.WriteLine($"결과는 {num1 - num2} 입니다.");
                }
                else if (math == "*")
                {
                    Console.WriteLine($"결과는 {num1 * num2} 입니다.");

                }
                else if (math == "/")
                {
                    Console.WriteLine($"결과는 {num1 / num2} 입니다.");
                }
                Console.Write("계산을 계속하시겠습니까? (y/n) : ");
                string res = Console.ReadLine();

                if (res == "n") break;
            }
            Console.WriteLine("계산기를 종료 합니다.");
        }
    }
}
```
재밌따
```
예쁘게 수정해봤다)

namespace EXAMAPP01
{
    internal class Program
    {
        static void Main(string[] args)
        {

            while (true)
            {

                Console.Write("첫 번째 숫자를 입력하세요 : ");
                int num1 = Int32.Parse(Console.ReadLine());

                Console.Write("연산자를 입력하세요 (+, -, *, /) : ");
                string math = Console.ReadLine();

                Console.Write("두 번째 숫자를 입력하세요 : ");
                int num2 = int.Parse(Console.ReadLine());

                if (math == "+")
                {

                    Console.WriteLine($"결과는 {num1 + num2} 입니다.");
                }
                else if (math == "-")
                {
                    Console.WriteLine($"결과는 {num1 - num2} 입니다.");
                }
                else if (math == "*")
                {
                    Console.WriteLine($"결과는 {num1 * num2} 입니다.");

                }
                else if (math == "/")
                {
                    Console.WriteLine($"결과는 {(double)num1 / num2} 입니다.");
                }
                while (true)
                {
                    Console.Write("계산을 계속하시겠습니까? (y/n) : ");
                    string res = Console.ReadLine().ToLower();

                    if (res == "y")
                    {
                        break;
                    }

                    else if (res == "n")
                    {
                        Console.WriteLine("계산기를 종료합니다.");
                        return;
                    }
                    else
                    {
                        Console.WriteLine("다시 입력하세요.");
                    }
                }
            }
        }
    }
}
```
혼자힘으로 하려니 어려워서 고생 좀 했다. 그래서 지피티를 조금 활용했다.

***














