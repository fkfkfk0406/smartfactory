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


