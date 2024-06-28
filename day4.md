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

            Console.Write("국어 성적을 입력하시오 : ");
            score[0] = Int32.Parse(Console.ReadLine());

            Console.Write("영어 성적을 입력하시오 : ");
            score[1] = Int32.Parse(Console.ReadLine());

            Console.Write("수학 성적을 입력하시오 : ");
            score[2] = Int32.Parse(Console.ReadLine());

            int sum = score[0] + score[1] + score[2];

            Console.Write("총점 : ");
            Console.WriteLine($"{sum}");

            Console.Write("평균 : ");
            Console.WriteLine($"{(double)sum/3:F2}");

        }
    }
}
```






