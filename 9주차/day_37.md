## 수업시작,,,
어번주 토요일엔 토이스피킹 시험을 쳤다..!!

##네트워크 실습
![image](https://github.com/user-attachments/assets/9053efbe-fc61-4f48-b011-0b173b1c3a5a)


## 스레드 실습
![image](https://github.com/user-attachments/assets/a0541d8b-26ab-4cea-95d1-5348447cf653)



## 스레드 실습 2
![image](https://github.com/user-attachments/assets/abcd3362-d920-404e-b2b2-aa02c90b5f18)



## 스레드 실습 3
![image](https://github.com/user-attachments/assets/b9ffd731-feff-44ae-9ac0-087214f8f252)



## 스레드 퀴즈
```
namespace threadError
{
    class Program
    {
        private static readonly object lockObject = new object();
        static int sharedValue = 0;

        static void Main(string[] args)
        {
            Thread incrementThread = new Thread(Increment);
            Thread decrementThread = new Thread(Decrement);

            // 스레드 시작
            incrementThread.Start();
            decrementThread.Start();

            // 스레드가 종료되기를 기다림
            incrementThread.Join();
            decrementThread.Join();

            Console.WriteLine($"최종 값: {sharedValue}");
        }

        static void Increment()
        {
            lock (lockObject)
            {

                for (int i = 0; i < 100000; i++)
                {
                    sharedValue++;
                }
            }
        }

        static void Decrement()
        {
            lock (lockObject)
            {
                for (int i = 0; i < 100000; i++)
                {
                    sharedValue--;
                }
            }
        }
    }
}
```
기존 코드를 수정해서 항상 0이 나오도록 했다.
***
## FileStream 사용
![image](https://github.com/user-attachments/assets/7a5df167-0ef9-4d2f-b5e8-7dbcf8100fbc)



## 서버-클라이언트 에코 실습
![image](https://github.com/user-attachments/assets/9f706444-bd16-4a9e-9df8-c7924bb5825a)



