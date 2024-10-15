![image](https://github.com/user-attachments/assets/9f913e22-cfd5-49e8-a7db-ac6003eb786d)## Mat 을 해봤다.
![image](https://github.com/user-attachments/assets/4010cbc6-04d1-448b-aa5a-a5740cc171d2)
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using OpenCvSharp;

namespace Opencv_005
{
	internal class Program
	{
		static void Main(string[] args)
		{
			Mat m1 = new Mat(4, 3, MatType.CV_32FC3, new Scalar(0, 0, 0));

			Console.WriteLine($"m1 : \n{m1.Dump()}");
		}
	}
}
```



![image](https://github.com/user-attachments/assets/313f1452-fe1b-4f2c-a76b-1e4b27d88b82)
***
![image](https://github.com/user-attachments/assets/fa2656d1-20ca-41f8-a31b-5a0a14e67aac)



오호,,,,,
***
![image](https://github.com/user-attachments/assets/cd1bb760-44b2-4778-ac88-df1f7ee7569f)
```
using OpenCvSharp;

namespace ConsoleApp82
{
	internal class Program
	{
		static void Main(string[] args)
		{
			String path = @"C:/Temp/opencv/cv_imgs/flip_test.jpg";
			Mat image = new Mat(path, ImreadModes.Color);
			if (image.Empty())
			{
				Console.WriteLine("경로나 이미지에 문제가 있습니다.");
			}

			Mat x_axis = new Mat();
			Mat y_axis = new Mat();
			Mat xy_axis = new Mat();

			Cv2.Flip(image, x_axis, FlipMode.X);
			Cv2.Flip(image, y_axis, FlipMode.Y);
			Cv2.Flip(image, xy_axis, FlipMode.XY);

			Cv2.ImShow("image", image);
			Cv2.ImShow("x_axis", x_axis);
			Cv2.ImShow("y_axis", y_axis);
			Cv2.ImShow("xy_axis", xy_axis);

			Cv2.WaitKey(0);
			Cv2.DestroyAllWindows();
		}
	}
}
```
***
# 집도 한번 그려봤음
```
using OpenCvSharp;

namespace ConsoleApp82
{
	internal class Program
	{
		static void Main(string[] args)
		{
			Scalar blue = new Scalar(255, 0, 0); 
			Scalar red = new Scalar(0, 0, 255); 
			Scalar white = new Scalar(255, 255, 255); 
			Scalar black = new Scalar(0, 0, 0); 

			Mat image = new Mat(700, 700, MatType.CV_8UC3, white);

			// 사각형 그리기
			Point pt1 = new Point(100, 200); 
			Point pt2 = new Point(500, 600); 
			Cv2.Rectangle(image, pt1, pt2, black, 2, LineTypes.AntiAlias); 

			Point pt3 = new Point(300, 400); 
			int radius = 200; 
			Cv2.Circle(image, pt3, radius, blue, -1, LineTypes.AntiAlias); 

			Point[] triangle =
			{
				new Point(100, 200), 
                new Point(300, 50), 
                new Point(500, 200) 
            };
			Cv2.FillPoly(image, new Point[][] { triangle }, red); 

			Cv2.Line(image, new Point(100, 200), pt2, blue, 2, LineTypes.AntiAlias);
			Cv2.Line(image, new Point(100, 600), new Point(500, 200), blue, 2, LineTypes.AntiAlias); 

			Cv2.ImShow("직선 & 사각형", image);

			Cv2.WaitKey(0);
			Cv2.DestroyAllWindows();
		}
	}
}
```
![image](https://github.com/user-attachments/assets/2e4ace22-219f-477a-87be-10d4f25aa529)

