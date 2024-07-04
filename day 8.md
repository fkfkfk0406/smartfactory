## 어제 한 오버로딩, 오버라이딩 복습~~~~!!!!

```
namespace ConsoleApp29
{
    class Shape
    {
        public int vertex; //멤버 변수

        public Shape() //매개변수가 없고 클래스랑 이름이 같음 = 디폴트 생성자
        {
            vertex = 0;
        }

        public void ShowVertex()
        {
            Console.WriteLine(vertex);
        }
        public void ShowVertex(string msg)
        {
            Console.WriteLine(msg + " " + vertex);
        }
        public void ShowVertex(string msg, string position, int repeat)
        {
            Console.WriteLine(msg + " " + vertex + " 현재 지역은 : " + position + " 반복 횟수는 : " + repeat);
        }
        public virtual void ShowName()
        {
            Console.WriteLine("도형입니다");
        }
    }
    class Triangle : Shape
    {
        public Triangle()
        {
            vertex = 3;
        }
        public override void ShowName()
        {
            Console.WriteLine("삼각형 입니다.");
        }

    }
    class Circle : Shape
    {
        public override void ShowName()
        {
            Console.WriteLine("원 입니다.");
        }
    }

    internal class Program
    {
        static void Main(string[] args)
        {

            Triangle triangle = new Triangle();
            triangle.ShowVertex();
            triangle.ShowVertex("꼭지점의 개수는 : ");
            triangle.ShowVertex("꼭지점의 개수는 : ", "안동", 4);
            triangle.ShowName();

            Circle circle = new Circle();
            circle.ShowName();

        }
    }
}
```

***

## 기습 복습퀴즈
## 상속, 다형성을 응용하라~~~!!
```
Car

Bus : Car
Taxi : Car
Truck : Car 
---------------------------------
﻿클래스들에 적합한 메소드의 오버로딩 메소드  3개정도 
오버라이딩 메소드는 1개 이상
----------------------------------


캡슐화
다형성(Polymorphism)
오버로딩(overloading)
오버라이딩(overriding)
상속(Inheritance)
```
## 풀이
```
namespace OOPPraactice01
{
    class Car
    {
        public string brand;
        public int speed;
        public int cost;

        public void ShowBrand()
        {
            Console.WriteLine(brand);
        }

        public void Speed()
        {
            speed = 0;
        }
        public void Speed(int n1, int n2)
        {
            Console.WriteLine($"마력은 : {n1}, 최고속도는 :  {n2}");
        }
        public virtual void ShowCost()
        {
            cost = 0;
        }
    }

    class Bus : Car
    {
        public Bus()
        {
            brand = "Benz";
        }
        public override void ShowCost()
        {
            Console.WriteLine($"{3} 억 입니다.");
        }
        public void Speed()
        {
            Console.WriteLine("100km 입니다.");
        }
    }

    class Taxi : Car
    {
        public Taxi()
        {
            brand = "Lamborghini";
        }
        public override void ShowCost()
        {
            Console.WriteLine($"{5} 억 입니다.");
        }
        public void Speed()
        {
            Console.WriteLine("200km 입니다.");
        }
    }

    class Truck : Car
    {
        public Truck()
        {
            brand = "Ford";
        }
        public override void ShowCost()
        {
            Console.WriteLine($"{1} 억 입니다.");
        }
        public void Speed()
        {
            Console.WriteLine("100km 입니다.");
        }

    }
    internal class Program
    {
        static void Main(string[] args)
        {
            Bus bus = new Bus();
            bus.ShowBrand();
            bus.Speed();
            bus.Speed(100, 200);
            bus.ShowCost();

            Taxi taxi = new Taxi();
            taxi.ShowBrand();
            taxi.Speed();
            taxi.Speed(200, 300);
            taxi.ShowCost();

            Truck truck = new Truck(); 
            truck.ShowBrand();
            truck.Speed();
            truck.Speed(500, 200);
            truck.ShowCost();
        }
    }
}
```
