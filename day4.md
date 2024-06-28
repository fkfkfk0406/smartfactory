## 4일차 (1주차의 마지막날)

***

```
함수 --> 메소드(Method)
배열(Array
```

## 예제 실습
```
namespace ConsoleApp13
{
    internal class Program
    {
        static void Main(string[] args)
        {

            int[] arr = new int[5];     //arr -- > 배열의 이름 / 배열의 선언
            // 배열의 사용법
            /*arr[0] = 1;
            arr[1] = 2;
            arr[2] = 3; 
            arr[3] = 4; 
            arr[4] = 5;*/

            for(int i =0; i< 5; i++)
            {
                arr[i] = i+1;
            }
            for(int i = 0; i< 5; i++)
            {
                Console.WriteLine(arr[i]);
            }
        }
    }
}
```

## char 사용 예제 코드

```
namespace ConsoleApp13
{
    internal class Program
    {
        static void Main(string[] args)
        {

            char ch = 'a';
            Console.WriteLine(ch);

            char[] arr = new char[3];
            arr[0] = 'a';
            arr[1] = 'b';
            arr[2] = 'c';

            for (int i = 0; i < 3; i++)
            {
                Console.Write(arr[i]);
            }

        }
    }
}

```

## 기습 단축키 설명

```
주석 ctrl + k + c
주석 해제 ctrl + k + u 
--- 편리한 단축키 !!
```

## 예제 실습

```
namespace ConsoleApp13
{
    internal class Program
    {
        static void Main(string[] args)
        {
            //크기가 5인 정수형 배열 arrint를 선언하고
            // 값은 10 20 30 40 50 을 입력해 보자.

            int[] arrint = new int[5];

            for (int i = 0; i < arrint.Length; i++)
            {
                arrint[i] = 10 * (i + 1);
                Console.WriteLine(arrint[i]);
            }
        }
    }
}

```

## mini quiz 2

```
namespace ConsoleApp13
{
    internal class Program
    {
        static void Main(string[] args)
        {
            // 크기가 3인 문자열 배열 arr을 만드세요
            // 값은 Z, Y, X 
            //화면에 요소값을 index 순서대로 출력해 보세요.


            char[] arr = new char[3];
            char ch = 'Z';

            for (int i = 0; i < arr.Length; i++)
            {
                arr[i] = ch--;
                Console.WriteLine(arr[i]);
            }

        }
    }
}
```

## mini quiz 응용

```
namespace ConsoleApp13
{
    internal class Program
    {
        static void Main(string[] args)
        {
            // 크기가 3인 문자열 배열 arr을 만드세요
            // 값은 Z, Y, X 
            //화면에 요소값을 index 순서대로 출력해 보세요.


            char[] arr = new char[26];
            char ch = 'Z';

            for (int i = 0; i < arr.Length; i++)
            {
                arr[i] = ch--;

            }
            for (int i = 0;i < arr.Length;i++)
            {
                Console.WriteLine(arr[i]);
            }

        }
    }
}
```

***

ASCII 코드,,, 이자식,,,
문자열을 배우기 시작하니 머리아픈 ASCII 코드도 설명을 들었다

***

## 퀴즈

```
정수형 배열 score를 만들고 



순서대로 국어, 영어, 수학 성적을 입력받아



총점과 평균을 출력하세요.



----------------------------------

100

100

100



총점 : 300

평균 : 100
```

## 풀이

```
namespace ConsoleApp13
{
    internal class Program
    {
        static void Main(string[] args)
        {

            int[] score = new int[3];
            int sum = 0;

            for (int i = 0; i < 3; i++)
            {

                score[i] = Int32.Parse(Console.ReadLine());
                sum += score[i];

            }

            Console.Write("총점 : ");
            Console.WriteLine($"{sum}");

            Console.Write("평균 : ");
            Console.WriteLine($"{(double)sum/3:F2}");

        }
    }
}

```

***

## QUIZ 2

```
정수형 배열 arr의 크기를 10개로 하고 



1 ~ 10까지 값을 삽입합니다.



index를 이용하여 홀수값 또는 짝수값만 출력해 봅니다.
```

## 풀이

```
namespace ConsoleApp13
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int[] numbers = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

            for (int o = 0; o < numbers.Length; o+= 2) //홀수
            {
                Console.WriteLine(numbers[o]);
            }

            Console.WriteLine();

            for (int e = 1; e < numbers.Length; e += 2) //짝수
            {
                Console.WriteLine(numbers[e]);
            }
        }
    }
}
```

## QUIZ 3

```
입력받은 문자를 거꾸로 출력 해보세요

string str = Console.ReadLine();





"ABCDEFG"

-----------------------------------

GFEDCBA

```

## 풀이

```
namespace ConsoleApp13
{
    internal class Program
    {
        static void Main(string[] args)
        {

            string str = Console.ReadLine();

            string outText = "";

            for (int i = str.Length - 1; i >= 0; i--)
            {
                outText += str[i];
            }

            Console.WriteLine(outText);

        }
    }
}
```

## for each 사용해보기

```
namespace ConsoleApp13
{
    internal class Program
    {
        static void Main(string[] args)
        {

            string[] fruits = { "사과", "복숭아", "포도"};

            for(int i = 0; i < fruits.Length; i++)
            {
                Console.WriteLine(fruits[i]);
            }

            foreach (string f in fruits)
            {
                Console.WriteLine(f);
            }

        }
    }
}
```

## 퀴즈 !

```
namespace ConsoleApp13
{
    internal class Program
    {
        static void Main(string[] args)
        {
            //1.크기가 100인 정수형 배열을 만들고 1 ~ 100 까지 초기화 하세요
            //2. 3의 배수는 배열의 요소값을 이용해서 콘솔 화면에 출력
            //3. 7의 배수는 index를 이용해서 출력해 보세요.


            int[] arr = new int[100];

            for(int i = 0; i < arr.Length; i++)
            {
                arr[i] = i + 1;
                Console.WriteLine(arr[i]);
            }

            Console.WriteLine();
            Console.WriteLine();

            for(int j =2; j < arr.Length; j+=3)
            {
                //if(arr[j]%3 == 0)
                //{
                    Console.WriteLine(arr[j]);
               // }
            }

            Console.WriteLine();
            Console.WriteLine();


            foreach (int k in arr)
            {
                if (k % 7 == 0)
                {
                    Console.WriteLine(k);
                }
            }
        }
    }
}
```

***

```
예제 코드

namespace ConsoleApp13
{
    internal class Program
    {
        static void Main(string[] args)
        {

            int[,] arr = new int[3, 3];
            int cnt = 0;
            for(int i = 0; i < 3; i++)
            {
                for(int j = 0; j < 3; j++)
                {
                    arr[i, j] = cnt++;
                }
            }

            for(int i = 0; i < 3; i++)
            {
                for(int j = 0;j < 3; j++)
                {
                    Console.Write($"{arr[i, j]}");
                }
                Console.WriteLine();
            }
        }
    }
}
```

***

## static 메소드

```
예제 코드

using System.Net.Security;

namespace method01
{
    class Program
    {
        static void NamePrint()
        {
            Console.WriteLine("라면 입니다.");
        }

        static string NamePrint2()
        {
            return "라면2 입니다.";
        }

        static void Main()
        {
           // string t = NamePrint(); //error
            string s = NamePrint2();
            Console.WriteLine(s);            
        }
    }
}

```

***

메소드를 부르면 stack 이 쌓임
프로그램이 실행되면 main 함수부터 찾아용 굉장히,, 빠른속도로,,,

***

## 예제

```
namespace quiz05
{
    internal class Calculator  
    {
        public int Multiple(int a, int b)
        {
            return a * b;
        }

        public double Divide(int a, double b)
        {
            return (double)a / b;
        }
    }
    internal class program
    {
        static void Main(string[] args)
        {

            Calculator cal = new Calculator();

            Console.WriteLine(cal.Multiple(5, 6));
            Console.WriteLine(cal.Divide(100, 5));
        }
    }
}
```

***

## 메소드 연습 2

```
국어, 영어, 수학 성적을 입력 받아 총점을 구하는 프로그램을 메소드로 만들어 봅시다. 



1. 성적을 입력받는 메소드 만들기

   조건 - return Type이 정수형 배열



2. 총점을 구하는 메소드를 작성하세요.

   조건 - return Type 정수형



----------------------------------

90

90

90



270

```

## 풀이 1 (STATIC)

```
namespace QUIZ06
{
    internal class Program
    {
        static int[] InputScore()
        {
            int[] score = new int[3];
            for(int i = 0; i < 3; i++)
            {
                score[i] = Int32.Parse(Console.ReadLine());
            }
            return score;
        }

        static int GetSum(int[] score)
        {
            int sum = 0;

            for (int i = 0; i < 3; i++)
            {
                sum += score[i];
            }

            return sum;
        }

        static void Main(string[] args)
        {
            int[] score = InputScore();
            int sum = GetSum(score);
            Console.WriteLine($"총점 : {sum}");
        }
    }
}
```

## 풀이 2 (CLASS)
```
namespace QUIZ06
{
    class Total
    {
        public int sum(int a, int b, int c)
        {
            return a + b + c;
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {
            Total total = new Total();

            Console.Write("국어 성적을 입력하세요 : ");
            int a = Int32.Parse(Console.ReadLine());

            Console.Write("영어 성적을 입력하세요 : ");
            int b = Int32.Parse(Console.ReadLine());

            Console.Write("수학 성적을 입력하세요 : ");
            int c = Int32.Parse(Console.ReadLine());

            Console.WriteLine($"총합은 {total.sum(a, b, c)}점 입니다.");
        }
    }
}
```

## 풀이 3

```
예쁘게 꾸며봤다.

using System.Numerics;

namespace QUIZ06
{
    internal class Program
    {

        static int[] InputScore()
        {
            int[] score = new int[3];
            for (int i = 0; i < 3; i++)
            {
                if (i == 0)
                {
                    Console.Write("국어 점수를 입력하시오 : ");
                }
                else if (i == 1)
                {
                    Console.Write("영어 점수를 입력하시오 : ");
                }
                else if (i == 2)
                {
                    Console.Write("수학 점수를 입력하시오 : ");
                }
                score[i] = Int32.Parse(Console.ReadLine());
            }
            return score;
        }
        static int Sum(int[] score)
        {
            int sum = 0;

            for (int i = 0; i < 3; i++)
            {
                sum += score[i];
            }
            return sum;
        }

        static double Rev(int[] score)
        {
            double rev = 0;

            for(int i = 0; i < 3;i++)
            {
                rev += score[i] / (double)score.Length;
            }
            return rev;
        }

        static void Main(string[] args)
        {
            int[] score = InputScore();

            int sum = Sum(score);
            Console.WriteLine($"총점 : {sum}");

            double rev = Rev(score);
            Console.WriteLine($"평균 : {rev:F2}");
        }
    }
}
```







