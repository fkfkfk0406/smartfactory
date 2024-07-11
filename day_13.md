## 객체지향 복습 !!!!
```
using System.Security.Cryptography;

namespace ConsoleApp49
{
    class Person //명사, 대문자로 시작 !
    {
        //1. 멤버 변수 (int, double, bye ,,,, )
        //private string name;
        //private int age;

        //Property
        public string Name { get; set; }
        public int Age { get; set; }


        //2. 생성자, 1개 이상
        public Person() //default 생성자
        {

        }
        public Person(string name)
        {
            Name = name;
        }
        public Person(string name, int age)
        {
            Name = name;
            Age = age;
        }
        //3. 멤버메소드
        public void Eat()
        {
            Console.WriteLine("밥을 먹습니다.");
        }
        public void Eat(string Food)
        {
            Console.WriteLine($"{Food}를 먹습니다.");
        }
        //getter, setter
        //public string GetName()
        //{
        //    return name;
        //}
        //public void SetName(string name)
        //{
        //    Name = name;
        //}
        //public int GetAge()
        //{
        //    return Age;
        //}
        //public void SetAge(int age)
        //{
        //    Age = age;
        //}
    }
    internal class Program
    {
        static void Main(string[] args)
        {

            Person tom = new Person();
            tom.Eat();
            tom.Eat("생선까스");
            //Console.WriteLine(tom.GetName());
            Console.WriteLine(tom.Name);
            Console.WriteLine(tom.Age);

            Person sam = new Person("Sam");
            //Console.WriteLine(sam.GetName());
            //Console.WriteLine(sam.GetAge());
            Console.WriteLine(sam.Name);
            Console.WriteLine(sam.Age);

            Person jake = new Person("Jake", 42);
            //Console.WriteLine(jake.GetName());
            //Console.WriteLine(jake.GetAge());
            Console.WriteLine(jake.Name);
            Console.WriteLine(jake.Age);
        }
    }
}
```
## 객체지향 학습
```
멤버변수, Property, 생성자 개수, Getter/Setter

Car -- Speed,  brand ----
------------------------------------------------
1. 멤버변수
2. 생성자 멤버개수 만큼 만들기
3. Getter/Setter 만들기
4. 멤버변수 & Getter/Setter -> Property로 대체
```
## 학습
```
using System.Xml.Linq;

namespace ConsoleApp50
{
    class Car
    {
        //1. 멤버 변수
        public string Name { get; set; }
        public int Speed { get; set; }
        public string Brand { get; set; }

        public Car(string name, int speed, string brand)
        {
            Name = name;
            Speed = speed;
            Brand = brand;
        }

        public void drive(string dest)
        {
            Console.WriteLine($"{dest}를 향해 달립니다.");
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {
            Car Ferrari = new Car("SportsCar", 400, "Ferrari");
            Console.WriteLine(Ferrari.Name);
            Console.WriteLine(Ferrari.Speed);
            Console.WriteLine(Ferrari.Brand);
            Ferrari.drive("속초");
            Console.WriteLine();

            Car Bus = new Car("Bus", 120, "Benz");
            Console.WriteLine(Bus.Name);
            Console.WriteLine(Bus.Speed);
            Console.WriteLine(Bus.Brand);
            Bus.drive("송천동");
            Console.WriteLine();

            Car JohnDeere = new Car("Tractor", 80, "John Deere");
            Console.WriteLine(JohnDeere.Name);
            Console.WriteLine(JohnDeere.Speed);
            Console.WriteLine(JohnDeere.Brand);
            JohnDeere.drive("임하");
            Console.WriteLine();
        }
    }
}
```
## Property 실습 2

```
namespace ConsoleApp51
{
    class Product
    {
        //private string name;
        //private int price;
        private int stock;



        //Property

        public string Name { get; set; }
        public int Price { get; set; }
        public int Stock
        {
            get { return stock; }
            set
            {
                if (value < 0)
                {
                    Console.WriteLine("재고가 없다니까요");
                }
                stock = value;
            }
        }
        public Product(string name, int price, int stock)
        {
            Name = name;
            Price = price;
            Stock = stock;
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {

            Product product = new Product("초코파이", 800, 10);
            product.Stock = -5;
            //Console.WriteLine(product.Name);
            //Console.WriteLine(product.Price);
            //Console.WriteLine(product.Stock);


        }
    }
}
```

***

## 인터페이스 실습
```
namespace ConsoleApp52
{
    interface IMaker
    {
        void MadWhere();
        void WareHouse();
    }
    class Korea : IMaker
    {
        public void MadWhere()
        {
            Console.WriteLine("국산 입니다.");
        }

        public void WareHouse()
        {
            Console.WriteLine("상품 등록 완료");
        }
    }
    class China : IMaker
    {
        public void MadWhere()
        {
            Console.WriteLine("중국산 입니다.");
        }

        public void WareHouse()
        {
            Console.WriteLine("상품 등록 완료");
        }
    }

    internal class Program
    {
        static void Main(string[] args)
        {
            IMaker m = new Korea();
            m.MadWhere();
            m.WareHouse();

            m = new China();
            m.MadWhere();
            m.WareHouse();
        }
    }
}
```
```
namespace interfacetest2
{
    interface IMaker
    {
        void MadeWhere();
    }
    interface IOwner
    {
        void WhoOwns();
    }
    class Korea : IMaker, IOwner
    {
        public void MadeWhere()
        {
            Console.WriteLine("국산 입니다.");
        }

        public void WhoOwns()
        {
            Console.WriteLine("대한민국 회사 제품입니다.");
        }
    }


    internal class Program
    {
        static void Main(string[] args)
        {
            IMaker km = new Korea();
            km.MadeWhere();
            //km.WhoOwns(); <-- 안보임
            IOwner ko = new Korea();
            //ko.MadeWhere(); <-- 안보임
            ko.WhoOwns();

            object obj = new Korea();
            //obj.MadeWhere(); //Access 불가 !!
            //obj.WhoOwns();    //Access 불가 !!

            Korea korea = new Korea();
            korea.MadeWhere();
            korea.WhoOwns();
        }
    }
}
```
***
## 구조체 ~~~!!!
```
namespace ConsoleApp53
{
    struct School
    {
        public string schName;
        public string stName;
        public int stGrade;

    }
    internal class Program
    {
        static void Main(string[] args)
        {

            School sc;
            sc.schName = "리버사이드 고등학교";

            Console.WriteLine(sc.schName);

        }
    }
}
```
***
