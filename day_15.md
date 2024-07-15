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
        public string brand { get; set; }
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
