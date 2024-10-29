## 오늘은 얼굴 검출 머시기를 해봤다~~~~
```
using OpenCvSharp;
using System;

public static class Preprocess
{
	public static bool LoadCascade(CascadeClassifier cascade, string filePath)
	{
		return cascade.Load(filePath);
	}

	public static Mat Preprocessing(Mat image)
	{
		Mat gray = new Mat();
		Cv2.CvtColor(image, gray, ColorConversionCodes.BGR2GRAY);
		Cv2.EqualizeHist(gray, gray);
		return gray;
	}
}

public class Program
{
	public static Point2d CalcCenter(Rect obj)
	{
		// Rect 크기의 중점 계산 후 int 타입으로 변환
		Point2d c = new Point2d(obj.Width / 2.0, obj.Height / 2.0);
		Point2d center = new Point2d(obj.X + c.X, obj.Y + c.Y);

		// Point2d를 Point로 명시적 캐스팅
		return new Point((int)center.X, (int)center.Y);
	}

	public static void Main()
	{
		CascadeClassifier faceCascade = new CascadeClassifier();
		CascadeClassifier eyesCascade = new CascadeClassifier();

		if (!Preprocess.LoadCascade(faceCascade, "C:\\Users\\Admin\\source\\repos\\ConsoleApp89\\data\\haarcascade_frontalface_alt2.xml") ||
			!Preprocess.LoadCascade(eyesCascade, "C:\\Users\\Admin\\source\\repos\\ConsoleApp89\\data\\haarcascade_eye.xml"))
		{
			Console.WriteLine("Could not load cascade classifiers");
			return;
		}

		Mat image = Cv2.ImRead("C:\\Temp\\opencv\\cv_imgs_2\\face\\59.jpg", ImreadModes.Color);
		if (image.Empty())
		{
			Console.WriteLine("Image not loaded.");
			return;
		}

		Mat gray = Preprocess.Preprocessing(image);

		Rect[] faces = faceCascade.DetectMultiScale(gray, 1.1, 2, HaarDetectionTypes.ScaleImage, new Size(100, 100));
		if (faces.Length > 0)
		{
			Mat faceROI = new Mat(gray, faces[0]);
			Rect[] eyes = eyesCascade.DetectMultiScale(faceROI, 1.15, 7, HaarDetectionTypes.ScaleImage, new Size(25, 20));

			if (eyes.Length == 2)
			{
				foreach (Rect eye in eyes)
				{
					Point center = (Point)CalcCenter(new Rect(faces[0].X + eye.X, faces[0].Y + eye.Y, eye.Width, eye.Height));
					Cv2.Circle(image, center, 5, new Scalar(0, 255, 0), 2);
				}
			}

			Cv2.Rectangle(image, faces[0], new Scalar(255, 0, 0), 2);
			Cv2.ImShow("image", image);
			Cv2.WaitKey(0);
		}
	}
}
```
![image](https://github.com/user-attachments/assets/c76257a0-8dcd-4e1b-b39a-bc6ceb40bf86)



되게 어려웠다 뭔가 기존에 ppt 에 있던 cpp 코드를 c# 으로 바꾸려니 여간 까다로운게 아니다 ;;; 에러도 엄청 나오고.
***
