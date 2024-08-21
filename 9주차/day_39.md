## 넘 피곤한데,, 화이팅~~

```
WINFORM 으로 서버-클라이언트 를 구동해봤다.


using System.Net;
using System.Net.Sockets;
using System.Text;

namespace WinFormEchoServer
{
    public partial class Form1 : Form
    {
        private static TcpListener server = null;

        public Form1()
        {
            InitializeComponent();
        }

        private void Form1_Load(object sender, EventArgs e)
        {
            Thread serverThread = new Thread(StartServer);
            serverThread.IsBackground = true;
            serverThread.Start();
        }//end of Form1_Load
        private void StartServer()
        {
            try
            {
                IPAddress serverIP = IPAddress.Parse("127.0.0.1");
                int port = 13000;

                server = new TcpListener(serverIP, port);
                server.Start();

                //textBox1.AppendText("Echo Server 시작 ...\n");
                AppendText("Echo Server 시작 ...");

                while (true)
                {
                    TcpClient client = server.AcceptTcpClient();
                    //textBox1.AppendText("클라이언트가 연결되었습니다.\n");
                    AppendText("클라이언트가 연결되었습니다.");

                    Thread clientThread = new Thread(new ParameterizedThreadStart(ClientAction));
                    clientThread.IsBackground = true;
                    clientThread.Start(client);
                }

            }
            catch (Exception e)
            {
                MessageBox.Show(e.Message); 
            }
            finally
            {
                if (server != null)
                {
                    server.Stop();
                }
            }//end finally
        }//end of StartServer
        private void ClientAction(object obj)
        {
            TcpClient client = (TcpClient)obj;
            try
            {
                using (NetworkStream stream = client.GetStream())
                {
                    //받기
                    byte[] buffer = new byte[2048];
                    int bytesRead = stream.Read(buffer, 0, buffer.Length);
                    string receiveMsg = Encoding.UTF8.GetString(buffer);
                    //Console.WriteLine("클라이언트에게 받은 메시지 : " + receiveMsg);
                    AppendText("클라이언트에게 받은 메시지 : " + receiveMsg);


                    //보내기
                    byte[] echoMsg = Encoding.UTF8.GetBytes(receiveMsg);
                    stream.Write(echoMsg, 0, echoMsg.Length);
                    //Console.WriteLine("에코메시지 전송 완료");
                    AppendText("에코메시지 전송 완료");
                }
            }
            catch (Exception e)
            {
                Console.WriteLine(e.Message);
            }
            finally
            {
                if (client != null)
                {
                    client.Close();
                }
            }
        }

        private void AppendText(string text)
        {
            if (this.InvokeRequired)
            {
                this.Invoke(new Action<string>(AppendText), new object[] { text });
            }
            else
            {
                textBox1.AppendText(text + Environment.NewLine);
            }
        }


    }//end of Form
}
```

```
윈폼을 응용한 채팅 서버

using System.Net;
using System.Net.Sockets;
using System.Text;

namespace WinFormTCPChattingServer
{
    public partial class Form1 : Form
    {
        private static TcpListener server = null;
        private static List<TcpClient> clientList = new List<TcpClient>();

        public Form1()
        {
            InitializeComponent();

            Thread serverThread = new Thread(StartServer);
            serverThread.IsBackground = true;
            serverThread.Start();
        }
        private void StartServer()
        {
            try
            {
                IPAddress serverIp = IPAddress.Parse("127.0.0.1");
                server = new TcpListener(serverIp, 13000);

                server.Start();
                AppendText("Chat Server 시작...");

                while (true)
                {
                    TcpClient client = server.AcceptTcpClient();
                    AppendText("클라이언트가 연결되었습니다.");

                    lock (clientList)
                    {
                        clientList.Add(client);
                    }

                    Thread clientThread = new Thread(ClientAction);
                    clientThread.IsBackground = true;
                    clientThread.Start(client);
                }
            }
            catch (SocketException ex)
            {
                MessageBox.Show("소켓 예외: " + ex.ToString());
            }
            finally
            {
                if (server != null)
                {
                    server.Stop();
                }
            }
        }
        private void ClientAction(object obj)
        {
            TcpClient client = (TcpClient)obj;
            try
            {
                using (NetworkStream stream = client.GetStream())
                {
                    byte[] buffer = new byte[256];
                    int bytesRead;

                    while ((bytesRead = stream.Read(buffer, 0, buffer.Length)) != 0)
                    {
                        string receivedMessage = Encoding.UTF8.GetString(buffer, 0, bytesRead);
                        AppendText("클라이언트로부터 받은 메시지: " + receivedMessage);

                        BroadcastMessage(receivedMessage, client);
                    }
                }
            }
            catch (Exception e)
            {
                AppendText("클라이언트 처리 중 예외 발생: " + e.Message);
            }
            finally
            {
                lock (clientList)
                {
                    clientList.Remove(client);
                }
                if (client != null)
                {
                    client.Close();
                }
                AppendText("클라이언트 연결이 종료되었습니다.");
            }
        }

        private void BroadcastMessage(string message, TcpClient senderClient)
        {
            byte[] broadcastMsg = Encoding.UTF8.GetBytes(message);

            lock (clientList)
            {
                foreach (TcpClient client in clientList)
                {
                    if (client != senderClient)
                    {
                        try
                        {
                            NetworkStream stream = client.GetStream();
                            stream.Write(broadcastMsg, 0, broadcastMsg.Length);
                        }
                        catch (Exception ex)
                        {
                            AppendText("메시지 전송 중 예외 발생: " + ex.Message);
                        }
                    }
                }
            }
            AppendText("메시지를 모든 클라이언트에게 전송했습니다.");
        }

        private void AppendText(string text)
        {
            if (this.InvokeRequired)
            {
                this.Invoke(new Action<string>(AppendText), new object[] { text });
            }
            else
            {
                textBox1.AppendText(text + Environment.NewLine);
            }
        }
                
    }
}
```
```
채팅 클라이언트
using System.Net.Sockets;
using System.Text;

namespace ChatTCPClient
{
    public partial class Form1 : Form
    {
        private TcpClient client;
        private NetworkStream stream;
        private Thread receiveThread;

        public Form1()
        {
            InitializeComponent();
        }

        private void Form1_Load(object sender, EventArgs e)
        {
            ConnectToServer();
        }
        private void ConnectToServer()
        {
            string server = "127.0.0.1";
            int port = 13000;

            try
            {
                client = new TcpClient(server, port);
                stream = client.GetStream();

                receiveThread = new Thread(ReceiveMsg);
                receiveThread.IsBackground = true;
                receiveThread.Start();

                AppendText("서버에 연결되었습니다.");
            }
            catch (Exception ex)
            {
                MessageBox.Show("서버에 연결할 수 없습니다: " + ex.Message);
            }
        }
        private void btnMsg_Click(object sender, EventArgs e)
        {
            if (client == null || !client.Connected)
            {
                MessageBox.Show("서버에 연결되어 있지 않습니다.");
                return;
            }

            string message = txtMsg.Text;
            byte[] Msg = Encoding.UTF8.GetBytes(message);
            stream.Write(Msg, 0, Msg.Length); // 메시지 전송

            AppendText("나: " + message); //화면에 내가 보낸 글자 추가

            txtMsg.Text = "";
        }
        private void ReceiveMsg()
        {
            try
            {
                byte[] buffer = new byte[256];
                int bytesRead;

                while ((bytesRead = stream.Read(buffer, 0, buffer.Length)) != 0)
                {
                    string receiveMsg = Encoding.UTF8.GetString(buffer, 0, bytesRead);
                    AppendText("받은 메시지: " + receiveMsg);
                }
            }
            catch (Exception ex)
            {
                AppendText("서버로부터 메시지 수신 중 오류 발생: " + ex.Message);
            }
            finally
            {
                Disconnect();
            }
        }

        private void Disconnect()
        {
           /// isRunning = false; // 스레드 종료 신호
            
            if (stream != null)
                stream.Close();
            if (client != null)
                client.Close();

            AppendText("서버와의 연결이 종료되었습니다.");
        }

        // UI 스레드에서 안전하게 텍스트박스에 메시지를 추가하는 메서드
        private void AppendText(string text)
        {
            if (this.InvokeRequired)
            {
                this.Invoke(new Action<string>(AppendText), new object[] { text });
            }
            else
            {
                txtResult.AppendText(text + Environment.NewLine);
            }
        }
        
        private void Form1_FormClosed(object sender, FormClosedEventArgs e)
        {
            this.Dispose();
        }
    }
}
```
