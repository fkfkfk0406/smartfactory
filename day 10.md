## 오늘 오후의 간단한 코딩테스트 리뷰 및 오답노트
~~~
ㅁㄴㅇㄹㅁㄴㅇㄹ
~~~
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
