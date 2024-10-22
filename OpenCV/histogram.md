```
using OpenCvSharp;

namespace ConsoleApp87
{
	internal class Program
	{
		// 히스토그램 계산 함수
		static Mat CalcHisto(Mat image, int bins = 256, int rangeMax = 256)
		{
			Mat hist = new Mat();
			int[] histSize = { bins };
			Rangef[] ranges = { new Rangef(0, rangeMax) };
			int[] channels = { 0 };

			// 히스토그램 계산
			Cv2.CalcHist(new[] { image }, channels, null, hist, 1, histSize, ranges);

			return hist;
		}

		// 히스토그램 그리기 함수
		static Mat DrawHisto(Mat hist, Size? size = null)
		{
			Size histSize = size ?? new Size(256, 200);  // 기본 사이즈 할당
			Mat histImg = new Mat(histSize, MatType.CV_8UC1, Scalar.All(255));  // 흰색 배경

			float binWidth = (float)histImg.Cols / hist.Rows;
			Cv2.Normalize(hist, hist, 0, histImg.Rows, NormTypes.MinMax);

			for (int i = 0; i < hist.Rows; i++)
			{
				float startX = i * binWidth;
				float endX = (i + 1) * binWidth;
				Point pt1 = new Point((int)startX, histImg.Rows);
				Point pt2 = new Point((int)endX, histImg.Rows - Math.Round(hist.At<float>(i)));

				// 사각형 그리기 (히스토그램 막대)
				if (pt2.Y > 0)
				{
					Cv2.Rectangle(histImg, pt1, pt2, Scalar.All(0), -1);  // 검은색 막대
				}
			}

			return histImg;
		}

		static void Main(string[] args)
		{
			// 이미지 읽기 (그레이스케일)
			string imagePath = "C:\\Temp\\opencv\\cv_imgs_2\\pixel_test.jpg";
			Mat image = Cv2.ImRead(imagePath, ImreadModes.Grayscale);
			if (image.Empty())
			{
				Console.WriteLine("이미지를 읽을 수 없습니다: " + imagePath);
				return;
			}

			// 히스토그램 계산 및 그리기
			Mat hist = CalcHisto(image, 256);  // 히스토그램 계산
			Mat histImg = DrawHisto(hist);     // 히스토그램 이미지 생성

			// 이미지 출력
			Cv2.ImShow("Image", image);
			Cv2.ImShow("Histogram", histImg);
			Cv2.WaitKey();  // 사용자 키 입력 대기
			Cv2.DestroyAllWindows();
		}
	}
}
```
![image](https://github.com/user-attachments/assets/9d918fac-be89-4733-8eea-f2902c2af615)
***
