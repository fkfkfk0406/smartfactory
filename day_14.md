## 14일차
수업 시작하자마자 OOP 복습 !!!

```
using System.Data;
using System.Runtime.CompilerServices;

namespace ConsoleApp56
{
    class Calculator
    {
        public int Plus(int a, int b)
        {
            return a + b;
        }
        public int Minus(int a, int b)
        {
            return a - b;
        }
    }
    internal class Program
    {
        delegate int Compute(int a , int b);
        static void Main(string[] args)
        {
            Calculator calculator = new Calculator();
            //calculator.Plus(1, 2);
            Compute compute = calculator.Plus;
            Console.WriteLine(compute(5, 7));

            compute = calculator.Minus;
            Console.WriteLine(compute(5, 7));

        }
    }
}
```
## quiz
```
신고하기 위한 클래스를 만든다.
1. 경찰서에 신고하다 -> 메소드
Console.WriteLine("경찰서에 신고하다");
2. 소방서에 신고하다 -> 메소드
3. 국세청에 신고하다 -> 메소드
-----------------------------
"신고하다"라는 델리게이트를 만들어 각각 동작시켜보자
```

## 예제
```
using System.Data;
using System.Runtime.CompilerServices;

namespace ConsoleApp56
{
    class Station
    {
        public string Policestation()
        {
            return "경찰서에 신고하다";
        }
        public string Firestaion()
        {
            return "소방서에 신고하다";
        }
        public string Tax()
        {
            return "국세청에 신고하다";
        }
    }
    internal class Program
    {
        delegate string Report();
        static void Main(string[] args)
        {
            Station st = new Station();
            Report report = st.Policestation;
            Console.WriteLine(report());

            report = st.Firestaion;
            Console.WriteLine(report());

            report= st.Tax;
            Console.WriteLine(report());

        }
    }
}
```

## 배열에서 벗어나 리스트 사용해버리기
```
namespace ConsoleApp57
{
    internal class Program
    {
        static void Main(string[] args)
        {

            char[] chars = new char[3];
            chars[0] = 'A';
            chars[1] = 'B';
            chars[2] = 'C';

            List<char> chrlist = new List<char>();
            chrlist.Add('A');
            chrlist.Add('B');
            chrlist.Add('C');

            foreach (char c in chars)
            {
                Console.WriteLine(c);
            }

            List<int> intList = new List<int>();
            intList.Add(10);
            intList.Add(20);
            intList.Add(30);

            foreach(int i in intList)
            {
                Console.WriteLine(i);
            }
        }
    }
}
```
## List 연습
```
namespace ConsoleApp58
{
    internal class Program
    {
        static void Main(string[] args)
        {
            //1. 리스트를 만들고 10,20,,,50 까지 넣기, 정수형 list 이름은 numberList
            List<int> numberList = new List<int>();
            int num = 10;
            for(int i = 0; i < 5; i++)
            {
                numberList.Add(num);
                num += 10;
            }

            Console.WriteLine($"배열요소의 수 : {numberList.Count}");
            Console.WriteLine($"배열의 크기 : {numberList.Capacity}");
            numberList.RemoveAt(3); //index 제거, 전체크기가 하나 줄어듦
            numberList.Remove(20);  //값으로 제거, 전체크기 줄지않음
            numberList.Insert(0, 5);


            numberList.Sort();
            numberList.Reverse(); //값을 역순으로.

            //출력
            foreach(int i in numberList)
            {
                Console.WriteLine(i);
            }
        }
    }
}
```

## List 퀴즈
```
Q) 1~100 사이의 랜덤한 수 7개를 생성하여 정수형 list에 삽입합니다.
정렬한 다음 다시 내림차순으로 출력해 봅니다.
-------------------------------------------------
가장 첫째 값에 -7을 삽입합니다.
가장 마지막 값에 -100을 삽입합니다.
다시 출력 해 봅니다.
-------------------------------------------------
-7 값을 삭제 후 다시 출력해 봅니다.
```
## 풀이
```

```

