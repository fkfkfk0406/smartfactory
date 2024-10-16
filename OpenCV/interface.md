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


