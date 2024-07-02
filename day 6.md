## 어제 안한거 오늘 하기

```
1. for 구문
2. while
3. do ~ while
```

```
앞으로 필요할것들
1. 타자 영타 250 ~ 300 이상
2. 오타와의 싸움 (대소문자, 스펠링, 내어쓰기, 들여쓰기 (ctrl + k + f)
```

## 기습 퀴즈

```
구구단 3단을 do ~ while 문으로 작성하시오
```

## 풀이

```
namespace ConsoleApp20
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int i = 1;
            do
            {
                Console.WriteLine($"3 * {i} = {3 * i}");
                i++;
            }while ( i < 10);
        }
    }
}
```

## 기습 퀴즈 2

```
namespace ConsoleApp20
{
    internal class Program
    {
        static void Main(string[] args)
        {

            int i;

            do
            {
                
                Console.WriteLine($"[  메  뉴  선  택  ]");
                Console.WriteLine("1. 데이터베이스 입력");
                Console.WriteLine("2. 데이터베이스 검색");
                Console.WriteLine("3. 데이터베이스 수정");
                Console.WriteLine("4. 데이터베이스 삭제");
                Console.WriteLine("5. 프로그램 종료");

                Console.Write("선택 : ");
                i = Int32.Parse(Console.ReadLine());


                switch (i)
                {
                    case 1:
                        Console.WriteLine("데이터베이스 입력을 선택하셨습니다.");
                        Console.WriteLine();
                        break;
                    case 2:
                        Console.WriteLine("데이터베이스 검색을 선택하셨습니다.");
                        Console.WriteLine();
                        break;
                    case 3:
                        Console.WriteLine("데이터베이스 수정을 선택하셨습니다.");
                        Console.WriteLine();
                        break;
                    case 4:
                        Console.WriteLine("데이터베이스 삭제를 선택하셨습니다.");
                        Console.WriteLine();
                        break;
                    case 5:
                        Console.WriteLine("프로그램을 종료합니다.");
                        break;
                    default:
                        Console.WriteLine("잘못 입력 하셨습니다");
                        Console.WriteLine();
                        break;
                }
            }
            while (i != 5);
        }
    }
}
```


