## Mat 을 해봤다.
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
