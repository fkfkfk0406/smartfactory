## 오늘은 winform 으로 카메라 제어를 해봤 따~!~~~~~~~~
```
using OpenCvSharp;
using OpenCvSharp.Extensions;
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace WindowsFormsApp8
{
	public partial class Form1 : Form
	{
		private VideoCapture capture;  // 카메라 캡처 객체
		private Mat frame;             // 현재 프레임을 저장할 객체
		private bool isRunning = false;  // 카메라가 실행 중인지 확인하는 변수
		private bool isColor = true;     // 컬러 모드인지 확인하는 변수
		public Form1()
		{
			InitializeComponent();
		}

		private void button1_Click(object sender, EventArgs e)
		{
			if (isRunning)  // 이미 카메라가 실행 중이면
			{
				isRunning = false;  // 실행 중 상태를 false로 변경
				button1.Text = "Start";  // 버튼 텍스트 변경
				return;
			}

			// 카메라 초기화
			capture = new VideoCapture(0);  // 첫 번째 카메라 장치(0) 사용
			if (!capture.IsOpened())  // 카메라가 연결되지 않았으면
			{
				MessageBox.Show("카메라가 연결되지 않았습니다.");
				return;
			}

			frame = new Mat();  // 프레임 객체 초기화

			button1.Text = "Stop";  // 버튼 텍스트 변경
			isRunning = true;  // 실행 중 상태를 true로 변경

			// 비동기적으로 카메라 실행
			Task.Run(() =>
			{
				while (isRunning)  // 카메라가 실행 중이면
				{
					capture.Read(frame);  // 프레임 읽기

					if (!frame.Empty())  // 프레임이 비어 있지 않으면
					{
						if (!isColor)  // 흑백 모드이면
						{
							Cv2.CvtColor(frame, frame, ColorConversionCodes.BGR2GRAY);  // 컬러를 흑백으로 변경
							Cv2.CvtColor(frame, frame, ColorConversionCodes.GRAY2BGR);  // 흑백을 다시 컬러로 변경 (PictureBox 호환을 위해)
						}

						// PictureBox에 영상 출력 (UI 스레드에서 실행해야 함)
						pictureBox1.Invoke((MethodInvoker)(() =>
						{
							pictureBox1.Image = BitmapConverter.ToBitmap(frame);
						}));
					}
				}

				// 카메라 리소스 해제
				capture.Release();
			});

		}

		private void button2_Click(object sender, EventArgs e)
		{
			isColor = true;   // 컬러 모드로 변경
		}

		private void button3_Click(object sender, EventArgs e)
		{
			isColor = false;  // 흑백 모드로 변경
		}

		private void button4_Click(object sender, EventArgs e)
		{

			isRunning = false;  // 카메라 중지
			capture.Release();  // 카메라 자원 해제
			this.Close();       // 프로그램 종료
		}
		private void Form1_Load(object sender, EventArgs e)
		{
			capture = new VideoCapture(0);  // 카메라 장치 연결
			frame = new Mat();
			capture.Set(VideoCaptureProperties.FrameWidth, 640);  // 프레임 너비 설정
			capture.Set(VideoCaptureProperties.FrameHeight, 480); // 프레임 높이 설정
		}
	}
}
```
## 컬러 버전
![image](https://github.com/user-attachments/assets/6aea8fdc-f15d-4a8a-a295-b702698d74a6)




## 흑백 버전
![image](https://github.com/user-attachments/assets/558768d7-f1c5-4d3b-8e7a-928b885800a4)
***
