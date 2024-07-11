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
## Delegate
```
namespace ConsoleApp54
{
    //Delegate
    //Code119

    internal class Program
    {
        //Delegate 선언
        delegate void PrintDelegate(string str);

        class Print
        {
            public void PrintOut(string str)
            {
                Console.WriteLine(str);
            }
        }
        static void Main(string[] args)
        {
            Print p = new Print();
            p.PrintOut("Hellow World~!!!");
            PrintDelegate pdg = p.PrintOut;
            pdg("안녕하세이요");
        }
    }
}
```
```
namespace DelegateApp02
{
    internal class Program
    {
        public delegate int Compute(int a, int b);
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
            public int Multiple(int a, int b)
            {
                return a * b;
            }
            public double Devide(int a, int b)
            {
                return (double)a / b; 
            }
        }
        static void Main(string[] args)
        { 
            

            int a = 100;
            int b = 200;

            Calculator cal = new Calculator();
            //Compute compute = cal.Plus;

            Func<int, int, int> intCompute = cal.Plus;
            Console.WriteLine("덧셈 : {0}", intCompute(a, b));

            intCompute = cal.Minus;
            Console.WriteLine("뺄셈 : {0}", intCompute(a, b));
        
            intCompute = cal.Multiple;
            Console.WriteLine("곱셈 : {0}",intCompute(a, b));

            Func<int, int, double> doubleCompute = cal.Devide;
            doubleCompute = cal.Devide;
            Console.WriteLine("나눗셈 : {0}", doubleCompute(a, b));
        }
    }
}
```
## WINFORM 어제 하던거 다듬기
```
using System.Text;

namespace P50Exam01
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void button1_Click(object sender, EventArgs e)
        {
            StringBuilder sb = new StringBuilder();
            sb.AppendLine("당신의 연령은");
            if (radioButton1.Checked == true)
                sb.AppendLine(radioButton1.Text);
            if (radioButton2.Checked == true)
                sb.AppendLine(radioButton2.Text);
            if (radioButton3.Checked == true)
                sb.AppendLine(radioButton3.Text);
            if (radioButton4.Checked == true)
                sb.AppendLine(radioButton4.Text);
            if (radioButton5.Checked == true)
                sb.AppendLine(radioButton5.Text);
            if (radioButton6.Checked == true)
                sb.AppendLine(radioButton6.Text);


            sb.AppendLine("\n좋아하는 색은");

            if (checkBox1.Checked == true)
                sb.AppendLine(checkBox1.Text);
            if (checkBox2.Checked == true)
                sb.AppendLine(checkBox2.Text);
            if (checkBox3.Checked == true)
                sb.AppendLine(checkBox3.Text);
            if (checkBox4.Checked == true)
                sb.AppendLine(checkBox4.Text);
            if (checkBox5.Checked == true)
                sb.AppendLine(checkBox5.Text);
            if (checkBox6.Checked == true)
                sb.AppendLine(checkBox6.Text);



            sb.Append("입니다.");
            label1.Text = sb.ToString();
        }

        private void button2_Click(object sender, EventArgs e)
        {
            Dispose();
        }
    }
}
```
## P59 예제 실습 및 퀴즈 
```
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace P59ListBoxApp
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void Form1_Load(object sender, EventArgs e)
        {
            listBox1.Items.Add("경상북도");
            listBox1.Items.Add("경상남도");
            listBox1.Items.Add("강원도");
            listBox1.Items.Add("서울특별시");
            listBox1.Items.Add("인천광역시");
            listBox1.Items.Add("부산광역시");
        }

        private void button1_Click(object sender, EventArgs e)
        {
            listBox1.Items.Add(textBox1.Text);
            textBox1.Text = "";
            textBox1.Focus();
        }

        private void button2_Click(object sender, EventArgs e)
        {
            listBox2.Items.Add(listBox1.Text);
            listBox1.Items.Remove(listBox1.Text);
        }

        private void button3_Click(object sender, EventArgs e)
        {
            listBox1.Items.Add(listBox2.Text);
            listBox2.Items.Remove(listBox2.Text);
            
        }
    }
}
```
## 실행결과

![test 59_!](https://github.com/fkfkfk0406/smartfactory/assets/91593653/c84ac393-50ac-4c87-9e19-885d8897140f)

***

## 윈폼 실습 2222@@@@

```
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace P59WINFORMAPP
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void button1_Click(object sender, EventArgs e)
        {
            textBox2.Text = textBox1.Text.Substring(0, 3);
            textBox3.Text = textBox1.Text.Substring(textBox1.Text.Length - 3, 3);
            textBox4.Text = textBox1.Text.Substring(5, 3);
            textBox5.Text = textBox1.TextLength.ToString();
        }

        private void button2_Click(object sender, EventArgs e)
        {
            Dispose();
        }

        private void button3_Click(object sender, EventArgs e)
        {
            textBox1.Clear();
            textBox1.Focus();
        }
    }
}
```

## 실행결과 

![화면 캡처 2024-07-11 162106](https://github.com/fkfkfk0406/smartfactory/assets/91593653/9988f7fd-fb77-4c70-88f5-d059f4f4ddbe)

***

## 예제 333
```
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace WindowsFormsApp2
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void button1_Click(object sender, EventArgs e)
        {

            int a = int.Parse(tbValue1.Text);
            int b = int.Parse(tbValue2.Text);
            int result = a + b;

            tbResult.Text = result.ToString(); //정수 -> 문자로

        }
    }
}
```
## 실행 결과

![화면 캡처 2024-07-11 163502](https://github.com/fkfkfk0406/smartfactory/assets/91593653/1d087f2e-cbb7-40ea-9c69-39cb52f9bc31)


