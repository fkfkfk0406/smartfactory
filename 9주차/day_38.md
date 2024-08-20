### 피곤하다
### 아침 퀴즈
```
https://github.com/HaSense/CSharp/tree/master/Network 
A16.SimpleTCPServer_using.cs 를 서버로 사용하세요.
A17.SimpleClient는 주고 받는 형식으로 되어 있어야 A16서버랑 통신을 하는데
패킷을 받기만 하는 코드로 되어있습니다.
A17.SimpleClient 코드를 수정하여 두 프로그램이 서로 통신이 되게 만들어 보세요!!!!
```
### 풀이
```
서버 예제 코드)

using System;
using System.Net;
using System.Net.Sockets;
using System.Text;

class Program
{
    static void Main(string[] args)
    {
        // 서버 소켓 생성
        TcpListener server = null;
        try
        {
            int port = 13000;
            IPAddress localAddr = IPAddress.Parse("192.168.0.19");

            // 서버 소켓 초기화
            server = new TcpListener(localAddr, port);

            // 서버 시작
            server.Start();
            Console.WriteLine("서버가 시작되었습니다. 클라이언트를 기다리는 중...");

            // 클라이언트의 연결을 기다림
            using (TcpClient client = server.AcceptTcpClient())
            {
                Console.WriteLine("클라이언트가 연결되었습니다.");

                // 네트워크 스트림을 통해 데이터를 주고받음
                using (NetworkStream stream = client.GetStream())
                {
                    // 클라이언트로부터 데이터를 읽음
                    byte[] buffer = new byte[256];
                    int bytesRead = stream.Read(buffer, 0, buffer.Length);
                    string receivedMessage = Encoding.UTF8.GetString(buffer, 0, bytesRead);
                    Console.WriteLine("클라이언트로부터 받은 메시지: " + receivedMessage);

                    // 클라이언트에게 메시지 전송
                    string responseMessage = "메시지를 받았습니다.";
                    byte[] responseData = Encoding.UTF8.GetBytes(responseMessage);
                    stream.Write(responseData, 0, responseData.Length);
                    Console.WriteLine("클라이언트에게 응답을 전송했습니다.");
                }
            }
        }
        catch (SocketException e)
        {
            Console.WriteLine("소켓 예외: " + e.ToString());
        }
        finally
        {
            // 서버 소켓을 종료
            if (server != null)
            {
                server.Stop();
            }
        }

        Console.WriteLine("서버를 종료합니다.");
    }
}
```
```
클라이언트 코드)

using System;
using System.Collections.Generic;
using System.Linq;
using System.Net.Sockets;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleTCPClient
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string server = "192.168.0.19";
            int port = 13000;

            TcpClient client = new TcpClient(server, port);

            NetworkStream stream = client.GetStream();

            //보내기
            string greet = "반갑노";
            byte[] message = new byte[256];
            message = Encoding.UTF8.GetBytes(greet);
            stream.Write(message, 0, message.Length);
            Console.WriteLine("보낸 메시지 : " +  greet);


            //받기
            byte[] data = new byte[256];
            int bytes = stream.Read(data, 0, data.Length);
            string responseData = Encoding.UTF8.GetString(data, 0, bytes);
            Console.WriteLine($"Received: {responseData}");

            client.Close();
        }
    }
}
```
## 퀴즈
```
서버/클라이언트 모델로 퀴즈를 맞추는 프로그램을 작성해 봅시다.



퀴즈는 총 3개며 클라이언트가 접속하면 서버는 퀴즈를 클라이언트에게 보여줍니다.



그럼 클라이언트는 1, 2, 3 

3가지 메뉴에 숫자로 답을 할 수 있고 서버로 보낸 숫자를 보고 서버는 정답 여부를 알려줍니다.



문제를 맞추면 두번째 문제가 나가고 총 3개 문제를 맞추면 우승, 중간에 실패하면 "다음기회에..." 



메시지를 받습니다. 



Socket API 방식으로 구현해 보세요!!!.





화면 예

Server

----------------------------------------

퀴즈 서버가 시작되었습니다... 



Client

----------------------------------------

문제 1: C#의 창시자는?

1. Anders Hejlsberg

2. James Gosling

3. Bjarne Stroustrup

정답을 입력하세요 (1, 2, 3):

1

정답입니다!

문제 2: HTTP의 기본 포트 번호는?

1. 21

2. 80

3. 443

정답을 입력하세요 (1, 2, 3):

2

정답입니다!

문제 3: OOP에서 상속을 제공하는 키워드는?

1. class

2. interface

3. extends

정답을 입력하세요 (1, 2, 3):

3

정답입니다!

축하합니다! 모든 문제를 맞추셨습니다. 우승하셨습니다!



client2
------------------------------------------------------------------------
문제 1: C#의 창시자는?

1. Anders Hejlsberg

2. James Gosling

3. Bjarne Stroustrup

정답을 입력하세요 (1, 2, 3):

2

오답입니다. 다음 기회에 도전하세요.


```
## 풀이
```
서버)









using System;

using System.Net;

using System.Net.Sockets;

using System.Text;

using System.Threading;



namespace MultiThread_Console_Server_v4

{

    internal class Program

    {

        static int cnt = 0;

        static void Main(string[] args)

        {

            Thread serverThread = new Thread(serverFunc);

            serverThread.IsBackground = true;

            serverThread.Start();



            serverThread.Join();

            Console.WriteLine("서버 메인 프로그램 종료!!!");

        }



        private static void serverFunc(object obj)

        {

            using (Socket srvSocket = new Socket(AddressFamily.InterNetwork, SocketType.Stream, ProtocolType.Tcp))

            {

                IPEndPoint endPoint = new IPEndPoint(IPAddress.Any, 13000);

                srvSocket.Bind(endPoint);

                srvSocket.Listen(50);



                Console.WriteLine("서버 시작...");

                while (true)

                {

                    Socket cliSocket = srvSocket.Accept();

                    cnt++;



                    Thread workThread = new Thread(new ParameterizedThreadStart(workFunc));

                    workThread.IsBackground = true;

                    workThread.Start(cliSocket);

                }

            }

        }



        private static void workFunc(object obj)

        {

            Socket cliSocket = (Socket)obj;

            string[] questions = {

                "C#의 창시자는?\n1. Anders Hejlsberg\n2. James Gosling\n3. Bjarne Stroustrup",

                "HTTP의 기본 포트 번호는?\n1. 21\n2. 80\n3. 443",

                "OOP에서 상속을 제공하는 키워드는?\n1. class\n2. interface\n3. extends"

            };

            int[] answers = { 1, 2, 3 };



            try

            {

                for (int i = 0; i < questions.Length; i++)

                {

                    // 클라이언트에게 문제 전송

                    byte[] sendBytes = Encoding.UTF8.GetBytes($"문제 {i + 1}: {questions[i]}\n정답을 입력하세요 (1, 2, 3): ");

                    cliSocket.Send(sendBytes);



                    // 클라이언트의 응답 받기

                    byte[] recvBytes = new byte[1024];

                    int nRecv = cliSocket.Receive(recvBytes);

                    string response = Encoding.UTF8.GetString(recvBytes, 0, nRecv).Trim();



                    // 정답 검사

                    if (int.TryParse(response, out int clientAnswer) && clientAnswer == answers[i])

                    {

                        if (i == questions.Length - 1) // 마지막 문제를 맞췄을 때

                        {

                            cliSocket.Send(Encoding.UTF8.GetBytes("축하합니다! 모든 문제를 맞추셨습니다. 우승하셨습니다!\n"));

                            break;

                        }

                        else

                        {

                            cliSocket.Send(Encoding.UTF8.GetBytes("정답입니다!\n"));

                        }

                    }

                    else

                    {

                        cliSocket.Send(Encoding.UTF8.GetBytes("오답입니다. 다음 기회에 도전하세요.\n"));

                        break;

                    }

                }

            }

            catch (Exception e)

            {

                Console.WriteLine($"에러 발생: {e.Message}");

            }

            finally

            {

                cliSocket.Close();

            }

        }

    }

}


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
클라이언트



using System;
using System.Net;
using System.Net.Sockets;
using System.Text;
using System.Threading;

namespace TestSocketClient
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Thread clientThread = new Thread(clientFunc);
            clientThread.Start();
            clientThread.IsBackground = true;
            clientThread.Join();

            Console.WriteLine("클라이언트가 종료되었습니다.");
        }

        static void clientFunc(object obj)
        {
            try
            {
                Socket socket = new Socket(AddressFamily.InterNetwork, SocketType.Stream, ProtocolType.Tcp);
                EndPoint serverEP = new IPEndPoint(IPAddress.Parse("192.168.0.19"), 13000);  // 서버 IP 주소와 포트 번호 설정
                socket.Connect(serverEP);

                while (true)
                {
                    // 서버로부터 문제 받기
                    byte[] recvBytes = new byte[1024];
                    int nRecv = socket.Receive(recvBytes);
                    string question = Encoding.UTF8.GetString(recvBytes, 0, nRecv);
                    Console.WriteLine(question);

                    // 축하 메시지나 오답 메시지를 받은 경우 종료
                    if (question.Contains("우승하셨습니다") || question.Contains("다음 기회에 도전하세요"))
                    {
                        break;
                    }

                    // 클라이언트에서 정답 입력
                    string answer = Console.ReadLine();
                    socket.Send(Encoding.UTF8.GetBytes(answer));
                }

                socket.Close();
            }
            catch (Exception e)
            {
                Console.WriteLine(e.Message);
            }
        }
    }
}
```
