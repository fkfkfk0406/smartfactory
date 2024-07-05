## 랜덤 함수 사용

## 시험점수 평균을 랜덤으로 구하기
```
using System;
using System.Diagnostics.CodeAnalysis;
using System.Globalization;
using static System.Runtime.InteropServices.JavaScript.JSType;

namespace ConsoleApp32
{

    internal class Program
    {
        static void Main(string[] args)
        {
            Random random = new Random();

            //kor, eng, math 성적을 Random을 사용하여 받고 평균만 출력
            int[] scores = new int[3];
            int total = 0;
            double avg = 0.0;

            for(int i = 0; i < 3; i++)
            {
                scores[i] = random.Next(1, 101);
                total += scores[i];
                Console.WriteLine(scores[i]);
            }
            avg = (double)total / scores.Length;

            Console.WriteLine($"평균 : {avg:F2}");
        }
    }
}
```
## 로또번호 랜덤으로 받기
```
using System;
using System.Diagnostics.CodeAnalysis;
using System.Globalization;
using static System.Runtime.InteropServices.JavaScript.JSType;

namespace ConsoleApp32
{

    internal class Program
    {
        static void Main(string[] args)
        {
            Random random = new Random();
            for(int i = 1; i < 7; i++) 
            Console.WriteLine(random.Next(1, 46));
        }
    }
}
```
## 로또번호구하기(시험에나올지도,,,?)
```
1단계



중복허용을 합니다.



로또번호 6자리와 

보너스 번호 1자리를 출력해 주세요.



--------------------------------------

로또번호 : 30 21 2 2 5 44

보너스번호: 7





2단계



1) 중복허용이 되지않습니다.

2) 로또번호를 정렬해서 출력해 주세요



--------------------------------------

로또번호 : 7 14 22 35 37 45

보너스번호: 13

```

```
using System;
using System.Diagnostics.CodeAnalysis;
using System.Globalization;
using static System.Runtime.InteropServices.JavaScript.JSType;

namespace ConsoleApp32
{

    internal class Program
    {
        static void Main(string[] args)
        {
            //1단계 중복허용
            Console.Write("로또번호 : ");

            Random random = new Random();
            for (int i = 1; i < 7; i++)
            {
                Console.Write($"{random.Next(1, 46)} ");
            }
            Console.WriteLine($"\n보너스 번호 : {random.Next(1, 46)}");

            //2단계 중복안돼
            Console.Write("로또번호 : ");
            int[] lotto = new int[7];
            for (int i = 1; i < 7; i++)
            {
                lotto[i] = random.Next(1, 46);
                for (int j = 0; j < i; j++)
                {
                    if (lotto[i] == lotto[j])
                    {
                        i--;
                        break;
                    }
                }
            }

            int BonusNumber = lotto[6];
            int[] lottoNumber = new int[6];
            Array.Copy(lotto, 0, lottoNumber, 0, 6);

            Array.Sort(lottoNumber);
            foreach (int i in lottoNumber)
            {
                Console.Write(i + " ");
            }
            Console.WriteLine($"\n보너스 번호 : {BonusNumber}");
        }
    }
}
```
```
using System;
using System.Diagnostics.CodeAnalysis;
using System.Globalization;
using static System.Runtime.InteropServices.JavaScript.JSType;

namespace ConsoleApp32
{

    internal class Program
    {
        static void Main(string[] args)
        {
            Random random = new Random(); 
            List<int> lottoNumberList = new List<int>();

            Console.Write("로또번호 : ");    

            while (lottoNumberList.Count < 7)
            {
                int number = random.Next(1, 46);

                //중복체크
                if (!lottoNumberList.Contains(number))
                {
                    lottoNumberList.Add(number);
                }
            }
            //보너스 번호 뽑기 0번지 첫번째 요소를 보너스 번호로 하자.
            int BonusNumber = lottoNumberList[0];
            lottoNumberList.RemoveAt(0);

            //로또번호 6개만 정렬
            lottoNumberList.Sort();

            foreach(int i in lottoNumberList)
            {
                Console.Write(i + " ");
            }
            Console.WriteLine();

            Console.WriteLine($"보너스 번호 : {BonusNumber}");
        }
    }
}
```
```
using System;
using System.Diagnostics.CodeAnalysis;
using System.Globalization;
using static System.Runtime.InteropServices.JavaScript.JSType;

namespace ConsoleApp32
{

    internal class Program
    {
        static void Main(string[] args)
        {

            Random random = new Random();
            HashSet<int> lottoNumber = new HashSet<int>();
            Console.Write("로또 번호 : ");

            while(lottoNumber.Count < 6)
            {
                int number = random.Next(1, 46);
                lottoNumber.Add(number);
            } // 로또번호 6개 만들기 끝
            //보너스번호
            int bousNumber;
            do
            {
                bousNumber = random.Next(1, 46);
            } while (lottoNumber.Contains(bousNumber));
            //출력
            //로또번호
            foreach(int number in lottoNumber)
            {
                Console.Write(number + " ");
            }
            //뽀나쓰
            Console.WriteLine($"\n보너스 번호 : " + bousNumber);
        }
    }
}
```
하 개어렵다.;;;

***

## 버블정렬 구하기
```
namespace bubblesort
{
    internal class Program
    {
        static void Main(string[] args)
        {

            int[] list = { 4, 5, 7, 3, 2, 1, 9, 8 };
            int temp;
            for(int i = 8-1; i > 0; i--)
            {
                for(int k = 0; k < i; k++)
                {
                    if (list[k] > list[k+1])
                    {
                        temp = list[k];
                        list[k] = list[k+1];
                        list[k+1] = temp;
                    }
                }
            }
            foreach(int i in list)
                Console.WriteLine(i);
        }
    }
}
```

## property 연습

```
namespace Property02
{
    class Person
    {
        public string Name{ get; set; }

        public void SetName(string value)
        {
            if(string.IsNullOrEmpty(value))
            {
                throw new ArgumentNullException("이름이 입력되지 않았습니다.");
            }
            Name = value;
        }
      
    }
    internal class Program
    {
        static void Main(string[] args)
        {

            Person person = new Person();
            person.SetName("hong kill dong");
            Console.WriteLine(person.Name);

        }
    }
}
```
## 소멸자 생성자 
```
namespace ConsoleApp33
{
    class Person
    {
        public Person()
        {
            Console.WriteLine("디폴트 생성자 호출");
        }

        ~Person()
        {
            Console.WriteLine("소멸자 호출");
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {

            Person person = new Person();

        }
    }
}
```
## 연습 연습,,
```
namespace ConsoleApp34
{
    class User
    {
        private readonly string userID; //상수처리
        private readonly string userPW; //상수처리

        public User(string userID, string userPW)
        {
            this.userID = userID;
            this.userPW = userPW;
        }
        public void Print()
        {
            Console.WriteLine(this.userID);
            Console.WriteLine(this.userPW);
        }
    }

    internal class Program
    {
        static void Main(string[] args)
        {
            string uID = "ABC";
            string uPW = "abc";

            User user = new User(uID, uPW);
            user.Print();

        }
    }
}
```

## 퀴즈
```
Q)
세 정수를 70 ~ 100 사이의 값 3개를 랜덤으로 받아
int[] score = new[3];

----------------------------------------------
총점 -> score.Sum()
가장 높은 점수 ->
가장 낮은 점수 ->
평균 점수 ->
```

```
namespace ConsoleApp35
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Random random = new Random();
            int[] score = new int[3];
            for (int i = 0; i < 3; i++)
            {
                score[i] = random.Next(70, 101);
                Console.WriteLine(score[i]);
            }


            Console.WriteLine($"총합 : {score.Sum()}");
            Console.WriteLine($"가장 높은 점수 : {score.Max()}");
            Console.WriteLine($"가장 낮은 점수 : {score.Min()}");
            Console.WriteLine($"평균 : {score.Average():F2}");

        }
    }
}
```

아주 조금 이해됨....

***


