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
## 변수 = 공간
```

