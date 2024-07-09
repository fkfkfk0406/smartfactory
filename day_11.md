## 11일차 !!!!!
***
## 오전 진도
## 함수 호출 복습
```
C# 교재에 있는 예제 풀이

namespace ConsoleApp41
{
    internal class Program
    {
        static int CallByValueDemo(int x)
        {
            return x;
        }
        static void Main(string[] args)
        {

            Console.Write("정수를 입력하세요. : ");
            int inputnumber = Convert.ToInt32(Console.ReadLine());

            Console.WriteLine("입력하신 정수의 값은 {0} 입니다.", CallByValueDemo(inputnumber));
        }
    }
}
```

```
using System.ComponentModel;

namespace ConsoleApp41
{
    internal class Program
    {
        //static void GetNumbers(int x, int y)
        //{
        //    x = 0; y = 0;
        //}
        //static void GetNumbers(out int x, out int y)
        //{
        //    x = 0;
        //    y = 0;
        //}
        //static void GetNumbers(ref int x, ref int y)
        //{
        //    x = 0; y = 0;
        //}
        static void GetValue(int x)
        {
            x = 1;
        }
        static void Main(string[] args)A
        {
            //int a = int.Parse(Console.ReadLine());
            //int b = int.Parse(Console.ReadLine());
            //GetNumbers(out a, out b);
            //Console.WriteLine("a에 저장된 값은 {0}", a);
            //Console.WriteLine("b에 저장된 값은 {0}", b);

            int a = 100;
            GetValue(a);
            Console.WriteLine($"a에 저장된 값은 {a}");
        }
    }
}
```
## 재귀
```
재귀호출(recursive call)이란 함수 내부에서 자기 자신을 반복적으로 호출하는 것을 의미한다.
반복 행위를 하는 함수를 재귀함수(recursive function)라고 한다.
```
## 예제
```
namespace ConsoleApp42
{
    internal class Program
    {
        static void Recursive(int n)
        {
            Console.WriteLine(n++);
            Recursive(n);
        }
        static void Main(string[] args)
        {

            Recursive(0);

        }
    }
}
```
```
팩토리얼
namespace ConsoleApp42
{
    internal class Program
    {
        static int Factorial(int n)
        {
            if (n == 1)
            {
                return n;
            }
            else
                return n * Factorial(n - 1);
        }
        static void Main(string[] args)
        {
            int a = 10;
            Console.WriteLine(Factorial(a));
        }
    }
}
```
```
다이나믹 프로그래밍
namespace ConsoleApp43
{
    internal class Program
    {

        static long[] arr;

        static void Main(string[] args)
        { 
            //Dynamic Programming Factorial

            int n = 5;
            arr = new long[n + 1];

            arr[0] = 1;  //이 코드가 핵심!!!!

            for(int i = 1; i <= n; i++)
            {
                arr[i] = i * arr[i - 1];
            }
            Console.WriteLine(arr[n]);
        }
    }
}
```

