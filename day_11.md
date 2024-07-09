## 11일차 !!!!! 👴👴👴👴👴👴👴👴👴👴
***
## 오전 진도
## 함수 호출 복습
```
C# 교재에 있는 예제 풀이

namespace ConsoleApp41
{
    internal class Program
    {
        static int CallByValueDemo(int x)
        {
            return x;
        }
        static void Main(string[] args)
        {

            Console.Write("정수를 입력하세요. : ");
            int inputnumber = Convert.ToInt32(Console.ReadLine());

            Console.WriteLine("입력하신 정수의 값은 {0} 입니다.", CallByValueDemo(inputnumber));
        }
    }
}
```

```
using System.ComponentModel;

namespace ConsoleApp41
{
    internal class Program
    {
        //static void GetNumbers(int x, int y)
        //{
        //    x = 0; y = 0;
        //}
        //static void GetNumbers(out int x, out int y)
        //{
        //    x = 0;
        //    y = 0;
        //}
        //static void GetNumbers(ref int x, ref int y)
        //{
        //    x = 0; y = 0;
        //}
        static void GetValue(int x)
        {
            x = 1;
        }
        static void Main(string[] args)A
        {
            //int a = int.Parse(Console.ReadLine());
            //int b = int.Parse(Console.ReadLine());
            //GetNumbers(out a, out b);
            //Console.WriteLine("a에 저장된 값은 {0}", a);
            //Console.WriteLine("b에 저장된 값은 {0}", b);

            int a = 100;
            GetValue(a);
            Console.WriteLine($"a에 저장된 값은 {a}");
        }
    }
}
```
## 재귀
```
재귀호출(recursive call)이란 함수 내부에서 자기 자신을 반복적으로 호출하는 것을 의미한다.
반복 행위를 하는 함수를 재귀함수(recursive function)라고 한다.
```
## 예제
```
namespace ConsoleApp42
{
    internal class Program
    {
        static void Recursive(int n)
        {
            Console.WriteLine(n++);
            Recursive(n);
        }
        static void Main(string[] args)
        {

            Recursive(0);

        }
    }
}
```
```
팩토리얼
namespace ConsoleApp42
{
    internal class Program
    {
        static int Factorial(int n)
        {
            if (n == 1)
            {
                return n;
            }
            else
                return n * Factorial(n - 1);
        }
        static void Main(string[] args)
        {
            int a = 10;
            Console.WriteLine(Factorial(a));
        }
    }
}
```
```
다이나믹 프로그래밍
namespace ConsoleApp43
{
    internal class Program
    {

        static long[] arr;

        static void Main(string[] args)
        { 
            //Dynamic Programming Factorial

            int n = 5;
            arr = new long[n + 1];

            arr[0] = 1;  //이 코드가 핵심!!!!

            for(int i = 1; i <= n; i++)
            {
                arr[i] = i * arr[i - 1];
            }
            Console.WriteLine(arr[n]);
        }
    }
}
```

## quiz!!
```
﻿5!의 경우



5 * 4 * 3 * 2 * 1 

입니다.



N 팩토리얼의 값을 구하는 문제를



1단계 : 재귀적인 방법 (Recursive)



2단계 : 다이나믹 방법 (Dynamic Algorithm) 



각각 구해주세요.



----------------------------------------

예습 : 피보나치 수열도 두 가지 방식으로 구현할 수 있습니다. 미리 예습해 봅시다.

피보나치 수열

1 1 2 3 5 8 13 21 33 ...



앞의 두 수열의 값이 현재 값이 되는 수

N번째 피보나치 수열의 값을 찾는 문제는 수학적으로 중요한 문제입니다.

이를 코딩으로 표현해 봅시다.



FibonacciRecursive(n - 1) + FibonacciRecursive(n - 2);
```
## 풀이
```
1단계)

namespace ConsoleApp43
{
    internal class Program
    {
        static int Recursive(int n)
        {
            if (n == 1)
            {
                return n;
            }
            else
                return n * Recursive(n - 1);
        }
        static void Main(string[] args)
        {
            int a = 5;
            Console.WriteLine(Recursive(a));
        }
    }
}
```
```
2단계)
namespace ConsoleApp43
{
    internal class Program
    {
        static long[] arr;
        static void Main(string[] args)
        {
            int n = 5;
            arr = new long[n + 1];
            arr[0] = 1;
            for (int i = 1; i <= n; i++)
            {
                arr[i] = i * arr[i - 1];
            }
            Console.WriteLine(arr[n]);
        }
    }
}
```
```
예습
using System.ComponentModel.Design;

namespace ConsoleApp43
{
    internal class Program
    {
        static int FibonacciRecursive(int n)
        {
                if (n <= 1)
                    return n;
                else
                    return FibonacciRecursive(n - 1) + FibonacciRecursive(n - 2);
            
        }
    

        static void Main(string[] args)
        {
            Console.Write("범위를 입력하시오 : ");
            int n = Int32.Parse(Console.ReadLine());

            Console.WriteLine("피보나치 수열 : ");
            for (int i = 1; i <= n; i++)
            {
                Console.Write(FibonacciRecursive(i) + " ");
            }
        }
    }
}
```

## 전역변수 연습
```
namespace ConsoleApp45
{
    internal class Program
    {
        static string name = "Janet"; //전역변수, 멤버변수

        static void ShowName()
        {
            string name = "Micheal";   //지역변수
            Console.WriteLine(name);
        }
        static void Main(string[] args)
        {
            ShowName();
            Console.WriteLine(name);

        }
    }
}
```
```
namespace ConsoleApp45
{
    internal class Program
    {
        static int num;
        static string str;

        static void PrintVar()
        {
             num = 100;
             str = "홍길동";

            Console.WriteLine($"PrintVar : num = {num}, str = {str}");
        }
        static void Main(string[] args)
        {
            PrintVar();

            Console.WriteLine($"Main : num = {num}, str = {str}");
        }
    }
}
```
## public, private 예제
```

namespace ConsoleApp46
{
    internal class Program
    {
        class ClassA
        {
            private int a;
            private void PrintOutA()
            {
                Console.WriteLine(a);
            }
        }

        class ClassB
        {
            public int b;
            //멤버 메소드
            public void PrintOutB()
            {

                Console.WriteLine(b);
            }
        }

        static void Main(string[] args)
        {

            ClassA x = new ClassA(); //객체 만들기는 지장이 없다.
            //x.a  = 123;
            //x.PrintOutA(); 

            ClassB y = new ClassB();
            y.b = 123;
            y.PrintOutB();

        }
    }
}
```

***


## WinForms 앱 코딩해보기
```
namespace WinFormsApp2
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void button1_Click(object sender, EventArgs e)
        {
            //MessageBox.Show("메시지 박스 확인");
            pictureBox1.Image = Image.FromFile(@"C:\Temp\img2.png");
        }

        private void pictureBox1_Click(object sender, EventArgs e)
        {
        }

        private void button2_Click(object sender, EventArgs e)
        {
            pictureBox1.Image = Image.FromFile(@"C:\Temp\img1.png");
        }
    }
}
```
## 실행 결과

```
컴파일했을때
```

![test 1](https://github.com/fkfkfk0406/smartfactory/assets/91593653/50484ec4-62d4-4b5c-a9e7-e55e41194705)


```
버튼 1을 눌렀을때
```

![test 2](https://github.com/fkfkfk0406/smartfactory/assets/91593653/4c6d4720-1683-424f-837a-b89d52e98ab2)


## 예제 2
```
namespace WinFormsApp3
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void textBox1_TextChanged(object sender, EventArgs e)
        {

        }
        private void button1_Click(object sender, EventArgs e)
        {
            textBox2.Text = textBox1.Text + "님 소프트웨어공학과에 들어온 것을 환영합니다.";
        }
        private void button2_Click(object sender, EventArgs e)
        {
            Dispose();
        }
    }
}
```
## 실행결과

컴파일 했을 때
![test3](https://github.com/fkfkfk0406/smartfactory/assets/91593653/a579bd42-33fa-40cc-bd0a-bbfa8b8f73fe)

출력 버튼을 눌렀을 때
![test 4](https://github.com/fkfkfk0406/smartfactory/assets/91593653/d0cbf254-85d6-4dae-bcd8-2516e44db897)

## 교제 예제
## 1번 풀이
```
namespace test1
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void textBox1_TextChanged(object sender, EventArgs e)
        {

        }

        private void textBox2_TextChanged(object sender, EventArgs e)
        {

        }

        private void button1_Click(object sender, EventArgs e)
        {
            textBox3.Text = textBox1.Text + "님~~! 당신의 학번은 " + textBox2.Text + " 입니다~!!";
        }

        private void button2_Click(object sender, EventArgs e)
        {
            Dispose();
        }

        private void textBox3_TextChanged(object sender, EventArgs e)
        {
            
        }
    }
}
```
## 실행결과

컴파일 결과

![text 5](https://github.com/fkfkfk0406/smartfactory/assets/91593653/e190b824-c0d1-496c-9cbf-c16456a4a452)


출력 결과

![test 6 ](https://github.com/fkfkfk0406/smartfactory/assets/91593653/53322f12-c7ce-45bb-89bb-e0c016c7a3a9)

## 2번 풀이
```
namespace test1
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void textBox1_TextChanged(object sender, EventArgs e)
        {

        }

        private void textBox2_TextChanged(object sender, EventArgs e)
        {

        }

        private void button1_Click(object sender, EventArgs e)
        {
            MessageBox.Show(textBox1.Text + "님~~! 당신의 학번은 " + textBox2.Text + " 입니다~!!");
        }

        private void button2_Click(object sender, EventArgs e)
        {
            Dispose();
        }

        private void textBox3_TextChanged(object sender, EventArgs e)
        {

        }
    }
}
```
## 실행결과
컴파일 결과

![test 7](https://github.com/fkfkfk0406/smartfactory/assets/91593653/ef7c0fe9-14e4-4493-9288-bac834118d2b)


실행 결과

![test 8](https://github.com/fkfkfk0406/smartfactory/assets/91593653/103de619-145e-4f43-8107-e37934834879)

## 3번 풀이
```
namespace test1
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void textBox1_TextChanged(object sender, EventArgs e)
        {

        }

        private void textBox2_TextChanged(object sender, EventArgs e)
        {

        }

        private void button1_Click(object sender, EventArgs e)
        {
            textBox3.Text = textBox1.Text + "님~~! " + Environment.NewLine + "당신의 학번은 " + Convert.ToChar(13) + Convert.ToChar(10) + textBox2.Text + Environment.NewLine + "입니다^^";
            MessageBox.Show(textBox1.Text + "님~~! " + "\r\n" + "당신의 학번은" + "\r\n" + textBox2.Text + "\r\n" + "입니다!!", "\" " + "확인 사항" + Convert.ToChar(34));
        }

        private void button2_Click(object sender, EventArgs e)
        {
            Dispose();
        }

        private void textBox3_TextChanged(object sender, EventArgs e)
        {

        }

        private void textBox3_TextChanged_1(object sender, EventArgs e)
        {
            
        }
    }
}
```
## 실행 결과

컴파일 결과

![test 9](https://github.com/fkfkfk0406/smartfactory/assets/91593653/a0eda6ee-3cbf-4d76-a0f1-eb89b3318315)


실행 결과

![text 10](https://github.com/fkfkfk0406/smartfactory/assets/91593653/68a242ba-98f3-495e-807c-4cd6f872cf72)

## 4~5번 풀이
```
4번) TextBox의 색깔을 변경 하려면 속성 중에 어느 것을 설정해야 하는가?
A) BackColor
```
```
5번) TextBox에 글자들이 여러 줄로 표시되도록 하려면 속성 중에 어느 것을 설정해야 하는가?
A) Multiline
```
```
6번) TextBox에 글자들을 여러 줄로 입력하시오.
A)
```

![test 12](https://github.com/fkfkfk0406/smartfactory/assets/91593653/f0f09ea4-7244-4320-8385-a24ee45290ab)


```
7번) Button, Label, TextBox의 글자 크기를 동시에 조정할 수 있는가?
A) 디자인 화면에서 드래그 후 Font의 글자크기를 조정하면 됨.
```

```
8번) Button 에서 사진을 표시하려면 어떤 속성을 이용해야 하는지 실제로 표시하시오.
A)
```

![image](https://github.com/fkfkfk0406/smartfactory/assets/91593653/12bd41de-1a02-4183-b2dd-ba275c28e525)

***


