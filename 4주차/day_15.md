## 15일차 !! (4주차 스타트)
~~벌써 한달이라니~~


```
배열과 리스트의 차이점
-> 배열은 크기가 할당되어있음, 리스트는 자료가 들어갈 때 마다 가변적으로 크기가 바뀜
```

## 리스트 연습 
```
namespace ConsoleApp60
{
    class Person 
    {
        public string name;
    }

    internal class Program
    {
        static void Main(string[] args)
        {
            string[] arr = new string[3] {"홍길동", "홍길서", "홍길북"};
            List<char> list = new List<char>();
            list.Add('X');
            list.Add('Y');
            list.Add('Z');

            Person[] persons = new Person[2];
            Person p1 = new Person();
            p1.name = "홍길동";
            persons[0] = p1;
            Person p2 = new Person(); 
            p2.name = "홍길서";
            persons[1] = p2;

            List<Person> list2 = new List<Person>();
            Person p3 = new Person();
            p3.name = "홍길남";
            list2.Add(p3);

            Person p4 = new Person();
            p4.name = "홍길북";
            list2.Add(p4);

            foreach (Person p in list2)
            {
                Console.WriteLine(p.name);
            }
        }
    }
}
```

## 리스트 연습 퀴즈
```
 //1. 브랜드와 스피드 다른 자동차 3개를 만드세요.

    //2. car 객체를 담는 carList를 만듭니다.

    //3. carList를 이용해서 자동차의 브랜와 속도를 출력하세요.



출력 예

--------------------------------

현대

300km



기아

280km



BMW

290km 다른 자동차 3개를 만드시오
2. CAR 객체를 담는 CARlist를 만드시오
3. carlist를 이용하여 출력하세이요
```

## 풀이

```
namespace QuizobjectList
{
    class Car
    {
        public string brand { get; set; } //게터, 세터 (property)로 만들면 대문자로 쓰는게 좋음(일반적으로)
        public int speed { get; set; }

    }

    internal class Program
    {
        static void Main(string[] args)
        {
            List<Car> CarList = new List<Car>();
            Car c1 = new Car();
            Car c2 = new Car();
            Car c3 = new Car();

            c1.brand = "현대";
            c2.brand = "기아";
            c3.brand = "벤츠";

            c1.speed = 150;
            c2.speed = 180;
            c3.speed = 400;

            CarList.Add(c1);
            CarList.Add(c2);
            CarList.Add(c3);

            foreach(Car c in CarList)
            {
                Console.WriteLine($"브랜드는 : {c.brand}");
                Console.WriteLine($"속도는 : {c.speed}");
            }
        }
    }
}
```

## 교재 예제 실습

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

namespace CurrentTimeApp
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }
        int Number;
        DateTime NowTime;

        private void GetNumber()
        {
            Number++;
        }
        private void OutNumber()
        {
            textBox1.AppendText(Number + "\r\n");
        }
        private void GetTime()
        {
            NowTime = DateTime.Now;
        }
        private void OutTime()
        {
            textBox2.AppendText(NowTime + "\r\n");
        }
        private void button1_Click(object sender, EventArgs e)
        {
            for (int i = 0; i < 5; i++)
            {
                GetNumber();
                OutNumber();
                GetTime();
                OutTime();
                System.Threading.Thread.Sleep(1000);
            }
        }
    }
}
```

![화면 캡처 2024-07-15 113329](https://github.com/user-attachments/assets/561aa568-c162-47aa-97a9-3dbd9360527e)

## 오후 퀴즈
```
년도, 월, 일 입력받아 날짜 출력

그리고 현재 시간 출력하는 콘솔 프로그램을 작성해 주세요.

힌트) DateTime, ToString(), Format -- yyyy MM dd HH mm ss 

------------------------------------

년도 : 2000

월 : 12

일 : 25



2000-12-25 





현재시간 : 2024-07-15 13:20:30

-------------------------------------------

```

## 풀이

```
using System.Runtime.Serialization;
using Microsoft.VisualBasic;

namespace datetimequiz
{
    internal class Program
    {
        static void Main(string[] args)
        {
            DateTime dateTime = DateTime.Now;
            Console.WriteLine("년도, 월, 일을 입력하시오");
            Console.Write("년도 : ");
            int year = Int32.Parse(Console.ReadLine());
            Console.Write("월   : ");
            int month = Int32.Parse(Console.ReadLine());
            Console.Write("일   : ");
            int day = Int32.Parse(Console.ReadLine());

            string time = new DateTime(year, month, day).ToString("yyyy-MM-dd");
            Console.WriteLine(time);

            string currentTime = DateTime.Now.ToString("yyyy-MM-dd HH:mm:ss");
            Console.WriteLine($"\n\n현재시간 : {currentTime}");
        }
    }
}
```
## 퀴즈
```
홀수합 짝수합 비쥬얼 C# 만드삼
```
## 풀이
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

namespace WinFormOddEvEN
{

    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }
        int value2;
        int value3;
        private void button1_Click(object sender, EventArgs e)
        {
            int value1 = int.Parse(textBox1.Text);
            for (int i = 1; i <= value1; i++)
            {
                if(i % 2 == 1)
                {
                    textBox2.AppendText($"{i} + ");
                    value2 += i;
                }
                else
                {
                    textBox3.AppendText($"{i} + ");
                    value3 += i;
                }
            }
            textBox2.AppendText($"= {value2}");
            textBox3.AppendText($"= {value3}");
        }
    }
}
```
![화면 캡처 2024-07-15 144400](https://github.com/user-attachments/assets/05d938fc-a7b9-4b42-a4e2-436887b0ee42)

## 교재 103페이지 예제 5번
## 풀이
```
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Diagnostics.Eventing.Reader;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace WinFormOddEvEN
{

    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }
        int value2;
        int value3;
        int value4;
        private void button1_Click(object sender, EventArgs e)
        {
            int value1 = int.Parse(textBox1.Text);
            for (int i = 1; i <= value1; i++)
            {
                if(i % 3 == 0)
                {
                    textBox2.AppendText($"{i} + ");
                    value2 += i;
                }
                else if(i % 3 == 1)
                {
                    textBox3.AppendText($"{i} + ");
                    value3 += i;
                }
                else if(i % 3 == 2)
                {
                    textBox4.AppendText($"{i} + ");
                    value4 += i;
                }
            }
            textBox2.AppendText($" = {value2}");
            textBox3.AppendText($" = {value3}");
            textBox4.AppendText($" = {value4}");
        }
    }
}
```
![화면 캡처 2024-07-15 150224](https://github.com/user-attachments/assets/e2a0d514-6f7b-48fc-801b-b7907c0a7f46)

## 마지막 + 없애기
```
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Diagnostics.Eventing.Reader;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace WinFormOddEvEN
{

    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }
        int value2;
        int value3;
        int value4;
        private void button1_Click(object sender, EventArgs e)
        {
            int value1 = int.Parse(textBox1.Text);
            for (int i = 1; i <= value1; i++)
            {
                if(i % 3 == 0)
                {
                    textBox2.AppendText(i + " + ");
                    value2 += i;
                }
                else if(i % 3 == 1)
                {
                    textBox3.AppendText(i + " + ");
                    value3 += i;
                }
                else if(i % 3 == 2)
                {
                    textBox4.AppendText(i + " + ");
                    value4 += i;
                }
            }
            textBox2.Text = textBox2.Text.Substring(0, textBox2.Text.Length - 2);
            textBox3.Text = textBox3.Text.Substring(0, textBox3.Text.Length - 2);
            textBox4.Text = textBox4.Text.Substring(0, textBox4.Text.Length - 2);

            textBox2.AppendText($" = {value2}");
            textBox3.AppendText($" = {value3}");
            textBox4.AppendText($" = {value4}");
        }
    }
}
```

![화면 캡처 2024-07-15 151044](https://github.com/user-attachments/assets/2fa13fde-fc31-40ab-848d-274e8f119c33)

## 오라클 설치 및 SQL 계정 설정을 수행했다,,!!!!
## SQL DEVELOPER 을 설치하고 실행 해 보았다,,!!!!

![화면 캡처 2024-07-15 165315](https://github.com/user-attachments/assets/08251636-1364-47a9-b6aa-71c399160509)




