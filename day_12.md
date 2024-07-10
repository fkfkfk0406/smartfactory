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
            int[] numbers = new int[8];

            for(int i = 1; i <= 8; i++)
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
            names[0] = Console.ReadLine();
            names[1] = Console.ReadLine();
            names[2] = Console.ReadLine();

            for (int i = 0; i < names.Length; i++)
            {
                Console.WriteLine(names[i]);
            }
        }
    }
}
```
