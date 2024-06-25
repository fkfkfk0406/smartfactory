***
1일차
***
- 적절한 마인드셋 확립
- 열심히 하자
- C# 은 많이 안 만져봤는데 열심히 해야겠다 진짜 
***

1. C# 기초 구동
실행하는 방법 및 프로젝트 생성 방법 등 수업에 활용할 수 있는 기초적인 부분을 배움.
***
2. C# 활용
INT, STRING, LONG 등의 함수를 지정 해밨음.

EX)
<pre>
<code>
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp5
{
    class MainClass
    {
         Void Main(string[] args) <------ string Main(~~ , long Main(~~~, int Main(~~~~
        {
            return 100;
        }
    }
}
</code>
</pre>
***

3. Hello world
이제 본격적인 코딩의 시작이다.

<pre>
<code>
namespace ConsoleApp5
{
    class MainClass
    {
         static void Main(String[] args)
        {
            Console.WriteLine("Hello World!!!");
        }
    }
}
</code>
</pre>
    
***

4. 변수
<pre>
<code>
string name = "홍길동";
Console.WriteLine("안녕하세요.");
Console.WriteLine($"나는 {name} 입니다");
</code>
</pre>

이런식으로 변수를 설정해서 출력도 해보았다.

***

5. MINI QUIZ !!!!!

Q) 
변수를 두개 만듭니다.
string greeet;
string name;

---------------------
반갑습니다.
저는 이순신입니다.


A)
<pre>
<code>
namespace ConsoleApp5
{
    class MainClass
    {
         static void Main(String[] args)
        {
            string greet = "반갑습니다.";
            string name = "이순신";
            Console.WriteLine(greet);
            Console.WriteLine($"저는 {name} 입니다");

        }
    }
}
</pre>
</code>

성공했다 아직까진 쉽다.

<pre>
<code>
namespace ConsoleApp5
{
    class MainClass
    {
         static void Main(String[] args)
        {
            string greet = "반갑습니다.";
            string greet2 = "안녕하세요.";
            string name = "이순신";
            int age = 479;
            Console.WriteLine("{0} {1}", greet,greet2);
            Console.WriteLine($"저는 {name}, {age}살 입니다");

        }
    }
}
</code>
</pre>

이런식으로 다른 방식도 시도 해봤다.

***

6. 컴파일러
-> 사람이 읽고 쓸 수 있는 언어로 작성한 코드 --해석-->> 컴퓨터가 편하게 읽을 수 있는 언어로 작성한 코드

***

7. MINI QUIZ 2 !!!!!!

Q) 500 - 300을 변수를 이용하여 결과를 출력하라.
A) 
<pre>
<code>
namespace ConsoleApp6
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int x = 500;
            int y = 300;
            int z = x - y;
            Console.WriteLine(z);
        }
    }
}
</code>
</pre>


Q2) 너비와 높이를 입력받아서 넓이를 구하라,,!!!!
A) 
<pre>
<code>
namespace ConsoleApp6
{
    internal class Program
    {
        static void Main(string[] args)
        {    
            //1. 변수 선언 및 입력부
            Console.Write("너비를 입력해주세요 : ");
            int width = int.Parse(Console.ReadLine());
            Console.Write("높이를 입력해주세요 : ");
            int height = int.Parse(Console.ReadLine());

            //2. 알고리즘 수식
            int result = width * height;

            //3. 출력부
        
            Console.WriteLine($"넓이는 {result} 입니다." );   
        }
    }
}
</code>
</pre>


Q3) 너비와 높이를 입력받아 삼각형의 넓이를 구하라,,!!!!
A) 
<pre>
<code>
namespace ConsoleApp6
{
    internal class Program
    {
        static void Main(string[] args)
        {
            //1. 변수선언 및 입력부
            Console.WriteLine("너비를 입력 하세요 : ");
            int width = int.Parse(Console.ReadLine());
            Console.WriteLine("높이를 입력 하세요 : ");
            int height = int.Parse(Console.ReadLine());
            //2. 알고리즘 수식
            int result = (width * height) / 2;
            //3. 출력부
            Console.WriteLine($"넓이는 {result} 입니다.");
        }
    }
}
</code>
</pre>

A2) 소수점까지 표현 해보았다.
<pre>
<code>
namespace ConsoleApp6
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("너비를 입력 하세요 : ");
            int width = int.Parse(Console.ReadLine());
            Console.WriteLine("높이를 입력 하세요 : ");
            int height = int.Parse(Console.ReadLine());
            double result = (width * height) / 2.0 ;    
            Console.WriteLine($"넓이는 {result} 입니다.");
        }
    }
}
</code>
</pre>

// double result = (width * height) / 2.0 ;  
-> 결과값으로 소수점까지 표현하기위해 double 을 사용함, 그리고 나눠주는값을 실수값으로 바꿈
