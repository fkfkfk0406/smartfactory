## 오늘 오후의 간단한 코딩테스트 리뷰 및 오답노트
~~~
1. [넓이 구하기] 삼각형의 넓이를 구하는 프로그램을 작성하세요.
정수변수 width의 초기값은 20 정수형 변수 height의 초기값은 10
정수형 변수 area는 width와 height의 곱으로 생성된 넓이 입니다.
~~~
~~~
2. 정수의 합] 반복문을 이용하여 정수의 함을 구해 봅시다. 콘솔화면에 결과를 출력하세요.
1~100까지 정수의 합을 구하세요.
~~~
~~~
3. [if-else] 정수 N을 하나 입력 받는다. N은 0~100까지만 입력한다고 가정한다.
N이 100~90이면 "A학점입니다. 출력, N이 80~89 B학점입니다.
출력 N이 70~79면 C학점입니다, N이 60~69이면 D학점 그 외의 점수는 모두 "F학점입니다"로 출력하세요.
~~~
~~~
4[변수교환] 1~10000 사이의 두 정수를 입력 받아서 다음과 같이 출력하세요.
(단, 입력 받은 순서대로 변수를 출력하여야 합니다.)
~~~
~~~
5.[구구단] 9단부터 ~ 2단까지 출력 하세요.
~~~
~~~
6.[배열] 문자열을 입력을 받아 입력된 글자 중 알파벳 대문자의 개수 소문자의 개수, 특수문자의 개수, 숫자의 개수를 출력하세요.
~~~
~~~
7. 소수란 1과 자기 자신으로 나누어 떨어지는 수이다. 1~ 100 사이의 소수를 구하세요
~~~
~~~
8. 완전수를 구하세요.
완전수란 자신을 제외한 약수의 합이 자신이 되는 수를 완전수라고 합니다. 6은 완전수입니다.
6의 약수는 12 3 6 이 중 자신을 제외한 약수의 합 1+ 2+ 3= 6 즉, 6은 완전수입니다.
1000 이하의 완전수를 입력 받아 yes, no로 표현해 주세요.
~~~
~~~
9. 다음을 완성하세요. N은 50 이하의 정수만 입력됩니다.
N? 5
*
**
***
****
*****
~~~
~~~
10. 다음을 완성하세요.
N은 50 이하의 홀수만 입력됩니다.
N? 5
  *
 ***
*****
 ***
  *
~~~
~~~
11. 문자열을 입력 받아 뒤집어서 출력해주세요.
    Hello
    olleH
~~~
```
2. 배열을 선언하고 1~10까지의 랜덤한 숫자를 넣어주세요.
5개 크기의 배열을 생성하고 랜덤한 정수 10개로 채우세요. 그리고 화면에 출력하세요.
(랜덤이라 출력 숫자는 다르며 중복을 허용합니다.)
```
```
13. 값이 중복되지 않고 다음과 같이 로또 번호와 보너스 번호를 출력해 주세요.
```
```
14. 버블정렬을 구현하세요. 아래 리스트 값이 오름차순으로 정렬되게 프로그램을 완성해 주세요.
intl list = { 4, 5, 7,3, 2, 1,9,8%
리스트가 다음과 같이 주어졌습니다. 오름차순으로 구현해 주세요.
```
```
15. Shape, Triangle, Rectangle, Circle 네 클래스를 이용하여 상속구조와 오버로딩을 구현하세요.
단, Shape는 abstract 클래스로 만들어 주세요. 오버라이드 함수인 void draw0를 만들어주세요.
```
```
16.인터페이스 IWing 클래스를 만들고 void Fly0 함수가 구현되게 만들어 주세요.
말(Horse) 클래스를 부모클래스로 하는 유니콘(Unicon) 클래스를 상속과 인터페이스 구현부분을 만드세요.
```
```
17. 무한루프를 만들어 주세요. 1 ~4 메뉴의 내용은 구현할 필요는 없습니다.)
```
```
18. [달팽이 배열] 다음을 완성하시오.
```
```
19 Swap (Call by Reference)
변수 교환을 Swapint a, int b)를 만들어서 해결하세요.
C#에서 Call by Reference를 만드는 방법이 있습니다. 이를 구현하세요.
```
```
20. 절사평균 보정평균
```

***

## 오후 진도
## OOP 복습
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Runtime.InteropServices;
using System.Text;
using System.Threading.Tasks;

namespace CalculatorApp
{
    class Calculator
    {
        //멤버변수
        private double radius;
        private double pi = Math.PI;
        private int width, height;
        //생성자
        //멤버 메소드
        public double ComputeTriangleArea(int _width, int _height)
        {
            width = _width;
            height = _height;

            double result = width * height / 2.0;
            return result;

        }
        public double ComputeCircleArea(int _radius)
        {
            radius = _radius;
            double area = radius * radius * pi;

            return area;
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {

            //계산기를 꺼내서 삼각형의 넓이를 구하고싶어.
            Calculator cal = new Calculator();
            Console.Write("높이를 입력하시오. : ");
            int value1 = Int32.Parse(Console.ReadLine());
            Console.Write("넓이를 입력하시오. : ");
            int value2 = Int32.Parse(Console.ReadLine());

            double result = cal.ComputeTriangleArea(value1, value2);
            Console.WriteLine($"삼각형의 넓이 : {result}");

            //계산기를 꺼내서 원의 넓이를 구해봅시다.
            Console.Write("\n반지름을 입력하시오 : ");
            int radius = Int32.Parse(Console.ReadLine());
            result = cal.ComputeCircleArea(radius);
            Console.WriteLine("원의 넓이는 : " + result);

        }
    }
}
```
