## 너무 덥다
오늘은 서버를 구동해봤다
![image](https://github.com/user-attachments/assets/f0f4e8ef-e26c-4be3-8061-733cca3c81c2)
***
![image](https://github.com/user-attachments/assets/ffde7aac-6cfb-4f1b-a991-2d0b748ba4fd)



연결 성공,,,,!
***
![image](https://github.com/user-attachments/assets/4a353f6a-9a59-4b19-875f-99af906db9a5)



소켓을 이용해서 서버와 클라이언트를 구성해봤삼
```
using System.Net;
using System.Net.Http.Headers;
using System.Net.Sockets;
using System.Text;

namespace SocketTCPServer
{
    internal class Program
    {
        static void Main(string[] args)
        {
            //1. ServerSocket 만들기
            IPAddress localAddr = IPAddress.Parse("192.168.0.19");
            int port = 13000;
            Socket serverSocket = new Socket(AddressFamily.InterNetwork,SocketType.Stream,ProtocolType.Tcp);
            //2. Bind
            serverSocket.Bind(new IPEndPoint(localAddr, port));
            //3. Listen
            serverSocket.Listen(1);
            Console.WriteLine("연결을 기다리는중이삼 , , , , , , ,");
            //4. Accept
            Socket clientSocket = serverSocket.Accept();
            Console.WriteLine("연결 성공 , , , , , , !");
            //5. Read/Write
            string message = "안녕하삼. 클라이언트삼";
            byte[] bytes = new byte[1024];
            byte[] data = Encoding.UTF8.GetBytes(message);

            clientSocket.Send(data);
            Console.WriteLine($"전송한 메시지삼 : {message}");
            //6. Close
            clientSocket.Shutdown(SocketShutdown.Both);
            clientSocket.Close();
        }
    }
}
```
```
using System.Net;
using System.Net.Sockets;
using System.Text;

namespace SocketTCPClient
{
    internal class Program
    {
        static void Main(string[] args)
        {
            //1. Client 소켓만들기, 서버 접속을 위한 소켓 만들기
            IPAddress serverADDr = IPAddress.Parse("192.168.0.19"); //친구 서버 주소
            int port = 13000;
            Socket clientsocket = new Socket(AddressFamily.InterNetwork, SocketType.Stream, ProtocolType.Tcp);
            //2. Connect
            clientsocket.Connect(new IPEndPoint(serverADDr, port));
            Console.WriteLine("서버에 연결 됐삼");
            //3. Read, Write
            byte[] bytes = new byte[1024];
            int byteReceived = clientsocket.Receive(bytes);

            // 받은 메시지 출력
            string message = Encoding.UTF8.GetString(bytes);
            Console.WriteLine($"서버로부터 받으 내용이삼 : {message}");

            //4. Close
            clientsocket.Shutdown(SocketShutdown.Both);
            clientsocket.Close();
        }
    }
}
```
***
![image](https://github.com/user-attachments/assets/1380a182-737b-4313-abc2-69a1d0183d54)



서버를 만들어서  파일을 보내는것도 작성 해봤다.
```
using System.IO;
using System.Net;
using System.Net.Sockets;

namespace PictureSaveServer
{
    internal class Program
    {
        static void Main(string[] args)
        {
            //1. 서버 소켓 만들기, binding, Listening
            TcpListener server = new TcpListener(IPAddress.Any, 13000);
            server.Start();
            Console.WriteLine("서버가 시작 됐삼. 클라이언트 기다리는중이삼");
            //3. accept
            TcpClient client = server.AcceptTcpClient();
            Console.WriteLine("클라이언트가 연결됐삼");
            //5. read, write
                //소켓에서 패킷을 가져오기
                //파일에 저장
            NetworkStream networkStream = client.GetStream();
            //그림파일 수신 및 저장
            using (FileStream fileStream = new FileStream("received_image.png", FileMode.Create, FileAccess.Write))
            {
                byte[] buffer = new byte[1024];
                int bytesRead;

                while ((bytesRead = networkStream.Read(buffer, 0, buffer.Length)) > 0)
                {
                    fileStream.Write(buffer, 0, bytesRead);
                }
            }
            Console.WriteLine("파일 수신 완료.");

            // 연결 종료
            networkStream.Close();
            client.Close();
            server.Stop();
        }
    }
}
```

```
using System.Net.Sockets;

namespace PicturSendClient
{
    internal class Program
    {
        static void Main(string[] args)
        {
            // 서버 IP와 포트 설정
            string serverIp = "192.168.0.19";
            int port = 13000;

            // TCP 클라이언트 생성 및 서버 연결
            TcpClient client = new TcpClient(serverIp, port);
            Console.WriteLine("서버에 연결되었습니다.");

            // 네트워크 스트림 생성
            NetworkStream networkStream = client.GetStream();

            // 전송할 파일 경로 설정
            string filePath = "image_to_send.jpg";

            // 파일 읽기 및 서버로 전송
            using (FileStream fileStream = new FileStream(filePath, FileMode.Open, FileAccess.Read))
            {
                byte[] buffer = new byte[1024];
                int bytesRead;

                while ((bytesRead = fileStream.Read(buffer, 0, buffer.Length)) > 0)
                {
                    networkStream.Write(buffer, 0, bytesRead);
                }
            }

            Console.WriteLine("파일 전송 완료.");

            // 연결 종료
            networkStream.Close();
            client.Close();
        }
    }
}
```
***
