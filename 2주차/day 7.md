## 어제한거 복습
```
OPP(객체 지향 프로그래밍)

using System.Reflection.PortableExecutable;

namespace ConsoleApp25
{
    /*
    /* 오버로딩 ~~~~
    */
    class MyClass
    {
        public void Print()
        {
            Console.WriteLine("MyClass Hello~~!!");
        }
        public void Print(string s)
        {
            Console.WriteLine(s);
        }
        public void Print(string s, double speed)
        {
            Console.WriteLine($"{s} , speed = {speed}");
        }
        public void Print(double speed, string s)
        {
            Console.WriteLine($"speed = {speed}, {s}");
        }
    } //end of MyClass
    internal class Program
    {
        static void Print()
        {
            Console.WriteLine("Hello~~!!!");
        }
        public static void Print(string s)
        {
            Console.WriteLine(s);
        }
        static void Main(string[] args)
        {

            Print();
            Print("안녕하세요");
            MyClass mc = new MyClass();
            mc.Print();
            mc.Print("반갑습니다.");
            mc.Print("수고하세요", 100);
            mc.Print(3.14, "수고욤");
        }
    }
}
```

***

## OPP 연습 2
## 오버로딩

```
using System.Net.Http.Headers;

namespace MethodApp02
{
    class Bank
    {
        //1. 멤버 변수
        private int money;

        //2. 생성자
        public Bank()
        {
            this.money = 10000;
        }
        //3. 멤버 메소드

        //예금하다
        public void Deposite()
        {
            Console.WriteLine($"{money} 원을 예금 하다");
        }
        public void Deposite(int money)
        {
            Console.WriteLine($"{money} 원을 예금하다.");
        }
        //인출하다
        public void WithDraw()
        {
            Console.WriteLine($"{money} 원을 인출 하다");
        }
        //이체하다
        public void Transfer()
        {
            Console.WriteLine($"{money} 원을 이체 하다");
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {
            //예금하다, 인출하다, 이체하다.
            Bank kb = new Bank();
            kb.Deposite();
            kb.Deposite(1000000);
            kb.WithDraw();
            kb.Transfer();
        }
    }
}
```
```
namespace MethodApp03
{
    class Sensor
    {
        //멤버 변수
        //생성자
        //멤버 메소드

        //데이터 읽어오기
        public void ReadData()
        {
            Console.WriteLine("데이터를 읽다");
        }
        public void ReadData(byte[] data)
        {
            Console.WriteLine($"{data[0]} {data[1]} {data[2]} 데이터를 읽다");
        }
        //설정값 조정하기
        public void Calibrate()
        {
            Console.WriteLine("설정값을 조정하다");
        }
        //경고메시지 보내기
        public void SendAlert()
        {
            Console.WriteLine("경고메시지를 보내다");
        }
        public void SendAlert(string message)
        {
            Console.WriteLine($"{message} 경고 보내기");
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {

            Sensor sensor = new Sensor();
            sensor.ReadData();
            byte[] arr = { 0x001, 0x002, 0x003 };
            sensor.ReadData(arr);
            sensor.Calibrate();
            sensor.SendAlert();
            sensor.SendAlert("온도초과");
            

        }
    }
}
```

***
## 오버라이딩

## 예제
```
using System.Security.Cryptography.X509Certificates;

namespace ConsoleApp26
{
    class Computer
    {
        public void Run()
        {
            Console.WriteLine("컴퓨터를 구동하다");
        }
    }
    class NoteBook : Computer
    {
        
    }

    class Car
    {
        public string Brand;
        public Car()
        {
            Brand = "Hyundai";
            Console.WriteLine("부모 클래스 생성자가 호출 되었습니다.");
        }
        public void Run()
        {
            Console.WriteLine("차가 달린다");
        }
    }

    class SuperCar : Car
    {
        public SuperCar()
        {
            Console.WriteLine("자식 클래스 생성자가 호출 되었습니다.");
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {

            Computer computer = new Computer();
            computer.Run();

            NoteBook notebook = new NoteBook();
            notebook.Run();

            SuperCar supercar = new SuperCar();
            supercar.Run();
            Console.WriteLine(supercar.Brand);

        }
    }
}
```

```
namespace oopapp02
{
    class Shape
    {
        public string Name;
        public Shape()
        {
            this.Name = "도형";
            Console.WriteLine("부모 클래스 생성자1!!!!!!!!!!!!!!!");
        }

        public virtual void Draw()
        {
            Console.WriteLine("도형을 그리다");
        }
    }
    class Rectangle : Shape
    {
        public Rectangle()
        {
            this.Name = "사각형";
            Console.WriteLine("자식 클래스 생성자!!!!!!!!!!!!!!!!");
        }
        public override void Draw() //오버라이딩 -> 자식클래스
        {
            Console.WriteLine("사각형을 그리다");
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {
            Rectangle rect = new Rectangle();
            Console.WriteLine(rect.Name);
            Console.WriteLine(rect.Draw);
        }
    }
}
```

```
namespace ConsoleApp27
{
    abstract class Shape //추상
    {
        public virtual void Draw()
        {
            Console.WriteLine("도형을 그리다.");
        }
    }
    
    class Triangle : Shape
    {
        public override void Draw()
        {
            Console.WriteLine("삼각형을 그리다");
        }
    }
    class Circle : Shape
    {
        public override void Draw()
        {
            Console.WriteLine("원을 그리다");
        }
    }
    class Rectangle : Shape
    {
        public override void Draw()
        {
            Console.WriteLine("사각형을 그리다");
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {
            //Shape shape = new Shape();
            Triangle triangle = new Triangle();
            Circle circle = new Circle();
            Rectangle rectangle = new Rectangle();

            triangle.Draw();
            circle.Draw();
            rectangle.Draw();

        }
    }
}
```
```
namespace ConsoleApp28
{
    abstract class Mammal
    {
        public virtual void Eat() // 추상 메소드 abstract mothod
        {
            Console.WriteLine("먹습니다");
        }
    }
    class Lion : Mammal
    {
        public override void Eat()
        {
            Console.WriteLine("사자가 먹습니다.");
        }
    }
    class Tiger : Mammal
    {
        public override void Eat()
        {
            Console.WriteLine("호랑이가 먹습니다.");
        }
    }
    class Dog : Mammal
    {
        public override void Eat()
        {
            Console.WriteLine("개가 먹습니다.");
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {
            Lion lion = new Lion();
            Tiger tiger = new Tiger();
            Dog dog = new Dog();

            lion.Eat();
            tiger.Eat();
            dog.Eat();
        }
    }
}
```

```
namespace OOP06
{
    //멤버변수
   
    class Shape
    {
        private string color;
        public string Color { get; set; } //property

        public void SetColor(string color)
        {
            this.color = color;
        }

        public string GetColor()
        {
            return this.color;
        }
        public virtual void Draw()
        {
            Console.WriteLine("도형을 그리다");
        }
    }

    class Circle : Shape
    {
        public override void Draw()
        {
            Console.WriteLine("원을 그리다");
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {
            Circle circle = new Circle();

            circle.SetColor("파란색");
            Console.WriteLine(circle.GetColor());
            circle.Color = "노란색";
            Console.WriteLine(circle.Color);
        }
    }
}
```
## getter / setter 실습
```
namespace propertyApp02
{
    class Person
    {
        //멤버 변수
        private string name;
        private int age;
        public string Color { get; set; }

        //Property

        public string Name
        {
            set
            {
                name = value;
            }
            get
            {
                return name;
            }
        }
        public int Age
        {
            get
            {
                return age;
            }
            set
            {
                if(value >= 0)
                {
                    age = value;
                }
            }
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {

            Person paul = new Person();
            paul.Name = "폴이";
            paul.Age = 23;

            Console.WriteLine($"이름 : {paul.Name}, 나이: {paul.Age}");

        }
    }
}
```
## 교재 예제 실습
```
namespace P133App
{
    class Circle
    {
        private double pi = 3.14;

        public double Pi
        {
            get
            {
                return pi;
            }
            set
            {
                pi = value;
            }
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {

            Circle o = new Circle();
            o.Pi = 3.14159;         //write property

            double piValue = o.Pi; //read property
        }
    }
}
```
## QUIZ!!!
```
﻿Q) Property 만들어 사용하기

    Cat 

    {

        private string name;

        private int age;

        private string color;



	public string ShowCatInfo()

        {

             // "야옹이"의 나이는 '7'살이고 색깔은 '하얀색' 입니다. 

            return ~~~~~;

        }



     }

    ===> Propery가 적용된 클래스로 만들어 주세요.

--------------------------------------------------------------------------

Cat cat = new Cat()

//코딩

cat.ShowCatInfo()
```

## 풀이

```
namespace QUIZ04
{
    class Cat
    {
        //private string name;
        //private int age;
        //private string color;

        public string Name { get; set; }
        public int Age { get; set; }
        public string Color { get; set; }
        public string ShowCatInfo()
        {
            //"냐옹이"의 나이는 '7'살이고 색깔은 '하얀색' 입니다.
            return $"{this.Name}의 나이는 {this.Age}살이고 색깔은 {this.Color}입니다.";
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {
            Cat cat = new Cat();
            cat.Name = "냐옹이";
            cat.Age = 7;
            cat.Color = "하얀색";

            Console.WriteLine(cat.ShowCatInfo());
        }
    }
}

property를 작성하면 member는 생략해도됨.
```

***

```
[OpenSource]
Linux --> Cloud
Ubuntu -> Cloud

[DevOps]
Docker
Kubernetes
```

## DOCKER
DOCKER 설치 후에 실습을 해보았다.

```
PS C:\Users\Admin> docker images
REPOSITORY   TAG       IMAGE ID       CREATED      SIZE
ubuntu       22.04     8a3cdc4d1ad3   5 days ago   77.9MB
PS C:\Users\Admin>
PS C:\Users\Admin> docker run -it -p 80:80 8a3c /bin/bash
root@dad26d7c4696:/#
```

## docker 에서 vi 를 이용하여 코딩작업
```
root@dad26d7c4696:~# vi hello.c
root@dad26d7c4696:~# ls
hello.c
root@dad26d7c4696:~# cat hello.c
#include<stdio.h>

int main()
{
        printf("Hello World~~~!!!\n");
        return 0;
}
root@dad26d7c4696:~# ./hello
Hello World~~~!!!
```
-- docker를 사용해서 파일의 공간을 엄청 줄일수가 있따~~~!!!!! (너무 멋있다)


