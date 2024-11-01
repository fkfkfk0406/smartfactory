## 동전 검출기를 만들어봤따~~
```
using OpenCvSharp;

using System;

using System.Collections.Generic;



public static class Preprocess

{

	public static Mat Preprocessing(Mat img)

	{

		Mat gray = new Mat(), th_img = new Mat();

		Cv2.CvtColor(img, gray, ColorConversionCodes.BGR2GRAY);

		Cv2.GaussianBlur(gray, gray, new Size(7, 7), 2);

		Cv2.Threshold(gray, th_img, 130, 255, ThresholdTypes.Binary | ThresholdTypes.Otsu);

		Cv2.MorphologyEx(th_img, th_img, MorphTypes.Open, Cv2.GetStructuringElement(MorphShapes.Rect, new Size(3, 3)));

		return th_img;

	}

}



public static class Histogram

{

	public static List<Mat> CalcCoinHistogram(List<Mat> coins, int hueBin)

	{

		List<Mat> histograms = new List<Mat>();

		foreach (Mat coin in coins)

		{

			Mat hsv = new Mat();

			Cv2.CvtColor(coin, hsv, ColorConversionCodes.BGR2HSV);

			Mat hist = new Mat();

			Cv2.CalcHist(

				new Mat[] { hsv },

				new int[] { 0 },

				null,

				hist,

				1,

				new int[] { hueBin },

				new Rangef[] { new Rangef(0, 180) }

			);

			Cv2.Normalize(hist, hist);

			histograms.Add(hist);

		}

		return histograms;

	}

}



public static class CoinClassifier

{

	public static void ClassifyCoins(List<RotatedRect> circles, List<int> groups, int[] Ncoins)

	{

		for (int i = 0; i < circles.Count; i++)

		{

			int radius = (int)Math.Round(circles[i].Size.Width / 2.0);

			int coin = 0;

			if (groups[i] == 0)

			{

				coin = radius > 48 ? 3 : (radius > 46 ? 2 : (radius > 25 ? 0 : 1));

			}

			else if (groups[i] == 1)

			{

				coin = radius > 48 ? 3 : (radius > 43 ? 2 : 1);

			}

			Ncoins[coin]++;

		}

	}



	public static int CalculateTotalValue(int[] Ncoins)

	{

		int[] coinValues = { 10, 50, 100, 500 };

		int total = 0;

		for (int i = 0; i < Ncoins.Length; i++)

		{

			total += coinValues[i] * Ncoins[i];

			Console.WriteLine($"{coinValues[i]}원: {Ncoins[i]} 개");

		}

		return total;

	}

}



public static class CoinDetection

{

	public static List<RotatedRect> FindCoins(Mat th_img)

	{

		List<RotatedRect> circles = new List<RotatedRect>();

		Point[][] contours;

		HierarchyIndex[] hierarchy;

		Cv2.FindContours(th_img, out contours, out hierarchy, RetrievalModes.Tree, ContourApproximationModes.ApproxSimple);



		foreach (var contour in contours)

		{

			RotatedRect ellipse = Cv2.FitEllipse(contour);

			circles.Add(ellipse);

		}

		return circles;

	}



	public static void DrawCircles(Mat image, List<RotatedRect> circles, List<int> groups)

	{

		Scalar[] colors = { new Scalar(0, 0, 255), new Scalar(255, 0, 0) };

		for (int i = 0; i < circles.Count; i++)

		{

			int radius = (int)Math.Round(circles[i].Size.Width / 2.0);

			Point center = new Point((int)circles[i].Center.X, (int)circles[i].Center.Y);

			Cv2.Circle(image, center, radius, colors[groups[i]], 2);

			Cv2.PutText(image, $"Group {groups[i]}", center + new Point(-10, 10), HersheyFonts.HersheySimplex, 0.5, colors[groups[i]], 1);

		}

	}

}



public class Program

{

	public static void Main()

	{

		Console.Write("동전 영상번호 : ");

		int coin_no = int.Parse(Console.ReadLine());

		string fname = $"C:\\Temp\\opencv\\cv_imgs_2\\{coin_no}.png";

		Mat image = Cv2.ImRead(fname, ImreadModes.Color);

		if (image.Empty())

		{

			Console.WriteLine("Image not loaded.");

			return;

		}



		Mat th_img = Preprocess.Preprocessing(image);

		List<RotatedRect> circles = CoinDetection.FindCoins(th_img);

		List<Mat> coinsImg = MakeCoinImages(image, circles);

		List<Mat> coinsHist = Histogram.CalcCoinHistogram(coinsImg, 32);



		int[] Ncoins = new int[4];

		List<int> groups = GroupCoinsByHistogram(coinsHist); // 사용자 정의 함수로 그룹 결정



		CoinClassifier.ClassifyCoins(circles, groups, Ncoins);

		int totalValue = CoinClassifier.CalculateTotalValue(Ncoins);



		string resultText = $"Total coin value: {totalValue} Won";

		Console.WriteLine(resultText);

		Cv2.PutText(image, resultText, new Point(10, 50), HersheyFonts.HersheySimplex, 1, new Scalar(0, 200, 0), 2);



		CoinDetection.DrawCircles(image, circles, groups);

		Cv2.ImShow("결과영상", image);

		Cv2.WaitKey();

		Cv2.DestroyAllWindows();

	}



	public static List<Mat> MakeCoinImages(Mat image, List<RotatedRect> circles)

	{

		List<Mat> coins = new List<Mat>();

		foreach (var circle in circles)

		{

			Rect roi = circle.BoundingRect();



			// roi가 이미지 경계를 벗어나지 않도록 수정

			roi.X = Math.Max(roi.X, 0);

			roi.Y = Math.Max(roi.Y, 0);

			roi.Width = Math.Min(roi.Width, image.Width - roi.X);

			roi.Height = Math.Min(roi.Height, image.Height - roi.Y);



			// 수정된 roi를 사용하여 Mat 객체 생성

			coins.Add(new Mat(image, roi));

		}

		return coins;

	}



	public static List<int> GroupCoinsByHistogram(List<Mat> histograms)

	{

		List<int> groups = new List<int>();

		foreach (var hist in histograms)

		{

			groups.Add(0); // Placeholder value, actual grouping logic needed

		}

		return groups;

	}
}
```



![image](https://github.com/user-attachments/assets/50d39195-82fd-4f60-b5b8-81f08c9684b3)
***
