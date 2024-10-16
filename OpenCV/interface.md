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

