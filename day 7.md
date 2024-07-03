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



