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
```
using OpenCvSharp;
using System;
using System.Collections.Generic;
using DrawingPoint = System.Drawing.Point;
using DrawingSize = System.Drawing.Size;

namespace PaintBrush_Level_Merged
{
	public static class IconFlags
	{
		public const int DRAW_RECTANGLE = 0;
		public const int DRAW_CIRCLE = 1;
		public const int DRAW_ECLIPSE = 2;
		public const int DRAW_LINE = 3;
		public const int DRAW_BRUSH = 4;
		public const int ERASE = 5;
		public const int OPEN = 6;
		public const int SAVE = 7;
		public const int PLUS = 8;
		public const int MINUS = 9;
		public const int CLEAR = 10;
		public const int COLOR = 11;
		public const int PALETTE = 12;
		public const int HUE_IDX = 13;
	}

	public class PaintToolbox
	{
		private int hue;
		private List<Rect> icons = new List<Rect>();
		private Mat image;
		private int mouse_mode = 0;
		private int draw_mode = 0;
		private Point pt1;
		private Point pt2;
		private Scalar color = new Scalar(0, 0, 0);

		public List<Rect> Icons => icons;
		public Mat Image => image;

		public void SetImage(Mat img)
		{
			this.image = img;
		}

		public void PlaceIcons(DrawingSize size)
		{
			List<string> iconNames = new List<string>
			{
				"rect", "circle", "eclipe", "line", "brush", "eraser",
				"open", "save", "plus", "minus", "clear", "color"
			};

			int btnRows = (int)Math.Ceiling(iconNames.Count / 2.0);
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

		public void CreateHueIndex(Rect rect)
		{
			Mat mHueIdx = image.SubMat(rect);
			float ratio = 180.0f / rect.Height;

			for (int i = 0; i < rect.Height; i++)
			{
				Scalar hueColor = new Scalar(i * ratio, 255, 255);
				mHueIdx.Row(i).SetTo(hueColor);
			}
			Cv2.CvtColor(mHueIdx, mHueIdx, ColorConversionCodes.HSV2BGR);
		}

		public void CreatePalette(int posY, Rect rectPale)
		{
			Mat mPalette = image.SubMat(rectPale);
			float ratio1 = 180.0f / rectPale.Height;
			float ratio2 = 256.0f / rectPale.Width;
			float ratio3 = 256.0f / rectPale.Height;

			hue = (int)Math.Round((posY - rectPale.Y) * ratio1);

			for (int i = 0; i < mPalette.Rows; i++)
			{
				for (int j = 0; j < mPalette.Cols; j++)
				{
					int saturation = (int)Math.Round(j * ratio2);
					int intensity = (int)Math.Round((mPalette.Rows - i - 1) * ratio3);
					mPalette.Set<Vec3b>(i, j, new Vec3b((byte)hue, (byte)saturation, (byte)intensity));
				}
			}
			Cv2.CvtColor(mPalette, mPalette, ColorConversionCodes.HSV2BGR);
		}

		public void Command(int mode)
		{
			Console.WriteLine($"Command called with mode: {mode}");

			if (mode == IconFlags.PALETTE)
			{
				float ratio1 = 256.0f / icons[IconFlags.PALETTE].Width;
				float ratio2 = 256.0f / icons[IconFlags.PALETTE].Height;

				Point pt = pt2 - icons[IconFlags.PALETTE].BottomRight;
				int saturation = (int)Math.Round(pt.X * ratio1);
				int value = (int)Math.Round((icons[IconFlags.PALETTE].Height - pt.Y - 1) * ratio2);
				Scalar hsv = new Scalar(hue, saturation, value);

				Mat m_color = image.SubMat(icons[IconFlags.COLOR]);
				m_color.SetTo(hsv);
				Cv2.CvtColor(m_color, m_color, ColorConversionCodes.HSV2BGR);
				Cv2.Rectangle(image, icons[IconFlags.COLOR], new Scalar(0, 0, 0), 1);

				Vec3b vec = m_color.At<Vec3b>(10, 10);
				color = new Scalar(vec.Item0, vec.Item1, vec.Item2);
			}
			else if (mode == IconFlags.HUE_IDX)
			{
				CreatePalette(pt2.Y, icons[IconFlags.PALETTE]);
			}
		}

		public void OnMouse(MouseEventTypes eventTypes, int x, int y, MouseEventFlags flags, IntPtr userdata)
		{
			Point pt = new Point(x, y);
			if (eventTypes == MouseEventTypes.LButtonUp)
			{
				for (int i = 0; i < icons.Count; i++)
				{
					if (icons[i].Contains(pt))
					{
						if (i < 6)
						{
							mouse_mode = 0;
							draw_mode = i;
							Command(i);
						}
						else
						{
							Command(i);
						}
						return;
					}
				}
				pt2 = pt;
				mouse_mode = 1;
			}
			else if (eventTypes == MouseEventTypes.LButtonDown)
			{
				pt1 = pt;
				mouse_mode = 2;
				Console.WriteLine("왼쪽 마우스가 클릭되었습니다.");
			}

			if (mouse_mode >= 2)
			{
				Rect rect = new Rect(0, 0, 125, image.Rows);
				mouse_mode = rect.Contains(pt) ? 0 : 3;
				pt2 = pt;
			}
		}
	}

	internal class Program
	{
		static void Main(string[] args)
		{
			Mat image = new Mat(500, 800, MatType.CV_8UC3, Scalar.All(255));
			PaintToolbox toolbox = new PaintToolbox();

			toolbox.SetImage(image);
			toolbox.PlaceIcons(new DrawingSize(60, 60));

			Rect lastIcon = toolbox.Icons.Last();
			OpenCvSharp.Point startPale = new OpenCvSharp.Point(0, lastIcon.Bottom + 5);

			toolbox.Icons.Add(new Rect(startPale, new OpenCvSharp.Size(100, 100)));
			toolbox.Icons.Add(new Rect(startPale + new OpenCvSharp.Point(105, 0), new OpenCvSharp.Size(15, 100)));

			toolbox.CreateHueIndex(toolbox.Icons[IconFlags.HUE_IDX]);
			toolbox.CreatePalette(startPale.Y, toolbox.Icons[IconFlags.PALETTE]);

			Cv2.ImShow("image", toolbox.Image);
			Cv2.SetMouseCallback("image", toolbox.OnMouse);

			Cv2.WaitKey();
		}
	}
}
```
클릭을 감지 할 수 있도록 코드를 추가해봤다.



![image](https://github.com/user-attachments/assets/94339129-2670-42d0-bdc8-64988785001f)
***
