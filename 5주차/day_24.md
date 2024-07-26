## 24일차~~
```
아침 뇌풀기 리스트 quiz

list를 사용하여 정수형 1~100값이 들어있는 리스트 arr를 만들어라.
이를 홀수만 있는 arr 리스트를 이용해서
oddlist와 evenList2개를 만들어라.
만들어야하는 list 총 3개
```
## 풀이
```
namespace ConsoleApp64
{
    internal class Program
    {
        static void Main(string[] args)
        {
            List<int> arr = new List<int>();
            List<int> oddlist = new List<int>();
            List<int> evenlist = new List<int>();

            for(int i = 1; i <= 100; i++)
            {
                arr.Add(i);
                if(i % 2 == 1)
                oddlist.Add(i);
                else 
                evenlist.Add(i);
            }
            foreach(int i in arr)
                Console.Write(i + " ");
            Console.WriteLine();
            foreach (int i in oddlist)
                Console.Write(i + " ");
            Console.WriteLine();
            foreach (int i in evenlist)
                Console.Write(i + " " );
        }
    }
}
```
## quiz 2
```
Q) 두 리스트의 교집합을 구하세요.

   

   list1  --> { 1, 2, 2, 3, 4}

   list2 --> { 2, 3, 5, 6}



----------------------------

2

3
```
## 풀이
```
namespace ConsoleApp65
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int[] list1 = { 1, 2, 2, 3, 4 };
            int[] list2 = { 2, 3, 5, 6 };

            List<int> list3 = new List<int>();

            for(int i = 0; i < list1.Length; i++)
            {
                for(int j = 0; j < list2.Length; j++)
                {
                    if (list1[i] == list2[j] && !(list3.Contains(list1[i])))
                    {
                        list3.Add(list1[i]);
                    }    
                }
            }
            foreach(int n in list3)
            {
                Console.WriteLine(n);
            }
        }
    }
}
```
## File 클래스
```
File : 파일의 생성, 복사, 삭제, 이동 조회 처리
Fileinfo : File클래스와 동일하지만 정적 메소드가 아닌 인스턴스 메소드 제공
Directory : 디렉토리 생성, 삭제, 이동, 복사 등 처리
DirectoryInfo : Directory 클래스와 기능은 동일하나 정적 메소드가 아닌 인스턴스 메소드 제공
```
![화면 캡처 2024-07-26 101604](https://github.com/user-attachments/assets/6bbb91a9-2ecc-4251-bf90-2c1d8535db24)
***
![화면 캡처 2024-07-26 101824](https://github.com/user-attachments/assets/78eca09f-3896-4fcc-affc-fbf912b35b22)
***
![화면 캡처 2024-07-26 102030](https://github.com/user-attachments/assets/fe6c6ec2-3a55-42ab-a8f4-dd7c5e84a5d4)
***
```
namespace FileExam01
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string path = @"c:\temp\abc.txt";
            string content = "Hello World~~";

            //File.WriteAllText(path, content);
            //byte[] bytes = new byte[3] { 1, 2, 3 };
            //File.WriteAllBytes(path, bytes);
            //string str = File.ReadAllText(path);
            //Console.WriteLine(str);

            FileInfo fileInfo = new FileInfo(path);

            StreamWriter sw = fileInfo.CreateText();
            sw.WriteLine("안녕하삼");
            sw.Close();
        }
    }
}
```
```
namespace FileExam02
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string path = @"c:\Temp\ccc.txt";
            FileInfo fi = new FileInfo(path);
            //쓰기
            using (StreamWriter sw = fi.CreateText())
            {
                sw.WriteLine("안녕하세용");
            }
            //읽기
            using (StreamReader sr = fi.OpenText())
            {
                var s = "";
                while ((s = sr.ReadLine()) != null)
                {
                    Console.WriteLine(s);
                }
            }
        }
    }
}
```
## File 퀴즈
```
---------------------------------------------------------
Q)
    1 ~ 100사이의 5의 배수를
    C:\Temp\result1.txt에
    결과를 출력해 보세요.

    1. File 클래스 사용
-------------------------------------------------------------
[2단계]
파일에 있는 결과 내용을
콘솔 화면으로 읽어서 출력해 봅니다.
	2. FileInfo와 StreamWriter 사용
```
## 풀이
```
1단계)
namespace FileQuiz01
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string path = @"C:\Temp\result2.txt";
            string content = "";
            for (int i = 1; i <= 100; i++)
            {
                if (i % 5 == 0)
                {
                    content += i.ToString() + " ";
                }
            }
            File.WriteAllText(path, content );
        }
    }
}


2단계)
namespace FileQuiz01
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string path = @"C:\Temp\result1.txt";
            FileInfo fi = new FileInfo(path);
            using (StreamWriter sw = fi.CreateText())
            {
                for (int i = 1; i <= 100; i++)
                {
                    if (i % 5 == 0)
                    {
                        sw.WriteLine(i + " ");
                    }
                }
            }
            using (StreamReader sr = fi.OpenText())
            {
                var s = "";
                while((s = sr.ReadLine()) != null)
                {
                    Console.WriteLine(s);
                }
            }
        }
    }
}
```
![화면 캡처 2024-07-26 112434](https://github.com/user-attachments/assets/fb177f07-c63b-4b47-acdf-fec1c590da22)
***
![화면 캡처 2024-07-26 114851](https://github.com/user-attachments/assets/0eb47abb-0d37-467a-9922-6222e38d252d)
***
```
namespace FileExam_Basic
{
    internal class Program
    {
        static void Main(string[] args)
        {
            long someValue = 0x123456789ABCDEF0;
            Console.WriteLine($"{someValue :X16}");

            string path = @"C:\Temp\a.dat";
            Stream outStream = new FileStream(path, FileMode.Create);
            byte[] wBytes = BitConverter.GetBytes(someValue);
            // 화면에 byte 출력??
            foreach(byte b in wBytes )
            {
                Console.Write($"{b:X16}");
            }
            Console.WriteLine();

            outStream.Write(wBytes, 0, wBytes.Length);
            outStream.Close();
            //읽기 -> binary -> text화면에 출력
            Stream inStream = new FileStream(path, FileMode.Open);
            byte[] rbytes = new byte[8];

            int i = 0;
            while(inStream.Position < inStream.Length)
            {
                rbytes[i++] = (byte)inStream.ReadByte();
            }
            long readValue = BitConverter.ToInt64(rbytes, 0);
            Console.WriteLine($"{readValue:X16}");
        }
    }
}
```
## 퀴즈
```
﻿- 텍스트 파일을 복사하는 프로그램을 
  만들어 봅시다.

 사용예 ) myCopy.exe abc.txt   cba.txt

abc.txt --> Hello World~!

------------------------------------------------

FileStream을 이용해서 만드세요.
StreamReader
StreamWriter

현재 프로그램은 txt파일만 입력받습니다.
```
## 풀이
```
namespace myCopy
{
    internal class Program
    {
        static void Main(string[] args)
        {
            //arg[0] a.txt
            //arg[1] b.txt
            string orgnfile = @$"C:\Temp\{args[0]}";
            string copyfile = @$"C:\Temp\{args[1]}";
            FileStream fs = new FileStream(orgnfile, FileMode.Create);

            using(StreamWriter write = new StreamWriter(fs))
            {
                write.WriteLine("안녕하삼계탕");
            }

            try
            {
                using (StreamReader sr = new StreamReader(orgnfile))
                using (StreamWriter sw = new StreamWriter(copyfile))
                {
                    var line = "";
                    while ((line = sr.ReadLine()) != null)
                    {
                        sw.WriteLine(line);
                    }
                }
                Console.WriteLine("복사성공");
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex.Message);
            }
        }
    }
}
```
***
## Thread
```
namespace ThreadTest01
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Thread t1 = new Thread(threadFunc1);
            Thread t2 = new Thread(threadFunc2);
            t1.Start();
            t2.Start();
        }
        static void threadFunc1()
        {
            for(int i = 1; i <= 100; i++)
            {
                Console.WriteLine(i);
            }
        }
        static void threadFunc2()
        {
            char c1 = 'A';
            char c2 = 'a';
            for(int i = 1; i <= 26; i++)
                Console.WriteLine((char)c1++);
            for(int j = 1; j <= 26; j++)
                Console.WriteLine((char)c2++);
        }
    }
}
```
```
namespace ThreadTest02
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Thread t = new Thread(threadFunc);
            t.IsBackground = true; //Main 종료시 바로 종료됨
            t.Start();
            t.Join();   //Main 스레드가 t 를 기다려줍니다

            Thread.CurrentThread.Name = "main 스레드";
            string mtName = Thread.CurrentThread.Name;
            Console.WriteLine($"{mtName} 프로그램 종료");
        }
        static void threadFunc()
        {
            Console.WriteLine("7초 후 프로그램 종료");
            Thread.Sleep(7000);

            Thread.CurrentThread.Name = "thread1 스레드";
            string mtName = Thread.CurrentThread.Name;
            Console.WriteLine($"{mtName} 프로그램 종료");
        }
    }
}
```
```
visual C#에서의 스레드

using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace WindowsFormsApp6
{
    public partial class Form1 : Form
    {
        private Thread thread1;
        public Form1()
        {
            InitializeComponent();
        }

        private void label1_Click(object sender, EventArgs e)
        {

        }

        private void button1_Click(object sender, EventArgs e)
        {
            for (int i = 0; i < 10; i++)
            {

                thread1 = new Thread(UpdateTime);
                thread1.IsBackground = true;
                thread1.Start();
                
            }
        }
        private void UpdateTime()
        {
            while (true)
            {
                DateTime currentTime = DateTime.Now;
                string strTime = currentTime.ToString("hh : mm : ss");

                //this.Invoke((MethodInvoker)delegate
                //{
                //    label1.Text = strTime;
                //});

                Invoke((Action)(() => label1.Text = strTime));

                Thread.Sleep(1000);
            }
        }
    }
}
```
![화면 캡처 2024-07-26 154758](https://github.com/user-attachments/assets/66485561-2163-4bf9-b4bd-a462a8fd9c1a)
***
```
timer를 이용해서 간단하게도 작성이 가능하다.



using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace timerapp
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void button1_Click(object sender, EventArgs e)
        {
           timer1.Start();
        }

        private void button2_Click(object sender, EventArgs e)
        {
            timer1.Stop();
        }

        private void timer1_Tick(object sender, EventArgs e)
        {
            label1.Text = DateTime.Now.ToString("hh : mm : ss");
        }
    }
}
```
## QUIZ
```
Q) 파일읽기와 파일쓰기 
     2 기능을 메소드로 만들어 봅시다.
    Main에서는  writeThread / readThread로  만들어서
    동작하도록 구현해 봅시다.
   단, 파일은 다음과 내용이 입력되어 있습니다.
    C:\Temp\data.txt  --> "파일처리 / 스레드 프로그래밍은 재미있다~!"
---------------------------------------------------------------------------------------------
Main()
{
     Thread writeThread  = new Thread( DataWrite );
     Thread readThread = new Thread( DataRead );
     //Background 스레드로 만드세요.
    // thread join을 사용하여 Main메소드가 스레드가 종료될 때까지 기다립니다.
 }
 static void DataWrite()
 {
 }
...
```
## 풀이
```
namespace ConsoleApp67
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Thread writeThread = new Thread(DataWrite);
            Thread readThread = new Thread(DataRead);

            writeThread.IsBackground = true;
            readThread.IsBackground = true;
            writeThread.Start();
            writeThread.Join();
            readThread.Start();
            readThread.Join();

            //Background  스레드로 만드세요
            //thread join  을 사용하여 main메소드가 스레드가 종료될때 까지
            //기다립니다.
        }
        static void DataWrite()
        {
            string data = $@"C:\Temp\data.txt";
            FileStream fs = new FileStream(data, FileMode.Create);

            using (StreamWriter sw = new StreamWriter(fs))
            {
                sw.WriteLine("파일처리/ 스레드 프로그래밍은 재미있다~!");
            }
            Console.WriteLine("파일처리 완료");
        }
        static void DataRead()
        {
            string readData = File.ReadAllText($@"C:\Temp\data.txt");
            Console.WriteLine(readData);
        }
    }
}
```







