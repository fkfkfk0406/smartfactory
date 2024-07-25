## 23일차~~
```
C# 기본문법 정리
1. 데이터타입(TYPE)및 변수
  - 기본타입(TYPE)
  - 사용자 정의 타입(CLASS)

  <변수>
  - 정수형 변수
  - 포인터형 변수

2. 메소드
  - CALL BY VALUE / CALL BY REFERENCE (SWAP 메소드)
  - 메소드의 RETURN과 RETURN TYPE
  - Void Print() {}
  - int Print(int a, int b)
    {
      return 100;
    }
  - 메소드의 매개변수(파라미터, 인자값)를 통해서 값들을 전달 할 수 있다.
3. 연산자
  - +, -, *, /, <, >, >=, ++, ()
  - 연산자들은 우선순위가 있다.
4. 조건문
  -if else, switch ~ case
5. 반복문
  - for, while
  - foreach (객체 반복 순환에 유리)
6. 배열, 컬렉션(List, ArrayList, Stack<int> ...)
  - 배열의 이름은 포인터
  - int[] arr1 = new int[5];
  - char[] arr2 = new char[3] {a, b, c,} (선언과 동시 초기화)
  - Person[] arr3 = new Person[1];
  - Person person = new Person();
  - arr3.Add(person)

  - List<T>, Dictionary<T>
  - Stack<T>
    -push(), pop(), top, empty
  - Queue<T>
    -Enqueue(), Dequeue()
  - HashTable
    -Key(키), Value(값)
  - ArrayList,
7. 예외처리
  - try ~ catch, finally
    - FrameWork 개발자가 아닌 사용하는
      프로그래머나 사용자의 문제 때문에 발생하는 문제 !
  -리소스 관리
    - using
      - IDispoable 인터페이스를 구현
      - 블록을 벗어나면 Dispose 메서드가 자동 호출
8. LINQ(Language Integrated Query)
10. Lamda식
  - 메서드 사용의 짧은 표현
  - Lamda 전용 델리게이트
    - Actioin
      - 반환 형식이 없다. return 없음
    - Func
      - 반환 형식이 있다. return 있음
```
## 퀴즈
```
국어,  영어, 수학 성적을 



배열로 입력받아 

---> 입력받는 부분을 메소드로 처리해주세요.

InputScore( ) 메소드 만들어서 사용

OutputScore() 메소드 만들기

총점과 평균(소수점 둘째자리)까지 출력하는

프로그램을 작성하라.

단, 총점은 배열의 4번째 요소에 입력해 놓으세요.

------------------------------------

국어 : 100

영어 : 100

수학 : 100



총점 : 300

평균 : 100
```
## 풀이
```
using System.ComponentModel.Design;

namespace ConsoleApp61
{
    class Score
    {
        public int[] InputScore(int[] arr)
        {
            int total = 0;
            for (int i = 0; i < 3; i++)
            {
                arr[i] = int.Parse(Console.ReadLine());
                total += arr[i];
            }
            arr[3] = total;
            return arr;
        }
        public void OutputScore(int[] arr)
        {
            Console.WriteLine("총점 : " + arr[3]);
            Console.WriteLine($"평균 : {arr[3] / 3.0:F2}");
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {
            int[] arr = new int[4];
            Score score = new Score();

            score.InputScore(arr);
            score.OutputScore(arr);
        }
    }
}
이게 기초가 되어버렸다;;; 안하니까 어려움 복습 더해야겠다.
```
***
## 실습
```
using System.Collections;

namespace listApp
{
    internal class Program
    {
        static void Main(string[] args)
        {

            List<int> list = new List<int>();
            list.Add(1);
            list.Add(2);
            list.Add(3);

            foreach (int i in list)
            {
                Console.WriteLine(i);
            }
            ArrayList alist = new ArrayList();
            alist.Add('A');
            alist.Add('B');
            alist.Add('C');

            alist.Insert(2, 'E');
            alist.RemoveAt(0);

            foreach (char ch in alist)
            {
                Console.WriteLine(ch);
            }

            ArrayList blist = new ArrayList();
            blist.Add(1);
            blist.Add('Z');
            Console.WriteLine((int)blist[0]);
            Console.WriteLine((char)blist[1]);
        }
    }
}


```
![화면 캡처 2024-07-25 101350](https://github.com/user-attachments/assets/32716c29-2c24-437f-b8ee-193a25938d83)
## STACK
```
namespace StackTest
{
    internal class Program
    {
        static void Main(string[] args)
        {
            
            Stack<int> stack = new Stack<int>();

            stack.Push(1);
            stack.Push(2);
            stack.Push(3);

            foreach (int i in stack)
            {
                Console.WriteLine(stack.Pop());
            }
        }
    }
}
출력 결과 : 3
```
```
namespace StackTest
{
    internal class Program
    {
        static void Main(string[] args)
        {
            
            Stack<int> stack = new Stack<int>();

            stack.Push(1);
            stack.Push(2);
            stack.Push(3);

            while(stack.Count > 0)
            {
                Console.WriteLine(stack.Pop());
            }
        }
    }
}
출력 결과
3
2
1
```
## QUEUE
```
namespace queuetestapp
{
    internal class Program
    {
        static void Main(string[] args)
        {

            Queue<string> que = new Queue<string>();
            que.Enqueue("사과");
            que.Enqueue("딸기");
            que.Enqueue("배");

            while(que.Count > 0)
            {
                Console.WriteLine(que.Dequeue());
            }
        }
    }
}

출력 결과
사과
딸기
배
```
## HashTable
```
using System.Collections;

namespace HashTableApp
{
    internal class Program
    {
        static void Main(string[] args)
        {

            Hashtable ht = new Hashtable();

            ht["하나"] = "one";
            ht["둘"] = "two";
            ht["셋"] = "three";
            ht["넷"] = "four";

            Console.WriteLine(ht["하나"]);
            Console.WriteLine(ht["둘"]);
            Console.WriteLine(ht["셋"]);
            Console.WriteLine(ht["넷"]);

        }
    }
}

출력 결과
one
two
three
four
```
## 예외처리
```
namespace exception
{
    internal class Program
    {
        static void Main(string[] args)
        {

            int a = 5;
            int b = 3;
            try
            {
                int result = a / b;
                Console.WriteLine(result);
            }
            catch (DivideByZeroException ex)
            {
                Console.WriteLine("0으로 나누어 예외가 발생했씁니다.");
            }
            catch (Exception ex)
            {
                Console.WriteLine("예외가 발생 했습니다");
            }
            finally
            {
                Console.WriteLine("무조건 실행되는 구문");
            }
        }
    }
}
```
```
namespace Exception2
{
    internal class Program
    {
        static void Main(string[] args)
        {

            int[] arr = { 1, 2, 3 };
            try
            {
                for (int i = 0; i < 5; i++)
                {
                    Console.WriteLine(arr[i]);
                }
            }
            catch (Exception ex)
            {
            }
            Console.WriteLine("종료");
        }
    }
}
아무것도 안하는것도 예외다~~
```
![화면 캡처 2024-07-25 112227](https://github.com/user-attachments/assets/bde03023-713e-4df2-b572-b30366fbfc92)
***
## FILE 함수
파일 작성



![화면 캡처 2024-07-25 113253](https://github.com/user-attachments/assets/f1340886-5345-4468-bc0f-4e0b70b90669)
***
```
파일을 읽고 파일을 잘못 읽었을때에 예외처리를 해줌

namespace filetest
{
    internal class Program
    {
        static void Main(string[] args)
        {

            string path = "c:\\Temp\\abc.txt";
            string content = "안녕하세요 C#~~~~!";

            File.WriteAllText(path, content);
            Console.WriteLine("파일작성 성공~~");

            // 읽기
            try
            {
                string path2 = "c:\\Temp\\ccc.txt";
                string words = File.ReadAllText(path2);
                Console.WriteLine(words);
            }
            catch (Exception ex)
            {
                Console.WriteLine("파일의 이름이 잘못됨");
            }
        }
    }
}
```
```
namespace filetest02
{
    internal class Program
    {
        static void Main(string[] args)
        {

            string path = @"c:\Temp\hello.txt";
            string content = "안녕하세요, 인사파일입니다.";

            using (StreamWriter writer = new StreamWriter(path))
            {
                writer.WriteLine(content);
                //writer.Close(); //close를 할때 write 됨
            }

            Console.WriteLine("현재 프로그램을 종료합니다.");

        }
    }
}
StreamWriter 객체에서 writer.Close()를 명시적으로 호출하지 않아도 잘 작동하는 이유는 using 문을 사용했기 때문입니다.
using 문이 종료되면 StreamWriter 객체의 Dispose 메서드가 자동으로 호출되어 스트림이 닫히고, 리소스가 해제됩니다.
```
## 프로그래머스 문제 풀기
```
할일 목록
using System.ComponentModel.Design;
using System.Security.Cryptography;

namespace ConsoleApp62
{
    internal class Program
    {
        static string[] solution(string[] todo_list, bool[] finished)
        {
            List<string> newWorkList = new List<string>();
            for(int i = 0; i < todo_list.Length; i++)
            {
                if (!finished[i])
                    newWorkList.Add(todo_list[i]);
            }

            return newWorkList.ToArray(); //리스트를 배열로 변경하는 메소드~
        }

        static void Main(string[] args)
        {
            string[] todo_list = { "problemsolving", "practiceguitar", "swim", "studygraph" };
            bool[] finished = { true, false, true, false };

            string[] list = solution(todo_list, finished);

            foreach (string s in list)
            {
                Console.WriteLine(s);
            }
        }
    }
}
```
```
5명씩
using System.ComponentModel.Design;
using System.Reflection.Metadata.Ecma335;

namespace ConsoleApp63
{
    internal class Program
    {
        static string[] solution(string[] names)
        {
            List<string> result = new List<string>();
            for (int i = 0; i < names.Length; i += 5)
            {
                result.Add(names[i]);
            }
            return result.ToArray();
        }
        static void Main(string[] args)
        {
            string[] names = { "nami", "ahri", "jayce", "garen", "ivern", "vex", "jinx" };
            string[] list = solution(names);
            foreach (string s in list)
            {
                Console.Write(s + " ");
            }
        }

    }
}
```
## LinQ (Language Integrated Query)
![화면 캡처 2024-07-25 141443](https://github.com/user-attachments/assets/b5aad907-fd3f-44f7-8863-1c54eb73b5d4)
***
```
namespace LinQ01
{
    internal class Program
    {
        static void Main(string[] args)
        {

            int[] numbers = { 9, 2, 6, 4, 5, 3, 7, 8, 1, 10};
            var result = from n in numbers
                         where n % 3 == 0
                         orderby n descending
                         select n;
            foreach(int n in result)
            {
                Console.WriteLine(n + " ");
            }
            Console.WriteLine();
        }
    }
}
3의 배수를 오름차순으로 출력해봤다.
```
## QUIZ
```
LINQ를 사용해서 알파벳을 역순으로 출력하삼
-------------------------------------------------------
namespace LinQQuiz
{
    internal class Program
    {
        static void Main(string[] args)
        {
            char[] alphabets = new char[26];
            for(int i = 0; i < alphabets.Length; i++)
            {
                alphabets[i] = (char)('A' + i);
            }
            var result = from a in alphabets
                         orderby a descending
                         select a;
            foreach(char c in result)
            {
                Console.Write(c + " ");
            }
            Console.WriteLine();
        }
    }
}
```
## LINQ 실습
```
using System.Data;
using System.Net.WebSockets;
using System.Text.RegularExpressions;

namespace LinqExam03
{
    //p624
    class Person
    {
        public string Name { get; set; }
        public int Age { get; set; }
        public string Address { get; set; }

        public Person(string name, int age, string address)
        {
            Name = name;
            Age = age;
            Address = address;
        }
        public override string ToString()
        {
            return string.Format($"{Name}{Age}{Address}");
        }
    }
    class MainLanguage
    {
        public string Name { get; set; }
        public string Language { get; set; }

        public MainLanguage(string name, string language)
        {
            Name = name;
            Language = language;
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {
            List<Person> people = new List<Person>
            {
                new Person("Tom", 63, "Korea"),
                new Person("Winnie", 40, "Tibet"),
                new Person("Anders", 47, "Sudan"),
                new Person("Hans", 25, "Tibet"),
                new Person("Eureka", 32, "Sudan"),
                new Person("Hawk", 15, "Korea")
            };

            List<MainLanguage> languages = new List<MainLanguage>
            {
                new MainLanguage("Anders", "Delphi"),
                new MainLanguage("Anders", "C#"),
                new MainLanguage("Tom", "Borland C++"),
                new MainLanguage("Hans", "Visual C++"),
                new MainLanguage("Winnie", "R")
            };
            //var all = from person in people
            //          select person;
            //foreach (var item in all)
            //{
            //    Console.WriteLine($"{item.Name}: {item.Age} in {item.Address}");
            //}
            //Console.WriteLine(string.Join(Environment.NewLine, all));

            //var nameList = from person in people 
            //               select person.Name;
            //foreach(var item in nameList)
            //{
            //    Console.WriteLine(item);
            //}

            //var nameList = people.Select((elem) => elem.Name); //확상메서드표현 Lamda식
            //foreach(var name in nameList)
            //{
            //    Console.WriteLine(name);
            //}

            //var dataList = from person in people
            //               select new
            //               {
            //                   Name = person.Name,
            //                   Year = DateTime.Now.AddYears(-person.Age).Year
            //               };
            //foreach(var item in dataList)
            //{
            //    Console.WriteLine($"{item.Name} - {item.Year}");
            //}

            //group by, Join
            var ageOver30 = from person in people
                            where person.Age > 30
                            select person;
            var addGroup = from person in people
                           group person by person.Address;
            foreach (var itemgroup in addGroup)
            {
                Console.WriteLine($"[{itemgroup.Key}]");
                foreach(var item in itemgroup)
                {
                    Console.WriteLine(item);
                }
                Console.WriteLine();
            }
        }
    }
}
```
![화면 캡처 2024-07-25 154937](https://github.com/user-attachments/assets/734a50ed-242e-4539-bde3-a26dabaf7896)



![화면 캡처 2024-07-25 154953](https://github.com/user-attachments/assets/34c0b38b-9b2a-481d-a402-b2c8a68d2538)
***
## Lamda
```
namespace LamdaTest01
{
    class Calculator
    {
        public int Plus(int a, int b)
        {
            return a + b;
        }
    }
    internal class Program
    {
        delegate int Calculate(int a, int b);
        static void Main(string[] args)
        {
            Calculate calc = (int a, int b) => a + b;
            //Calculate cal = delegate (int a, int b)
            //{
            //    return a + b;
            //};
            Console.WriteLine(calc(100, 200));
            //Console.WriteLine(cal(100, 200));
        }
    }
}
```
```
namespace LamdaExam02
{
    internal class Program
    {
        delegate int? MyDivide(int a, int b); // ? = (값에 null이 들어갈 수 있다)
        static void Main(string[] args)
        {
            //Thread thread = new Thread(
            //    (obj) => Console.WriteLine("~~~~~~~~~~")
            //    );
            MyDivide myFunction = (a, b) =>
            {
                if (b == 0)
                    return null;
                return a / b;
            };
        }
    }
}
```
Lamda 전용 델리게이트인 Action과 Func



![화면 캡처 2024-07-25 164256](https://github.com/user-attachments/assets/f4a8f79d-d141-49ff-b4c1-7fe8b43b995a)
***
![화면 캡처 2024-07-25 165330](https://github.com/user-attachments/assets/5df805f5-a254-47af-ba33-aeaedf0ba0e3)



Action을 아주 쉽게 설명한것임~~~~
***









