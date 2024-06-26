## 스마트 팩토리 2일차
***
<pre>
<code>
[web]ASP --> ASP.NET Core
2018년도 부터...[Cross Platform] C# .Net Core //리눅스, 윈도우 등등 적용
               [Windows] .Net Platform //윈도우 전용
</code>
</pre>

***

<pre>
<code>
[PC] C# FrameWork --> namespace의 집합 // package의 집합
                    --> class 들의 집합
                      --> 표현하고싶은 객체 (coding)

[J2SE] JDK(Java Framework) --> 컴퓨터로 할 수 있는 모든 것. --> 학부/개인 에서 사용(Single Edition)
[J2EE] --> 기업에서 사용(Enterprise Edition)

[Android] Mobile Device Framework 
</code>
</pre>

***

https://learn.microsoft.com/en-us/dotnet/csharp/ <-- 마이크로 소프트에서 제공하는 C# 가이드이다. 유용하게 사용하자.

***

<pre>
<code>
namespace ConsoleApp7
{
    internal class Program
    {
        static void Main(string[] args)
        {
            String greeting; //변수 선언
            Console.WriteLine("이름을 입력해주세요");
            greeting = Console.ReadLine(); //값 할당, 초기화
            Console.WriteLine($"당신의 이름은 {greeting} 입니다"); //출력부
        }
    }
}
</code>
</pre>

이런것도 해봤따.

***

## MINI QUIZ!!

<pre>
  <code>
    namespace ConsoleApp8
{
    internal class Program
    {
        static void Main(string[] args)
        {
            //두 정수 value 1, value 2 를 입력받아 그 합을 출력하라.
            int result;

            Console.WriteLine("첫번째 값을 입력하시오 : ");
            int value1 = Int32.Parse(Console.ReadLine());

            Console.WriteLine("두번째 값을 입력하시오 : ");
            int value2 = Int32.Parse(Console.ReadLine());

            result = value1 + value2;

            Console.WriteLine($"값은 {result} 입니다.");
        }
    }
}
  </code>
</pre>

여러가지 방법으로 변형해서도 코드를 작성해 보았다. 아직까지도 할만하다.

***

## MINI QUIZ 2

<pre>
  <code>
    namespace quiz01
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int value1 = Int32.Parse(Console.ReadLine());
            int value2 = Int32.Parse(Console.ReadLine());   

            Console.WriteLine($"{value1} {value2}"); //100 200

            //코딩~~~
            //
            //

            Console.WriteLine($"{value1} {value2}"); //200 100
        }
    }
}  
  </code>
</pre>

## ANSWER 

<pre>
  <code>
    namespace quiz01
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int value1 = Int32.Parse(Console.ReadLine());
            int value2 = Int32.Parse(Console.ReadLine());   

            Console.WriteLine($"{value1} {value2}"); //100 200

            int temp = value1;

            value1 = value2;
            value2 = temp;

            Console.WriteLine($"{value1} {value2}"); //200 100
        }
    }
}
  </code>
</pre>

머리가 아팠다.

***

위에 링크된 마이크로소프트 C# 가이드에서 코딩연습을 해봤다.

## 예제 코드

<pre>
  <code>
    string greeting = "      Hello World!       ";
Console.WriteLine($"[{greeting}]");

string trimmedGreeting = greeting.TrimStart();
Console.WriteLine($"[{trimmedGreeting}]");

trimmedGreeting = greeting.TrimEnd();
Console.WriteLine($"[{trimmedGreeting}]");

trimmedGreeting = greeting.Trim();
Console.WriteLine($"[{trimmedGreeting}]");
  </code>
</pre>

<pre>
  <code>
    string greeting = "    안녕     ";
Console.WriteLine(greeting);

string trimmedGreeting = greeting.TrimStart();
Console.WriteLine(trimmedGreeting);

trimmedGreeting = greeting.TrimEnd();
Console.WriteLine(trimmedGreeting);

trimmedGreeting = greeting.Trim();
Console.WriteLine(trimmedGreeting);
  </code>
</pre>

## 출력

```
    안녕     
안녕     
    안녕
안녕
```

## 예제코드 2

```
string greeting = "Good Morning";

Console.WriteLine(greeting.ToUpper());

Console.WriteLine(greeting.ToLower());

```

## 출력 결과

```

GOOD MORNING
good morning

```

***

## 사칙연산 예제코드

```
int a = 18;
int b = 7;
double c = (double)a / b; //(double)은 "캐스팅" 이라고 한다. -> 소수점까지 나타내기위해 한쪽을 실수값으로 맞춤. 아니면 안나옴 ㅋ
Console.WriteLine(c);
```

## 출력 결과
```
2.5714285714285716
```

***

## 기습 퀴즈

http://www.verthasys.co.kr/ 사이트에 올라온 문제이다.

```
프로그램 명: CtoF

섭씨 온도를 화씨 온도로 변환하는 프로그램을 작성하세요.

화씨 온도 = 9 / 5 * 섭씨온도 + 32

입력
1 에서 100 사이의 자연수가 입력으로 주어진다.

출력
소수점 둘째자리까지 출력한다.

입출력 예
-----------------------------------------------------------
50

122.0  

--------------------------------------

36



96.8
```

## 풀이 및 출력

```
namespace C__TO_F_
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int cel = Int32.Parse(Console.ReadLine());
            double feh = 0.0;

            //코딩

           feh = (double)cel * 9/5 + 32;

            //출력
            Console.WriteLine($"{feh:F2}");
        }
    }
}
```

***

> C# Primitive Type
>   >byte, short, long , double, string, char, bool

이정도는 기억하기

***

## 기습 퀴즈 2

```
반지름을 입력 받으면 원넓이를 구해주는 프로그램을 작성하라.
단. 소수점 둘째자리까지만 출력하기.
단, 원주율은 Math 클래스를 사용하기.
```

### 풀이 및 코드

```
namespace C__TO_F_
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.Write("반지름의 길이를 입력하시오 : ");

            double radius;
            radius = double.Parse(Console.ReadLine());

            double area = Math.PI * radius * radius;

            Console.WriteLine($"넓이는 {area:F2} 입니다.");
        }
    }
}
```
성공,,,

***

## IF, ELSE IF, ELSE 사용해보기

```
namespace IFAPP01
{
    internal class Program
    {
        static void Main(string[] args)
        {

            int value = Int32.Parse(Console.ReadLine());
            if (value == 100)
            {
                Console.WriteLine("if 로직 실행.");
            }
            else if (value == 200)
            {
                Console.WriteLine("else if 로직 실행");
            }
            else
            {
                Console.WriteLine("else 로직 실행");
            }
        }
    }
}
```

```
namespace IFAPP01
{
    internal class Program
    {
        static void Main(string[] args)
        {

            string name = Console.ReadLine();
            if (name == "홍길동")
            {
                Console.WriteLine("1. 나는 {0} 입니다.", name);
            }
            else if (name == "이순신")
            {
                Console.WriteLine("2. 나는 {0} 입니다.", name);
            }
            else
            {
                Console.WriteLine("3. 나는 {0} 입니다", name);
            }
        }
    }
}
```

## 기습퀴즈 3 !!!!!

```
정수 1개를 입력받아 홀수 또는 짝수를 출력하라
ex) 100 -> 짝수, 200 -> 홀수
```

## 풀이 및 코드

```
namespace IFAPP01
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.Write("정수를 입력 하시오. : ");
            int num = Int32.Parse(Console.ReadLine());
            if (num%2==0)
            {
                Console.WriteLine("짝수 입니다.");
            }
            else
            {
                Console.WriteLine("홀수 입니다.");
            }
        }
    }
}
```
해냈다,,!

***

## for 문

###### ~~굉장히 만만한 "Hello, World!" 로 해보았다.~~

```
namespace ConsoleApp9
{
    internal class Program
    {
        static void Main(string[] args)
        {
            //1. 초기화조건, 2. 종료조건, 3. 증가감조건
            for (int i = 0; i < 3; i++)
            {
                Console.WriteLine("Hello, World!");
            }
        }
     }
}
```
컴파일 해보면 "Hello, World!" 가 3번 반복된다.

```
namespace ConsoleApp9
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int counter = 0;

            for (int i = 0; i < 3; i++)
            {
                counter = counter + i + 1;
            }
            Console.WriteLine(counter);
        }
     }
}
```

눈 코딩으로 코딩근육을 득근 해보았다.

***

## 기습 퀴즈 4 !!!!!!!!!!!!!!!!!!!!!!

```
1~100 까지의 합을 구하시오.
for 문으로
```

## 풀이 및 코드

```
namespace ConsoleApp9
{
    internal class Program
    {
        static void Main(string[] args)
        {
            //1 부터 100까지 합을 구해보세요, for 문으로
            int num = 0;

            for (int i = 0; i < 100; i++)
            {
                num += i + 1;
            }
            Console.WriteLine(num);
        }
     }
}
```

됐다,,

***

## 오늘의 코딩 명언 
_바다를 보지말고 물고기를 봐라,,,,,,!_

***
## While 문

```
namespace whileapp01
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int i = 0;
            int sum = 0;

            while(i <= 100)
            {
                sum += i;
                i++;
            }
            Console.WriteLine(sum);
        }
    }
}
```

위의 퀴즈 4번과 같은 문제를 while문 을 이용하여 실습해보았다.

## 오늘의 마무리 마지막 LAST 퀴즈!!!!1

```
Q) 홀수의 합 과 짝수의 합을 구하시오.
FOR, WHILE 둘 다 사용해서
출력값 홀수 -> 2500, 짝수 -> 2550
```

```
A) 짝수 (for문 사용)
namespace whileapp01
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int sum = 0;

            for(int i = 0; i <= 100; i++) 
            {
                sum += i;
                i++;
            }
            Console.WriteLine(sum);
        }
    }
}
```

```
A) 홀수 (for문 사용)
namespace whileapp01
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int sum = 0;

            for(int i = 0; i < 100; i++) 
            {
                sum += i+1;
                i++;
                Console.WriteLine(sum);
            }
            Console.WriteLine(sum);
        }
    }
}
```

```
A) 짝수 (while문 사용)

namespace whileapp01
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int i = 0;
            int sum = 0;

            while(i <= 100) 
            {
                if(i % 2 == 0)
                {
                    sum += i;
                }
                i++;
            }
            Console.WriteLine(sum);
        }
    }
}

```
```
A) 홀수 (while문 사용)

namespace whileapp01
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int i = 0;
            int sum = 0;

            while(i <= 100) 
            {
                if(i % 2 != 0)
                {
                    sum += i;
                }
                i++;
            }
            Console.WriteLine(sum);
        }
    }
}

```

for 문은 할만했으나 whie문은 이상하게도 어려웠다,,,, 군대를 다녀오니 배웠던 전공도 가물가물하다
열심히 복습하자,,,!






