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

## 메소드를 이용하여 최대, 최솟값 구하기
```
using System.Numerics;

namespace ConsoleApp16
{
    internal class Program
    {
        // Q) 배열 요소값 중 가장 큰 값을 max로 대입 후 출력하라!
        static void Main(string[] args)
        {
            int[] arr = { -7, 5, 60, -33, 42, -879 , 98};
            int max = int.MinValue;
            int min = int.MaxValue;

            for(int i = 0; i < arr.Length; i++)
            {
                if (arr[i] > max)
                {
                    max = arr[i];
                }
                if(arr[i] < min)
                {
                    min = arr[i];
                }
            }

            Console.WriteLine($"최댓값은 : {max}");
            Console.WriteLine($"최솟값은 : {min}");
        }
    } 
}
```
```
using System.ComponentModel;
using System.Numerics;
using System.Reflection.Metadata.Ecma335;

namespace ConsoleApp16
{
    internal class Program
    {
        static int GetMax(int[] arr)
        {
            int max = int.MinValue;
            for(int i = 0; i < arr.Length; i++)
            {
                if(arr[i] > max)
                    max = arr[i];
            }
            return max;
        }
        static int GetMin(int[] arr)
        {
            int min = int.MaxValue;
            for(int i = 0;i < arr.Length;i++)
            {
                if(arr[i] < min)
                    min = arr[i];
            }
            return min;
        }
        // Q) 배열 요소값 중 가장 큰 값을 max로 대입 후 출력하라!
        static void Main(string[] args)
        {
            int[] arr = { -7, 5, 60, -33, 42, -879, 98 };
            Console.WriteLine($"최댓값은 : {GetMax(arr)}");
            Console.WriteLine($"최솟값은 : {GetMin(arr)}");
        }
    } 
}
```

## 퀴즈

```
namespace ScoreApp02

{

    internal class Program

    {

        //성적 입력 함수를 만들어 주세요. 3과목

        static int[] InputThreeSocre()

        {

            int[] score = new int[3];

            //코딩

           //세 정수를 입력하는 로직

            return socre;

        }

        static int TotalScore(int[] arr)

        {

            int totalscore = 0;

//코딩

// 국어, 영어, 수학 성적을 합하는 코딩 

            return totalscore;

        }

        static double GetAvg(int totalScore)

        {

            double avg=0.0;

// 총점에서 평균값을 만드는 코딩

            return avg;

        }



        static void Main(string[] args)

        {

            //1. 세 성적 입력받기

           //2. 총점 구하기

           //3. 평균 구하기



        }

    }

}
```

## 풀이

```
namespace ConsoleApp17
{
    internal class Program
    {
        static int[] InputThreeScore()
        {
            int[] score = new int[3];

            for (int i = 0; i < 3; i++)
            {
                if(i == 0)
                {
                    Console.Write("국어 점수를 입력하시오 : ");
                }
               else if(i == 1)
                {
                    Console.Write("영어 점수를 입력하시오 : ");
                }
                else if(i == 2)
                {
                    Console.Write("수학 점수를 입력하시오 : ");
                }
                score[i] = Int32.Parse(Console.ReadLine());
            }
            return score;
        }
        static int TotalScore(int[] score)
        {
            int totalScore = 0;

            for (int i = 0; i < 3; i++)
            {
                totalScore += score[i];
            }

            return totalScore;
        }
        static double GetAvg(int totalScore)
        {
            double avg = 0.0;
            avg = totalScore / 3.0;
            return avg;
        }
        static void Main(string[] args)
        {
            int[] score = InputThreeScore();
            int totalScore = TotalScore(score);
            double avg = GetAvg(totalScore);

            Console.WriteLine($"총점 : {totalScore}");
            Console.WriteLine($"평균 : {avg:F2}");
        }
    }
}
```

## 클래스 타입 얘제 코드
```
namespace op01
{
    internal class Program
    {
        class Book
        {
            string Title;
            decimal ISBN13;
            string Contents;
            string Author;
            int PageCount;
        }

        class Student
        {
            public int ID;
            public string Name;
            public string Run()
            {
                return "학번 : " + this.ID + " " + this.Name + "달리다.";
            }
        }
        static void Main(string[] args)
        {

            Book gulliver = new Book();
            Student hong = new Student();
            // 객체 초기화 <-- 값 넣기

            hong.ID = 1;
            hong.Name = "홍길동";

            Console.WriteLine(hong.ID);
            Console.WriteLine(hong.Name);
            Console.WriteLine(hong.Run());
        }
    }
}
```

## 교재 예제 실습

```
제곱 계산기
namespace op01
{
    class Mathematics
    {
        public int f(int x)
        {
            return x * x;
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {
            Mathematics m = new Mathematics();
            int result = m.f(5);
            Console.WriteLine(result);
        }
    }
}
```

## 예쁘게 바꿔봤다.

```
namespace op01
{
    class Mathematics
    {

        //멤버 변수
        //생성자
        //멤버 메소드
        public int f(int x)
        {
            Console.Write("제곱 할 수를 입력하시오 : ");
            x = Int32.Parse(Console.ReadLine());
            return x * x;
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {
            Mathematics m = new Mathematics();
            int result = m.f(5);
            Console.WriteLine($"결과 : {result}");
        }
    }
}
```

***

## 교재 예제풀이 2

```
namespace ConsoleApp18
{
    internal class Program
    {
        class Person
        {
            string name;

            public Person()
                {
                name = "홍길동";
                Console.WriteLine("생성자 호출");
                }
        }
        static void Main(string[] args)
        {

            Console.WriteLine("person 객체 생성되기 전.");
            Person person = new Person();
            Console.WriteLine("person 객체 생성된 후.");

        }
    }
}
```

***

```
- call by value
-> 변수가 가진 값을 복사하여 전달하므로 함수 내에서 값을 변경해도 원본 값은 변경되지 않는다.


- call by reference
-> 방식에서는 함수 내에서 인자로 전달된 변수의 값을 변경하면, 호출한 쪽에서도 해당 변수의 값이 변경된다.
이는 인자로 전달되는 값이 변수의 주소이므로, 함수 내에서 변수의 값을 변경하면 해당 주소에 저장된 값이 변경되기 때문이다.
```

## CALL BY VALUE 예제 코드
```
namespace swapbyvalue
{
    internal class Program
    {
        static void Swap(int a , int b)
        {

            int temp = b;
            b = a;
            a = temp;

            Console.WriteLine($"{a} {b}");

        }                                    

        static void Main(string[] args)
        {

            int x = 3, y = 4;

            Console.WriteLine($"{x} {y}");  // result = 3, 4
            Swap(x, y);                     // result = 4, 3 후에 pop
            Console.WriteLine($"{x} {y}");  // result = 3, 4

        }
    }
}


```
## CALL BY REFERENCE 예제 코드
```
namespace swapbyvalue
{
    internal class Program
    {
        static void Swap(ref int a , ref int b) //a, b -> pointer
        {

            int temp = b;
            b = a;
            a = temp;

            Console.WriteLine($"{a} {b}");

        }                                    //변수가 값이 아닌 스택에 쌓임

        static void Main(string[] args)
        {

            int x = 3, y = 4;

            Console.WriteLine($"{x} {y}");    //result = 3, 4
            Swap(ref x, ref y);               //result = 4, 3 //ref 가 내부적으로 값을 바꿔줌 x, y 와 a, b를 연결해줌.
            Console.WriteLine($"{x} {y}");    //result = 4, 3

        }
    }
}
```

