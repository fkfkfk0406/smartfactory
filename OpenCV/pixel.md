## 오늘은 화소처리를 좀 해봤음~~~~~
```
using System;

using System.Threading.Tasks;

using System.Windows.Forms;

using OpenCvSharp;

using OpenCvSharp.Extensions;



namespace CvCamera

{

	public partial class Form1 : Form

	{

		private VideoCapture capture;  // 카메라 캡처 객체

		private Mat frame;             // 현재 프레임을 저장할 객체

		private bool isRunning = false;  // 카메라가 실행 중인지 확인하는 변수

		private bool isColor = true;     // 컬러 모드인지 확인하는 변수

		private bool isContrastMode = false; // 대비 증가 모드 확인 변수



		public Form1()

		{

			InitializeComponent();

		}



		private void Form1_Load(object sender, EventArgs e)

		{

			capture = new VideoCapture(0);  // 카메라 장치 연결

			frame = new Mat();

			capture.Set(VideoCaptureProperties.FrameWidth, 640);  // 프레임 너비 설정

			capture.Set(VideoCaptureProperties.FrameHeight, 480); // 프레임 높이 설정

		}

		private async void btnStart_Click(object sender, EventArgs e)

		{

			if (isRunning)  // 이미 카메라가 실행 중이면

			{

				isRunning = false;  // 실행 중 상태를 false로 변경

				btnStart.Text = "Start";  // 버튼 텍스트 변경

				return;

			}



			btnStart.Text = "Stop";  // 버튼 텍스트 변경

			isRunning = true;  // 실행 중 상태를 true로 변경



			while (isRunning)  // 카메라가 실행 중이면

			{

				if (capture.IsOpened())  // 카메라가 연결되어 있으면

				{

					capture.Read(frame);  // 프레임 읽기



					// 컬러 또는 흑백 모드 적용

					if (!isColor)  // 흑백 모드이면

					{

						Cv2.CvtColor(frame, frame, ColorConversionCodes.BGR2GRAY);  // 컬러를 흑백으로 변환

						Cv2.CvtColor(frame, frame, ColorConversionCodes.GRAY2BGR);  // 흑백을 다시 컬러로 변경 (PictureBox 호환을 위해)

					}



					if (isContrastMode)  // 대비 증가 모드가 활성화되어 있으면

					{

						Mat enhancedFrame = EnhanceContrast(frame);  // 채널별 정규화를 통해 대비 증가

						Invoke((MethodInvoker)delegate

						{

							pictureBox1.Image = BitmapConverter.ToBitmap(enhancedFrame);  // 화질 개선된 영상 출력

						});

					}

					else

					{

						Invoke((MethodInvoker)delegate

						{

							pictureBox1.Image = BitmapConverter.ToBitmap(frame);  // 기본 컬러 또는 흑백 영상 출력

						});

					}

				}

				await Task.Delay(33);  // 대략 30 fps

			}

		}

		private void btnColor_Click(object sender, EventArgs e)

		{

			isColor = true;   // 컬러 모드로 변경

		}



		private void btnBlack_Click(object sender, EventArgs e)

		{

			isColor = false;  // 흑백 모드로 변경

		}



		private void btnExit_Click(object sender, EventArgs e)

		{

			isRunning = false;  // 카메라 중지

			capture.Release();  // 카메라 자원 해제

			this.Close();

		}



		private void btnContrast_Click(object sender, EventArgs e)

		{

			isContrastMode = true;  

		}

		// 화질 개선을 위해 채널별로 최소값, 최대값을 구해 정규화하는 메소드

		private Mat EnhanceContrast(Mat inputFrame)

		{

			Mat[] channels = Cv2.Split(inputFrame);

			for (int i = 0; i < channels.Length; i++)

			{

				double minVal, maxVal;

				Cv2.MinMaxLoc(channels[i], out minVal, out maxVal);

				channels[i].ConvertTo(channels[i], MatType.CV_8U, 300.0 / (maxVal - minVal), -minVal * 300.0 / (maxVal - minVal));

			}

			Mat enhancedFrame = new Mat();

			Cv2.Merge(channels, enhancedFrame);

			return enhancedFrame;

		}

	}
}
```
![image](https://github.com/user-attachments/assets/d8d38e8a-59e4-4808-a706-a757ba9a0229)



![image](https://github.com/user-attachments/assets/01c85d55-09cd-4045-90ff-4554ebd1da1e)
***
```
using OpenCvSharp;



namespace ConsoleApp86

{

	internal class Program

	{

		static void Main(string[] args)

		{

			Mat image1 = new Mat(50, 512, MatType.CV_8UC1, new Scalar(0));



			Mat image2 = new Mat(50, 512, MatType.CV_8UC1, new Scalar(0));







			for (int i = 0; i < image1.Rows; i++)

			{



				for (int j = 0; j < image1.Cols; j++)



				{



					byte value1 = (byte)(j / 2);



					byte value2 = (byte)((j / 20) * 10);







					image1.Set(i, j, value1);



					image2.Set(i, j, value2);



				}



			}



			Cv2.ImShow("image1", image1);



			Cv2.ImShow("image2", image2);



			Cv2.WaitKey();



		}



	}

}
```
![image](https://github.com/user-attachments/assets/18fb0524-b9fa-4c99-838f-e86d1761e4a8)
***
```
using System.Collections.Specialized;

using OpenCvSharp;



namespace ConsoleApp86

{

	internal class Program

	{

		static void Main(string[] args)

		{

			Mat image = new Mat("C:\\Temp\\opencv\\cv_imgs_2\\pixel_test.jpg", ImreadModes.Grayscale);

			if (image.Empty())

			{

				Console.WriteLine("영상을 읽지 못 했습니다.");

				Environment.Exit(1);

			}



			Rect roi = new Rect(135, 95, 20, 15);

			Mat roi_img = image.SubMat(roi);

			Console.WriteLine("[roi_img] =");



			for (int i = 0; i < roi_img.Rows; i++)

			{

				for (int j = 0; j < roi_img.Cols; j++)

				{

					Console.Write($"{roi_img.At<byte>(i, j),5}");

				}

				Console.WriteLine();

			}



			image.Rectangle(roi, Scalar.White, 1);

			Cv2.ImShow("image", image);

			Cv2.WaitKey();

		}

	}

}
```
![image](https://github.com/user-attachments/assets/fcfe0bdb-caef-4578-91ca-9e5ee3dd8b4d)
***
```
using System.Collections.Specialized;
using System.Net;
using OpenCvSharp;

namespace ConsoleApp86
{
	internal class Program
	{
		static void Main(string[] args)
		{
			Mat image = new Mat("C:\\Temp\\opencv\\cv_imgs_2\\bright.jpg", ImreadModes.Grayscale);
			if (image.Empty())
			{
				Console.WriteLine("영상을 읽지 못 했습니다.");
				Environment.Exit(1);
			}

			Mat dst1 = new Mat();
			Mat dst2 = new Mat();
			Mat dst3 = new Mat();
			Mat dst4 = new Mat(image.Size(), image.Type());
			Mat dst5 = new Mat(image.Size(), image.Type());

			Cv2.Add(image, new Scalar(100), dst1);
			Cv2.Subtract(image, new Scalar(100), dst2);
			Cv2.Subtract(new Scalar(255), image, dst3);

			for (int i = 0; i < image.Rows; i++)
			{
				for (int j = 0; j < image.Cols; j++)
				{
					dst4.Set(i, j, image.At<byte>(i, j) + 100);

					dst5.Set(i, j, 255 - image.At<byte>(i, j));
				}
			}

			Cv2.ImShow("Image", image);
			Cv2.ImShow("dst1", dst1);
			Cv2.ImShow("dst2", dst2);
			Cv2.ImShow("dst3", dst3);
			Cv2.ImShow("dst4", dst4);
			Cv2.ImShow("dst5", dst5);

			Cv2.WaitKey();
			Cv2.DestroyAllWindows();
		}
	}
}
```
![화면 캡처 2024-10-21 155645](https://github.com/user-attachments/assets/161ef4c0-a791-4aa9-b096-52b1813e07ab)
***
```
using System.Collections.Specialized;
using System.Net;
using OpenCvSharp;

namespace ConsoleApp86
{
	internal class Program
	{
		static void Main(string[] args)
		{
			Mat image1 = new Mat("C:\\Temp\\opencv\\cv_imgs\\add1.jpg", ImreadModes.Grayscale);
			Mat image2 = new Mat("C:\\Temp\\opencv\\cv_imgs\\add2.jpg", ImreadModes.Grayscale);

			if (image1.Empty() || image2.Empty())
			{
				Console.WriteLine("영상을 읽지 못 했습니다.");
				Environment.Exit(1);
			}

			double alpha = 0.6;
			double beta = 0.7;

			Mat add_img1 = new Mat();
			Cv2.Add(image1, image2, add_img1);

			Mat add_img2 = new Mat();
			Cv2.Add(image1 * 0.5, image2 * 0.5, add_img2);

			Mat add_img3 = new Mat();
			Cv2.AddWeighted(image1, alpha, image2, 1.0 - alpha, 0, add_img3);

			Mat add_img4 = new Mat();
			Cv2.AddWeighted(image1, alpha, image2, beta, 0, add_img4);

			Cv2.ImShow("image1", image1);
			Cv2.ImShow("image2", image2);
			Cv2.ImShow("add_img1", add_img1);
			Cv2.ImShow("add_img2", add_img2);
			Cv2.ImShow("add_img3", add_img3);
			Cv2.ImShow("add_img4", add_img4);

			Cv2.WaitKey();
			Cv2.DestroyAllWindows();
		}
	}
}
```
![화면 캡처 2024-10-21 164526](https://github.com/user-attachments/assets/ed171d4e-4f81-4ed3-8ea8-26955f0ce817)
