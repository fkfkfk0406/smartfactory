## 스도쿠 이미지에 adaptiveThreshold 를 적용 해봣다~~
```
using OpenCvSharp;

namespace sudoku
{
	internal class Program
	{
		static void Main(string[] args)
		{
			// 이미지 파일 경로
			string imagePath = @"C:\Temp\opencv\cv_imgs/sudoku.png";

			// 이미지를 그레이스케일로 읽기
			Mat src = Cv2.ImRead(imagePath, ImreadModes.Grayscale);
			Cv2.ImShow("src", src);

			// Otsu의 이진화 적용
			Mat dst = new Mat();
			Cv2.Threshold(src, dst, 0, 255, ThresholdTypes.Binary | ThresholdTypes.Otsu);
			Cv2.ImShow("dst", dst);

			// 적응형 이진화 (Mean C)
			Mat dst2 = new Mat();
			Cv2.AdaptiveThreshold(src, dst2, 255, AdaptiveThresholdTypes.MeanC, ThresholdTypes.Binary, 51, 7);
			Cv2.ImShow("dst2", dst2);

			// 적응형 이진화 (Gaussian C)
			Mat dst3 = new Mat();
			Cv2.AdaptiveThreshold(src, dst3, 255, AdaptiveThresholdTypes.GaussianC, ThresholdTypes.Binary, 51, 7);
			Cv2.ImShow("dst3", dst3);

			// 대기 및 창 닫기
			Cv2.WaitKey();
			Cv2.DestroyAllWindows();
		}
	}
}
```
![image](https://github.com/user-attachments/assets/9b70233d-d848-413d-b98b-5f2ce6dcd7fc)
***
## bitwise_overlap 을 해봤다
```
using System.Numerics;
using OpenCvSharp;

namespace ConsoleApp84
{
	internal class Program
	{
		static void Main(string[] args)
		{
			// 이미지 파일 경로
			string imagePath = @"C:\Temp\opencv\cv_imgs_2/bit_test.jpg";
			string logoPath = @"C:\Temp\opencv\cv_imgs_2/logo.jpg";

			// 이미지 읽기
			Mat image = Cv2.ImRead(imagePath, ImreadModes.Color);
			Mat logo = Cv2.ImRead(logoPath, ImreadModes.Color);

			// 예외 처리
			if (image.Empty() || logo.Empty())
			{
				throw new Exception("이미지를 불러올 수 없습니다.");
			}

			// 결과 행렬 선언
			Mat logoTh = new Mat();
			Mat[] masks;

			// 로고 영상 이진화
			Cv2.Threshold(logo, logoTh, 70, 255, ThresholdTypes.Binary);

			// 로고 영상 채널 분리 (분리된 채널 수 확인)
			masks = Cv2.Split(logoTh); //알파채널이 분리가 안됨

			// 채널 수 확인
			if (masks.Length < 3)
			{
				throw new Exception("로고 이미지는 최소한 3채널이어야 합니다.");
				//확인해 보면 3개만 분리되고 mask[3]이 분리되어 나오지 않음!!!
				//masks.Length를 4로 해보고나 masks.Length == 3으로 해보면 확인할 수 있음
			}

			// 전경 통과 마스크
			Mat mask1 = new Mat();
			Cv2.ImShow("mask0", masks[0]);
			Cv2.ImShow("mask1", masks[1]);
			Cv2.ImShow("mask2", masks[2]);
			//Cv2.ImShow("mask3", masks[3]); //분리되지 않으면 당연히 안나옵니다. 

			Cv2.BitwiseOr(masks[0], masks[1], mask1);
			Mat mask3 = new Mat();
			Cv2.BitwiseOr(masks[2], mask1, mask3);
			Cv2.ImShow("3개 mask합성", mask3);

			// 배경 통과 마스크
			Mat notMask = new Mat(mask1.Size(), MatType.CV_8UC1, new Scalar(255));
			Cv2.BitwiseNot(mask3, notMask);
			Cv2.ImShow("원본로고", logo);
			Cv2.ImShow("bitwiseNot", notMask);

			// 영상 중심 좌표 계산
			Point center1 = new Point(image.Width / 2, image.Height / 2);  // 이미지 중심 좌표
			Point center2 = new Point(logo.Width / 2, logo.Height / 2);    // 로고 중심 좌표
			Point start = new Point(center1.X - center2.X, center1.Y - center2.Y); // 시작 좌표

			// 로고가 위치할 관심 영역 설정
			Rect roi = new Rect(start, logo.Size());

			// 비트 곱과 마스킹을 이용한 관심 영역의 복사
			Mat background = new Mat();
			Mat foreground = new Mat();
			Cv2.BitwiseAnd(logo, logo, foreground, mask3);
			Cv2.BitwiseAnd(new Mat(image, roi), new Mat(image, roi), background, notMask);

			// 전경과 배경 합성
			Mat dst = new Mat();
			Cv2.Add(background, foreground, dst);

			// 합성된 이미지를 원본 이미지의 관심영역에 복사
			dst.CopyTo(new Mat(image, roi));

			// 결과 이미지 출력
			Cv2.ImShow("background", background);
			Cv2.ImShow("foreground", foreground);
			Cv2.ImShow("dst", dst);
			Cv2.ImShow("image", image);
			Cv2.WaitKey(0);
		}
	}
}

```
![image](https://github.com/user-attachments/assets/f6d9fb52-f5e6-41b1-a3ee-8d8bd2a5c395)
***
## MinMAX_AutoConstrast ~~~~
```
using System.Numerics;
using OpenCvSharp;

namespace ConsoleApp84
{
	internal class Program
	{
		static void Main(string[] args)
		{
			// 이미지 파일 경로
			string imagePath = @"C:\Temp\opencv\cv_imgs_2/minMax.jpg";

			// 이미지 그레이 스케일로 읽기
			Mat image = Cv2.ImRead(imagePath, ImreadModes.Grayscale);

			// 예외 처리
			if (image.Empty())
			{
				throw new Exception("이미지를 불러올 수 없습니다.");
			}

			// 최소값, 최대값 찾기
			double minVal, maxVal;
			Cv2.MinMaxIdx(image, out minVal, out maxVal);

			// 최소값과 최대값을 사용하여 이미지 정규화
			double ratio = (maxVal - minVal) / 255.0;
			Mat dst = new Mat();
			image.ConvertTo(dst, MatType.CV_64F);  // 계산을 위해 이미지 타입을 CV_64F로 변환
			Cv2.Subtract(dst, new Scalar(minVal), dst);  // dst에서 minVal을 빼기

			// 나누기 연산 수행
			Cv2.Divide(dst, new Scalar(ratio), dst);  // ratio로 나누기

			// 계산된 결과를 다시 CV_8U로 변환하여 시각화
			dst.ConvertTo(dst, MatType.CV_8U);

			// 결과 출력
			Console.WriteLine("최소값  = " + minVal);
			Console.WriteLine("최대값  = " + maxVal);

			// 이미지 출력
			Cv2.ImShow("image", image);
			Cv2.ImShow("dst", dst);
			Cv2.WaitKey();
			Cv2.DestroyAllWindows();
		}
	}
}
```
![image](https://github.com/user-attachments/assets/526d21c3-f6f4-4f4c-b1c0-9fea496df65c)
***
## 두 이미지의 차이를 출력해봤따~~
```
using System.Numerics;
using OpenCvSharp;

namespace ConsoleApp84
{
	internal class Program
	{
		static void Main(string[] args)
		{
			// 이미지 파일 경로
			string imagePath1 = @"C:\Temp\opencv\cv_imgs_2/abs_test1.jpg";
			string imagePath2 = @"C:\Temp\opencv\cv_imgs_2/abs_test2.jpg";

			// 이미지 그레이 스케일로 읽기
			Mat image1 = Cv2.ImRead(imagePath1, ImreadModes.Grayscale);
			Mat image2 = Cv2.ImRead(imagePath2, ImreadModes.Grayscale);

			// 예외 처리
			if (image1.Empty() || image2.Empty())
			{
				throw new Exception("이미지를 불러올 수 없습니다.");
			}

			// 결과 행렬 선언
			Mat difImg = new Mat();
			Mat absDif1 = new Mat();
			Mat absDif2 = new Mat();

			// 이미지 타입을 CV_16S로 변환
			image1.ConvertTo(image1, MatType.CV_16S);
			image2.ConvertTo(image2, MatType.CV_16S);

			// 두 이미지의 차이를 계산
			Cv2.Subtract(image1, image2, difImg);

			// 관심 영역 출력
			Rect roi = new Rect(10, 10, 7, 3);
			Console.WriteLine("[difImg] = \n" + difImg[roi]);

			// 차이 이미지의 절대값 계산
			absDif1 = Cv2.Abs(difImg);

			// 이미지 타입을 다시 CV_8U로 변환
			image1.ConvertTo(image1, MatType.CV_8U);
			image2.ConvertTo(image2, MatType.CV_8U);
			difImg.ConvertTo(difImg, MatType.CV_8U);
			absDif1.ConvertTo(absDif1, MatType.CV_8U);

			// 두 이미지의 절대 차이 계산
			Cv2.Absdiff(image1, image2, absDif2);

			// 관심 영역 출력
			Console.WriteLine("[difImg] = \n" + difImg[roi] + "\n");
			Console.WriteLine("[absDif1] = \n" + absDif1[roi]);
			Console.WriteLine("[absDif2] = \n" + absDif2[roi]);

			// 결과 이미지 출력
			Cv2.ImShow("image1", image1);
			Cv2.ImShow("image2", image2);
			Cv2.ImShow("difImg", difImg);
			Cv2.ImShow("absDif1", absDif1);
			Cv2.ImShow("absDif2", absDif2);

			Cv2.WaitKey();
			Cv2.DestroyAllWindows();
		}
	}
}
```
![image](https://github.com/user-attachments/assets/f582210b-9f88-427d-9a1f-9039e6ac0e59)
***
