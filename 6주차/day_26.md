## 26일차~
```
OOP
1. 캡슐화 (Encapsulation)
  - 객체(OBJECT) -> 인스턴스(INSTANCE)
  - 객체를 만드는것 클래스(CLASS)
    -클래스의 구성
    - clas Lion
    - { 멤버변수 -- 속성, 변수 -> 명사
    -   멤버메소드 -- 액션, 메소드 -> 동사
    -   -생성자도 멤버 메소드에 속한다.
    - }

2. 다형성 (Polymorphism)
  - 오버로딩 (생성자 만들기 패턴?)
  - 오버라이딩 --> ToString? --> 메소드 재정의!!
              --> Shape     --> Draw() 메소드 생각!!

3. 상속(Inheritance)
  - 상속 하기 위한 키워드(:)
  - : object 최종 부모클래스 상속은 표현이 생략가능

  - Is - A 관계, Has - A 관계(??)

4. Wrapper Class
  - Boxing, UnBoxing

  -> char, float 기본타입에 대한 Wrapper Class를 이용해 값을 서로 교환해 봅시다.
      int number = 42; //값 타입, 기본타입
      Int32 boxed = number // WrapperClass(Int32)
                          // Boxing
      int unboxed = boxed // Unboxing

      object obj = number // UpCasting
      int downed = (int)obj // DownCasting

5. String 복습
  - StringBuilder 복습

6. 인터페이스(Interface), 추상 클래스(Abstract Class)
  - 추살 클래스는 개념적으로만 존재

7. 깊은복사(Deep Copy), 얇은 복사(Shallow Copy)
```

## StringBuilder 실습
```

using System.Text;

public partial class Program
{
    public static void Main()
    {
        string str1 = "Hello World";
        string str2 = new string("Hello World");
        string str3 = "Hello World";
        string str4 = "Hello World";
        string str5 = new string("Hello World");

        object obj1 = new object();
        object obj2 = new object();

        StringBuilder sb1 = new StringBuilder("Hello World");
        StringBuilder sb2 = new StringBuilder("Hello World");

        Console.WriteLine($"str1 : {str1.GetHashCode()}");
        Console.WriteLine($"str2 : {str2.GetHashCode()}");
        Console.WriteLine($"str3 : {str3.GetHashCode()}");
        Console.WriteLine($"str4 : {str4.GetHashCode()}");
        Console.WriteLine($"str4 : {str5.GetHashCode()}");
        Console.WriteLine();

        Console.WriteLine($"obj1 : {obj1.GetHashCode()}");
        Console.WriteLine($"obj2 : {obj2.GetHashCode()}");
        Console.WriteLine();

        Console.WriteLine($"sb1 : {sb1.GetHashCode()} {sb1.ToString()}");
        Console.WriteLine($"sb2 : {sb2.GetHashCode()} {sb2.ToString()}");
    }
}
```

## Boxing 실습
```

public partial class Program
{
    public static void Main()
    {
        int number = 42;
        Int32 boxed = number; //Boxing
        int unboxed = boxed; //UnBoxing

        object obj = number; //UpCasting, Boxing
        int downed = (int)obj; //강제형변환, DownCasting


    }
}
```

## 얕은복사 깊은복사 실습
```
using System;

namespace DeepCopy
{
    class MyClass
    {
        public int MyField1;
        public int MyField2;

        public MyClass DeepCopy()
        {
            MyClass newCopy = new MyClass();
            newCopy.MyField1 = this.MyField1;
            newCopy.MyField2 = this.MyField2;

            return newCopy;
        }
    }

    class MainApp
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Shallow Copy");

            {
                MyClass source = new MyClass();
                source.MyField1 = 10;
                source.MyField2 = 20;

                MyClass target = source;
                target.MyField2 = 30;

                Console.WriteLine($"{source.MyField1} {source.MyField2}");
                Console.WriteLine($"{target.MyField1} {target.MyField2}");
            }

            Console.WriteLine("Deep Copy");

            {
                MyClass source = new MyClass();
                source.MyField1 = 10;
                source.MyField2 = 20;

                MyClass target = source.DeepCopy();
                target.MyField2 = 30;

                Console.WriteLine($"{source.MyField1} {source.MyField2}");
                Console.WriteLine($"{target.MyField1} {target.MyField2}");
            }
        }
    }
}
```


    

