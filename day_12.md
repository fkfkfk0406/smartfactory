## 배열 코딩 복습
```
namespace ConsoleApp48
{
    internal class Program
    {
        static void Main(string[] args)
        {

            int[] StudentIDs = new int[5] {1,2,3,4,5};  //선언과 동시 초기화
            //StudentIDs[0] = 1; //선언 후 초기화
            string[] StudentNames = new string[3] { "Jones", "Jake", "Tim" };

            int[] evenNums = new int[10];
            for(int x = 0; x < 10; x++)
            {
                evenNums[x] = x * 2;
                Console.WriteLine($"you ust saved {evenNums[x]}");
            }
        }
    }
}
```
## 기습 퀴즈
```
Q) 13의 배수가 7개 들어있는 numbers라는 배열을 만들어보자...
값은 for문을 사용하여 채워 넣으시오..
```
## 풀이
```
namespace ConsoleApp48
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int[] numbers = new int[13];

            for(int i = 1; i <= 7; i++)
            {
                numbers[i] = i * 13;
                Console.WriteLine(numbers[i]);
            }
        }
    }
}
```

## 기습 퀴즈 2
```
Q) 이름을 3개 입력하여 string 배열 names에 입력해보시오...
그리고 입력된 배열의 이름을 출력하시오....
```
## 풀이
```
namespace ConsoleApp48
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string[] names = new string[3];
            for(int i = 0; i < names.Length; i++)
            {
                names[i] = Console.ReadLine();
            }
            for(int j = 0; j < names.Length; j++)
            {
                Console.WriteLine(names[j]); 
            }
        }
    }
}
```
***

## foreach 사용 연습
```
using System.Globalization;

namespace ConsoleApp48
{
    internal class Program
    {
        static void Main(string[] args)
        {

            int[] number = new int[5] { 100, 200, 300, 400, 500 };

            foreach(int n in number)
            {
                Console.WriteLine(n);
            }

        }
    }
}
```
```
using System.Globalization;

namespace ConsoleApp48
{
    class Student
    {
        public int Id { get; set; }
        public string Name { get; set; } = "아무개";
        public string Major { get; set; } = "공통학부";
    }
    internal class Program
    {
        static void Main(string[] args)
        {
            Student[] students = new Student[3];
            Student s1 = new Student();
            Student s2 = new Student();
            Student s3 = new Student();

            students[0] = s1;
            students[1] = s2;
            students[2] = s3;

            s1.Id = 1;
            s1.Name = "홍길동";
            s1.Major = "컴퓨터 공학";

            s2.Id = 2;
            s2.Name = "이순신";
            s2.Major = "기계 설계 공학";

            s3.Id = 3;
            s3.Name = "강감찬";
            s3.Major = "전자공학";

            foreach(Student s in students)
            {   
                Console.WriteLine(s.Id);
                Console.WriteLine(s.Name);
                Console.WriteLine(s.Major);
            }
            for(int i = 0; i < students.Length; i++)
            {
                Console.WriteLine(students[i].Id);
                Console.WriteLine(students[i].Name);
                Console.WriteLine(students[i].Major);
            }
        }
    }
}
```
```
using System.Runtime.Intrinsics.X86;

namespace Code89
{
    internal class Program
    {
        static void Main(string[] args)
        {

            string[] studentNames = new string[10];

            for (int i = 0; i < 2; i++)
            {
                Console.Write("학생의 이름을 입력하세요 : ");
                studentNames[i] = Console.ReadLine();
            }
            int cnt = 0;
            foreach(string y in studentNames)
            {
                Console.WriteLine(studentNames[cnt++]);
            }
        }
    }
}
```

```
C/C++ -- 컴파일 언어(기계어 모드)
JAVA, C# -- 하이브리드 컴파일, 인터프린터
            (class가 반쯤 컴파일)
Python, Ruby -- 인터프린터 -> 소스 실시간 컴파일
JavaScripts(React.js, jQuery, Anguar, Svelte ,,,,,)
```

## PARAMS 이용 실습
```
using System.Runtime.Intrinsics.X86;

namespace Code89
{
    internal class Program
    {
        static void TestMethod(double[] arr)
        {

        }
        static int TotalSum(params int[] myArray)
        {
            int sum = 0;
            for(int i = 0; i < myArray.Length; i++)
            {
                sum += myArray[i];
            }
            return sum;
        }
        static void Main(string[] args)
        {
            double[] arr2 = {1, 2, 3};

            TestMethod(arr2);
            //TestMethod(1.1, 2.2) //error
            Console.WriteLine(TotalSum(1, 2, 3, 4, 5, 6, 7, 8, 9, 10));
            Console.WriteLine(TotalSum(1, 3, 5, 7, 9));



        }
    }
}
```
## (indexer) this 문법 사용
```
namespace IndexerTest
{
    class IdxDemo
    {
        private int[] num = new int[5];

        public int this[int x]
        {
            set { num[x] = value; }
            get { return num[x]; }
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {

            IdxDemo test = new IdxDemo();
            for (int i = 0; i < 5; i++)
            {
                test[i] = i;
                Console.WriteLine(test[i]);
            }
        }
    }
}
```
```
namespace IndexTest2
{
    class StudentScore
    {
        private double[,] eachScore = new double[3, 3]
        {
            {0, 0, 0 },
            {0, 0, 0 },
            {0, 0, 0 }
        };
        //매개변수를 두개 가지는 인덱서
        public double this[int x, int y]
        {
            set { eachScore[x, y] = value; }
            get { return eachScore[x, y]; }
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {

            int a; // 학생 카운터
            int b; // 과목별 점수
            double sum = 0.0; // 총점
            double avg = 0.0; // 평균

            StudentScore ss = new StudentScore();

            for(int i = 0; i < 3; i++)
            {
                for(int j = 0; j < 3; j++)
                {
                    sum += ss[i, j];
                }
            }
        }
    }
}
```
```
namespace IndexerApp01
{
    class MemberInfo
    {
        private string[] names = new string[5];

        public string this[int index]
        {
            set {names[index] = value; }
            get { return names[index]; }
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {
            MemberInfo mInfo = new MemberInfo();
            mInfo[0] = "홍길동";
            mInfo[1] = "이순신";
            
            Console.WriteLine(mInfo[0]);
            Console.WriteLine(mInfo[1]);
        }
    }
}                         
```
```
namespace IndexerApp02
{
    class ScoreBoard
    {
        private int[] scores = new int[5];

        public int this[int index]
        {
            get { return scores[index]; }
            set { scores[index] = value; }
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {

            ScoreBoard sb = new ScoreBoard();
            sb[0] = 100;
            sb[1] = 90;
            sb[2] = 80;

        }
    }
}
```
## 인덱스 vs 인덱서
```
-- 배열에서 데이터가 저장되는 위치(주소)를 가리키는 변수를 인덱스(index)라고 부르는데 비해,
인덱서(indexer)는 특별한 종류의 프로퍼티를 부르는 이름이다.
```
## enum
```
namespace Code99
{
    enum Days { Sun=2, Mon, Tue, Wed=8, Thu, Fri, Sat }
    internal class Program
    {
        static void Main(string[] args)
        {

            Console.WriteLine((int)Days.Sun);
            Console.WriteLine((int)Days.Mon);
            Console.WriteLine((int)Days.Tue);
            Console.WriteLine((int)Days.Wed);
            Console.WriteLine((int)Days.Thu);
            Console.WriteLine((int)Days.Fri);
            Console.WriteLine(Days.Sat);

        }
    }
}
```
```
namespace Code100
{
    enum TrafficLights { GREEN, RED, YELLOW };
    internal class Program
    {
        static void Main(string[] args)
        {

            //주소를 통한 접근
            for (int i = 0; i < 3; i++)
            {

                Console.WriteLine((TrafficLights)i);
            }
            //인스턴스(객체)를 통한 접근
            TrafficLights r = TrafficLights.RED;
            TrafficLights g = TrafficLights.GREEN;
            TrafficLights y = TrafficLights.YELLOW;
            Console.WriteLine(r);
            Console.WriteLine(g);
            Console.WriteLine(y);
        }
    }
}
```

## WINDOW FORM 실습 ~~~!!!!!

```
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
            string str;
            str = "당신의 연령은 \n";
            if (radioButton1.Checked == true)
            {
                str = str + radioButton1.Text;
            }
            if (radioButton2.Checked == true)
            {
                str = str + radioButton2.Text;
            }
            if (radioButton3.Checked == true)
            {
                str = str + radioButton3.Text;
            }
            if (radioButton4.Checked == true)
            {
                str = str + radioButton4.Text;
            }
            if (radioButton5.Checked == true)
            {
                str = str + radioButton5.Text;
            }
            if (radioButton6.Checked == true)
            {
                str = str + radioButton6.Text;
            }

            str = str + "\n" + "\n" + "좋아하는 색은" + Environment.NewLine;

            if (checkBox1.Checked == true)
                str = str + checkBox1.Text + Environment.NewLine;
            if (checkBox2.Checked == true)
                str = str + checkBox2.Text + Environment.NewLine;
            if (checkBox3.Checked == true)
                str = str + checkBox3.Text + Environment.NewLine;
            if (checkBox4.Checked == true)
                str = str + checkBox4.Text + Environment.NewLine;
            if (checkBox5.Checked == true)
                str = str + checkBox5.Text + Environment.NewLine;
            if (checkBox6.Checked == true)
                str = str + checkBox6.Text + Environment.NewLine;

            str = str + "입니다.";

            label1.Text = str;
        }

        private void button2_Click(object sender, EventArgs e)
        {
            Dispose();
        }
    }
}
```

***

## 실행결과

![test 13](https://github.com/fkfkfk0406/smartfactory/assets/91593653/86415125-5fa5-447e-90ff-74b8163d6a51)








