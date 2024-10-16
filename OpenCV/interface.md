## 오늘도 openCV를 해봤다~~~~~
```
using OpenCvSharp;

namespace CvKeyboard
{
	internal class Program
	{
		static void Main(string[] args)
		{
			using (Mat image = new Mat(200, 300, MatType.CV_8U, new Scalar(255)))
			{
				Cv2.NamedWindow("키보드 이벤트", WindowFlags.AutoSize);
				Cv2.ImShow("키보드 이벤트", image);

				while(true)
				{
					int key = Cv2.WaitKeyEx(200);

					if (key == 27) //'ESC'
						break;

					switch(key)
					{
						case 'A':
							Console.WriteLine("A키 입력");
							break;
						case 'a':
							Console.WriteLine("a키 입력");
							break;
						case 'B':
							Console.WriteLine("B키 입력");
							break;
						case 'b':
							Console.WriteLine("b키 입력");
							break;
						case 0x250000:
							Console.WriteLine("왼쪽 화살표 입력");
							break;
						case 0x260000:
							Console.WriteLine("위쪽 화살표 입력");
							break;
						case 0x270000:
							Console.WriteLine("오른쪽 화살표 입력");
							break;
						case 0x280000:
							Console.WriteLine("아래쪽 화살표 입력");
							break;
					}
				}
			}
		}
	}
}
```
![image](https://github.com/user-attachments/assets/f198bfc5-0998-4561-9d23-025f155316d2)
***
## 카메라 제어도 해봤당



![image](https://github.com/user-attachments/assets/dfe37ee6-bc95-4fc4-b999-a0605616135d)

```
using OpenCvSharp;

namespace CvBasicCam
{
	internal class Program
	{
		class StringUtil
		{
			public void PutString(Mat frame, string text, Point pt, double value)
			{
				text += value.ToString();
				Point shade = new Point(pt.X + 2, pt.Y + 2);
				int font = (int)HersheyFonts.HersheySimplex;

				// 그림자 효과 
				Cv2.PutText(frame, text, shade, (HersheyFonts)font, 0.7, Scalar.Black, 2);

				// 실제 텍스트 
				Cv2.PutText(frame, text, pt, (HersheyFonts)font, 0.7, new Scalar(120, 200, 90), 2);
			}
		}
		static void Main(string[] args)
		{
			// 웹캠 연결
			VideoCapture capture = new VideoCapture(0);
			if (!capture.IsOpened())
			{
				Console.WriteLine("카메라가 연결되지 않았습니다.");
				return;
			}

			// 카메라 속성 출력
			Console.WriteLine("너비: " + capture.Get(VideoCaptureProperties.FrameWidth));
			Console.WriteLine("높이: " + capture.Get(VideoCaptureProperties.FrameHeight));
			Console.WriteLine("노출: " + capture.Get(VideoCaptureProperties.Exposure));
			Console.WriteLine("밝기: " + capture.Get(VideoCaptureProperties.Brightness));

			Mat frame = new Mat();
			while (true)
			{
				// 카메라에서 프레임 읽기
				capture.Read(frame);
				if (frame.Empty())
					break;

				// 노출 정보 출력
				StringUtil su = new StringUtil();
				su.PutString(frame, "EXPOS: ", new Point(10, 40), capture.Get(VideoCaptureProperties.Exposure));

				Cv2.ImShow("카메라 영상보기", frame);

				// 키 입력 대기 (30ms)
				if (Cv2.WaitKey(30) >= 0)
					break;
			}
			Cv2.DestroyAllWindows();
		}
	}
}
```
## 원도 그려봤다
```
using OpenCvSharp;

namespace CvBasicCam2
{
	internal class Program
	{
		static void Main(string[] args)
		{
			// 색상 정의
			Scalar orange = new Scalar(0, 165, 255);
			Scalar blue = new Scalar(255, 0, 0);
			Scalar magenta = new Scalar(255, 0, 255);

			// 흰색 배경의 이미지 생성
			Mat image = new Mat(300, 500, MatType.CV_8UC3, new Scalar(255, 255, 255));

			// 이미지 크기 및 중심점 정의
			Size size = image.Size();
			Point center = new Point(size.Width / 2, size.Height / 2);

			// 원을 그릴 두 점 정의
			Point pt1 = new Point(70, 50);
			Point pt2 = new Point(350, 220);

			// 원 그리기
			Cv2.Circle(image, center, 100, blue); // 중심에 파란색 원
			Cv2.Circle(image, pt1, 80, orange, 2); // pt1에 주황색 테두리 원
			Cv2.Circle(image, pt2, 60, magenta, -1); // pt2에 채워진 자주색 원

			// 글자 쓰기
			int font = (int)HersheyFonts.HersheyComplex;
			Cv2.PutText(image, "center_blue", center, HersheyFonts.HersheyComplex, 1.2, blue);
			Cv2.PutText(image, "pt1_orange", pt1, HersheyFonts.HersheyComplex, 0.8, orange);

			// pt2의 텍스트는 그림자 효과처럼 두 번 그리기
			Point newPt2 = new Point(pt2.X + 2, pt2.Y + 2); // 약간 이동된 검정색 글자
			Cv2.PutText(image, "pt2_magenta", newPt2, HersheyFonts.HersheyComplex, 0.5, new Scalar(0, 0, 0), 2);
			Cv2.PutText(image, "pt2_magenta", pt2, HersheyFonts.HersheyComplex, 0.5, magenta, 1); // 원래 위치에 자주색 글자

			// 결과 이미지 출력
			Cv2.ImShow("원그리기", image);

			// 키 입력 대기 후 창 닫기
			Cv2.WaitKey(0);
			Cv2.DestroyAllWindows();
		}
	}
}
```

![image](https://github.com/user-attachments/assets/585b4a40-ab29-48a0-bd4f-73a7ec459f10)
***
## 타원도 그려봤다.
```
using OpenCvSharp;

namespace CvBasicCam2
{
	internal class Program
	{
		static void Main(string[] args)
		{
			Scalar orange = new Scalar(0, 165, 255);
			Scalar blue = new Scalar(255, 0, 0);
			Scalar magenta = new Scalar(255, 0, 255);
			Mat image = new Mat(300, 700, MatType.CV_8UC3, new Scalar(255, 255, 255));

			Point pt1 = new Point(120, 150);
			Point pt2 = new Point(550, 150);

			Cv2.Circle(image, pt1, 1, new Scalar(0), 1);
			Cv2.Circle(image, pt2, 1, new Scalar(0), 1);

			Cv2.Ellipse(image, pt1, new Size(100, 60), 0, 0, 360, orange, 2);
			Cv2.Ellipse(image, pt1, new Size(100, 60), 0, 30, 270, blue, 4);


			Cv2.Ellipse(image, pt2, new Size(100, 60), 30, 0, 360, orange, 2);
			Cv2.Ellipse(image, pt2, new Size(100, 60), 30, -30, 160, magenta, 4);

			Cv2.ImShow("타원 및 호 그리기", image);
			Cv2.WaitKey(0);
			Cv2.DestroyAllWindows();
		}
	}
}
```
![image](https://github.com/user-attachments/assets/94c2cc43-3409-44b7-8ae6-7975aa48dcad)

***
## 줌 도 해봤다
```
using OpenCvSharp;

namespace CvBasicCam2
{
	internal class Program
	{
		private static Mat frame = new Mat();
		private static VideoCapture capture = new VideoCapture(0);
		private static int zoomFactor = 1; // 줌 기본값
		private static int focusFactor = 40; // 포커스 기본값

		private static void ZoomBar(int value, IntPtr userdata)
		{
			zoomFactor = value;
		}
		private static void FocusBar(int value, IntPtr userdata)
		{
			focusFactor = value;
		}

		static void Main(string[] args)
		{
			capture.Open(0);
			if (!capture.IsOpened())
			{
				Console.WriteLine("카메라가 연결되지 않았습니다.");
				return;
			}

			// 카메라 속성 설정
			capture.Set(VideoCaptureProperties.FrameWidth, 800);
			capture.Set(VideoCaptureProperties.FrameHeight, 600);
			capture.Set(VideoCaptureProperties.AutoFocus, 0); // 수동 포커스 설정
			capture.Set(VideoCaptureProperties.Brightness, 150);

			// 창 및 트랙바 생성
			string title = "카메라 속성변경";
			Cv2.NamedWindow(title);
			Cv2.CreateTrackbar("Zoom", title, ref zoomFactor, 5, ZoomBar);
			Cv2.CreateTrackbar("Focus", title, ref focusFactor, 40, FocusBar);

			while (true)
			{
				capture.Read(frame);
				if (frame.Empty())
					break;

				//트랙바와 Focus
				capture.Set(VideoCaptureProperties.Zoom, zoomFactor);
				capture.Set(VideoCaptureProperties.Focus, focusFactor);

				// 줌 적용된 이미지
				ShowZoomedImage(zoomFactor);

				// 30ms 간격으로 키 입력 대기, 아무 키나 누르면 종료
				if (Cv2.WaitKey(30) >= 0)
					break;
			}

			capture.Release();
			Cv2.DestroyAllWindows();
		}

		// 줌을 적용하여 이미지 크롭 및 확대하는 함수
		private static void ShowZoomedImage(int zoomLevel)
		{
			// 줌 레벨이 1보다 작거나 같으면 원본 표시
			if (zoomLevel <= 1)
			{
				Cv2.ImShow("카메라 속성변경", frame);
				return;
			}
			// 중앙 부분을 크롭하여 줌 효과 적용
			int newWidth = frame.Width / zoomLevel;
			int newHeight = frame.Height / zoomLevel;
			int x = (frame.Width - newWidth) / 2;
			int y = (frame.Height - newHeight) / 2;

			Rect roi = new Rect(x, y, newWidth, newHeight);
			Mat zoomedFrame = new Mat(frame, roi);

			// 크롭한 이미지를 다시 원래 크기로 확대
			Cv2.Resize(zoomedFrame, zoomedFrame, new Size(frame.Width, frame.Height));

			// 결과 이미지를 동일한 창에 표시
			Cv2.ImShow("카메라 속성변경", zoomedFrame);
		}
	}
}
```
원래 줌이 안먹는데 억지로 했다,,!
