## 뭔가 많은 일이 있어서 수업을 못나갔따~~~~
새로운 한 주가 돌아오자마자 미니프로젝트 시작 ,,
```
using OpenCvSharp;
using System;
using System.Collections.Generic;
using DrawingPoint = System.Drawing.Point;
using DrawingSize = System.Drawing.Size;

namespace Opencv1028_Drawing_Place
{
	internal class Program
	{
		// IconFlag.hpp 파일
		public enum IconFlag
		{
			DRAW_RECTANGLE = 0,
			DRAW_CIRCLE,
			DRAW_ECLIPSE,
			DRAW_LINE,
			DRAW_BRUSH,
			ERASE,
			OPEN,
			SAVE,
			PLUS,
			MINUS,
			CLEAR,
			COLOR,
			PALETTE,
			HUE_IDX
		}

		// Menu 파일
		public static class Menu
		{
			public static List<Rect> icons = new List<Rect>();   // 아이콘 사각형 리스트
			public static Mat image = new Mat();                 // 그림판 이미지
			public static int hue;                               // hue 값 - 전역 변수

			// 아이콘 배치 메서드
			public static void PlaceIcons(DrawingSize size)
			{
				List<string> iconNames = new List<string>
				{
					"rect", "circle", "eclipe", "line", "brush", "eraser",
					"open", "save", "plus", "minus", "clear", "color"
				};

				int btnRows = (int)System.Math.Ceiling(iconNames.Count / 2.0);
				string iconBasePath = @"C:\Temp\opencv\icon\";

				for (int i = 0, k = 0; i < btnRows; i++)
				{
					for (int j = 0; j < 2 && k < iconNames.Count; j++, k++)
					{
						OpenCvSharp.Point pt = new OpenCvSharp.Point(j * size.Width, i * size.Height);
						icons.Add(new Rect(pt, new OpenCvSharp.Size(size.Width, size.Height)));

						Mat icon = Cv2.ImRead($"{iconBasePath}{iconNames[k]}.jpg");
						if (icon.Empty()) continue;

						Cv2.Resize(icon, icon, new OpenCvSharp.Size(size.Width, size.Height));
						icon.CopyTo(image[icons[k]]);
					}
				}
			}

			// 색상 인덱스 생성 메서드
			public static void CreateHueIndex(Rect hueIndexRect)
			{
				Mat mHueIdx = image[hueIndexRect];
				float ratio = 180.0f / hueIndexRect.Height;

				for (int i = 0; i < hueIndexRect.Height; i++)
				{
					Scalar hueColor = new Scalar(i * ratio, 255, 255);
					mHueIdx.Row(i).SetTo(hueColor);
				}
				Cv2.CvtColor(mHueIdx, mHueIdx, ColorConversionCodes.HSV2BGR);
			}

			// 팔레트 생성 메서드
			public static void CreatePalette(int posY, Rect paletteRect)
			{
				Mat mPalette = image[paletteRect];
				float ratio1 = 180.0f / paletteRect.Height;
				float ratio2 = 256.0f / paletteRect.Width;
				float ratio3 = 256.0f / paletteRect.Height;

				hue = (int)System.Math.Round((posY - paletteRect.Y) * ratio1);

				for (int i = 0; i < mPalette.Rows; i++)
				{
					for (int j = 0; j < mPalette.Cols; j++)
					{
						int saturation = (int)System.Math.Round(j * ratio2);
						int intensity = (int)System.Math.Round((mPalette.Rows - i - 1) * ratio3);
						mPalette.Set<Vec3b>(i, j, new Vec3b((byte)hue, (byte)saturation, (byte)intensity));
					}
				}
				Cv2.CvtColor(mPalette, mPalette, ColorConversionCodes.HSV2BGR);
			}
		}

		// Place Menu 파일
		static void Main(string[] args)
		{
			Menu.image = new Mat(new OpenCvSharp.Size(800, 500), MatType.CV_8UC3, Scalar.All(255));
			Menu.PlaceIcons(new DrawingSize(60, 60));

			Rect lastIcon = Menu.icons[^1];
			OpenCvSharp.Point startPale = new OpenCvSharp.Point(0, lastIcon.Bottom + 5);

			Menu.icons.Add(new Rect(startPale, new OpenCvSharp.Size(100, 100)));
			Menu.icons.Add(new Rect(startPale + new OpenCvSharp.Point(105, 0), new OpenCvSharp.Size(15, 100)));

			Menu.CreateHueIndex(Menu.icons[(int)IconFlag.HUE_IDX]);
			Menu.CreatePalette(startPale.Y, Menu.icons[(int)IconFlag.PALETTE]);

			Cv2.ImShow("image", Menu.image);
			Cv2.WaitKey();
		}
	}
}
```
![image](https://github.com/user-attachments/assets/170fd522-6d4d-416c-a41a-29a808552688)



이런식으로 나온다~~~~ 이게 레벨 1
***
