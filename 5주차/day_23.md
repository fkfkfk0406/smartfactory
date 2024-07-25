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

