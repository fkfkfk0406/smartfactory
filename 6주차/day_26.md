## 26일차~
```
OOP
1. 캡슐화 (Encapsulation)
  - 객체(OBJECT) -> 인스턴스(INSTANCE)
  - 객체를 만드는것 클래스(CLASS)
    -클래스의 구성
    - clas Lion
    - { 멤버변수 -- 속성, 변수 -> 명사
    -   멤버메소드 -- 액션, 메소드 -> 동사
    -   -생성자도 멤버 메소드에 속한다.
    - }

2. 다형성 (Polymorphism)
  - 오버로딩 (생성자 만들기 패턴?)
  - 오버라이딩 --> ToString? --> 메소드 재정의!!
              --> Shape     --> Draw() 메소드 생각!!

3. 상속(Inheritance)
  - 상속 하기 위한 키워드(:)
  - : object 최종 부모클래스 상속은 표현이 생략가능

  - Is - A 관계, Has - A 관계(??)

4. Wrapper Class
  - Boxing, UnBoxing

  -> char, float 기본타입에 대한 Wrapper Class를 이용해 값을 서로 교환해 봅시다.
      int number = 42; //값 타입, 기본타입
      Int32 boxed = number // WrapperClass(Int32)
                          // Boxing
      int unboxed = boxed // Unboxing

      object obj = number // UpCasting
      int downed = (int)obj // DownCasting

5. String 복습
  - StringBuilder 복습

6. 인터페이스(Interface), 추상 클래스(Abstract Class)
  - 추살 클래스는 개념적으로만 존재

7. 깊은복사(Deep Copy), 얇은 복사(Shallow Copy)
```

## StringBuilder 실습
```

using System.Text;

public partial class Program
{
    public static void Main()
    {
        string str1 = "Hello World";
        string str2 = new string("Hello World");
        string str3 = "Hello World";
        string str4 = "Hello World";
        string str5 = new string("Hello World");

        object obj1 = new object();
        object obj2 = new object();

        StringBuilder sb1 = new StringBuilder("Hello World");
        StringBuilder sb2 = new StringBuilder("Hello World");

        Console.WriteLine($"str1 : {str1.GetHashCode()}");
        Console.WriteLine($"str2 : {str2.GetHashCode()}");
        Console.WriteLine($"str3 : {str3.GetHashCode()}");
        Console.WriteLine($"str4 : {str4.GetHashCode()}");
        Console.WriteLine($"str4 : {str5.GetHashCode()}");
        Console.WriteLine();

        Console.WriteLine($"obj1 : {obj1.GetHashCode()}");
        Console.WriteLine($"obj2 : {obj2.GetHashCode()}");
        Console.WriteLine();

        Console.WriteLine($"sb1 : {sb1.GetHashCode()} {sb1.ToString()}");
        Console.WriteLine($"sb2 : {sb2.GetHashCode()} {sb2.ToString()}");
    }
}
```

## Boxing 실습
```

public partial class Program
{
    public static void Main()
    {
        int number = 42;
        Int32 boxed = number; //Boxing
        int unboxed = boxed; //UnBoxing

        object obj = number; //UpCasting, Boxing
        int downed = (int)obj; //강제형변환, DownCasting


    }
}
```

## 얕은복사 깊은복사 실습
```
using System;

namespace DeepCopy
{
    class MyClass
    {
        public int MyField1;
        public int MyField2;

        public MyClass DeepCopy()
        {
            MyClass newCopy = new MyClass();
            newCopy.MyField1 = this.MyField1;
            newCopy.MyField2 = this.MyField2;

            return newCopy;
        }
    }

    class MainApp
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Shallow Copy");

            {
                MyClass source = new MyClass();
                source.MyField1 = 10;
                source.MyField2 = 20;

                MyClass target = source;
                target.MyField2 = 30;

                Console.WriteLine($"{source.MyField1} {source.MyField2}");
                Console.WriteLine($"{target.MyField1} {target.MyField2}");
            }

            Console.WriteLine("Deep Copy");

            {
                MyClass source = new MyClass();
                source.MyField1 = 10;
                source.MyField2 = 20;

                MyClass target = source.DeepCopy();
                target.MyField2 = 30;

                Console.WriteLine($"{source.MyField1} {source.MyField2}");
                Console.WriteLine($"{target.MyField1} {target.MyField2}");
            }
        }
    }
}
```
## Visual C# 실습
```
namespace WinFormsApp6
{
    public partial class Form1 : Form
    {
        private int Shinhodoong_Color = 1;
        private int reverse = 1;
        public Form1()
        {
            InitializeComponent();
        }
        public void Changeshinhodoong(int Color)
        {
            switch (Color)
            {
                case 0:
                    pictureBox1.Image = Image.FromFile(Environment.CurrentDirectory +
                "/신호등(준비중).png");
                    break;
                case 1:
                    pictureBox1.Image = Image.FromFile(Environment.CurrentDirectory +
                "/신호등(빨간색).png");
                    break;
                case 2:
                    pictureBox1.Image = Image.FromFile(Environment.CurrentDirectory +
                "/신호등(노란색).png");
                    break;
                case 3:
                    pictureBox1.Image = Image.FromFile(Environment.CurrentDirectory +
                "/신호등(녹색).png");
                    break;
            }
        }

        private void timer1_Tick(object sender, EventArgs e)
        {
            Changeshinhodoong(Shinhodoong_Color);

            Shinhodoong_Color += reverse;

            //if (Shinhodoong_Color >= 4)
            //{
            //    Shinhodoong_Color = 1;
            //}

            if(Shinhodoong_Color >= 3 || Shinhodoong_Color <= 1)
                reverse = -reverse;
        }

        private void Form1_Load(object sender, EventArgs e)
        {
            Changeshinhodoong(0);
        }
    }
}
플래그 변수를 사용해서 왔다갔다 불을 켜는 코드를 작성했는데 무슨말인지 모르겠다;;
```
```
using System.Data.SqlTypes;

namespace WinFormsApp7
{
    public partial class Form1 : Form
    {
        private int sajin = 1;
        private int sajin_max = 4;
        public Form1()
        {
            InitializeComponent();
        }

        private void pictureBox1_Click(object sender, EventArgs e)
        {

        }

        private void timer1_Tick(object sender, EventArgs e)
        {
            pictureBox1.Image = Image.FromFile(System.Environment.CurrentDirectory +
                "/재롱피우는 오버액션토끼/"+sajin + ".jpg");
            sajin++;
            if (sajin > sajin_max)
                sajin = 1;
        }
    }
}
```
![화면 캡처 2024-07-30 135207](https://github.com/user-attachments/assets/aa47bf6b-beb5-4169-9a8a-d0e2d52b8a1d)
귀엽다
***
![화면 캡처 2024-07-30 140147](https://github.com/user-attachments/assets/4ca98c49-0d89-4fe3-8c8f-fe7f60ffaffc)
코끼리도 똑같이 작성해봤다.
***
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
using static System.Windows.Forms.VisualStyles.VisualStyleElement;

namespace WinFormsApp7
{
    public partial class Form2 : Form
    {
        private int sajin1 = 1;
        private int sajin1_max = 4;

        private int sajin2 = 1;
        private int sajin2_max = 4;

        private int sajin3 = 1;
        private int sajin3_max = 7;
        public Form2()
        {
            InitializeComponent();
        }

        private void timer1_Tick(object sender, EventArgs e)
        {
            pictureBox1.Image = Image.FromFile(System.Environment.CurrentDirectory +
                "/다가오는 코끼리 두마리/" + sajin1 + ".jpg");
            sajin1++;
            if (sajin1 > sajin1_max)
                sajin1 = 1;
            pictureBox2.Image = Image.FromFile(System.Environment.CurrentDirectory +
                "/재롱피우는 오버액션토끼/" + sajin2 + ".jpg");
            sajin2++;
            if (sajin2 > sajin2_max)
                sajin2 = 1;
            pictureBox3.Image = Image.FromFile(System.Environment.CurrentDirectory +
                "/돌아서는 신랑신부/" + sajin3 + ".jpg");
            sajin3++;
            if (sajin3 > sajin3_max)
                sajin3 = 1;
        }

        private void button1_Click(object sender, EventArgs e)
        {
            timer1.Interval = 1000;
        }

        private void button2_Click(object sender, EventArgs e)
        {
            timer1.Interval = 100;
        }

        private void button3_Click(object sender, EventArgs e)
        {
            timer1.Interval = 10;
        }

        private void hScrollBar1_Scroll(object sender, ScrollEventArgs e)
        {
            timer1.Interval = hScrollBar1.Value;
        }
    }
}
```
![화면 캡처 2024-07-30 152828](https://github.com/user-attachments/assets/aea2bbf9-52be-4f71-a1e4-d14662d7c1e5)



이렇게도 만들어봤다.
***
![화면 캡처 2024-07-30 163254](https://github.com/user-attachments/assets/c8140271-8eab-4286-a1e2-7875b3c76f77)


메뉴 스트립으로 각각 다른속도로 움직이게도 해봤다.
***



    

