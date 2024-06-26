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

'''
    안녕     
안녕     
    안녕
안녕
'''

신기했다.
