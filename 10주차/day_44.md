## 오늘도 c# 웹 앱을 만들어봤당
```
using Microsoft.AspNetCore.Mvc;

namespace QuizEmptyApp
{
    public class MyController : Controller
    {
        public IActionResult Index()
        {
            return View();
        }
        public IActionResult MyPage()
        {
            return View();
        }
        [HttpGet]
        public IActionResult InputQuiz()
        {
            return View();
        }
        [HttpPost]
        public IActionResult OutputQuiz(int number)
        {
            ViewBag.Result = number;
            return View();
        }
    }
}
```
```

@{
    ViewData["Title"] = "InputQuiz";
}

<h1>InInputQuiz</h1>

<form action="My/OutputQuiz" method="post">
    <label>숫자를 넣어 주세요 : </label>
    <input type="number" id="number" name="number" value="5" required/>
    <input type="submit" value="계산" />
</form>

```
```

@{
    ViewData["Title"] = "OutputQuiz";
}

<h1>OutputQuiz</h1>
@if (ViewBag.Result != null)
{
    <h3>결과는 : @ViewBag.Result </h3>
}
```
## 실행 결과
![image](https://github.com/user-attachments/assets/0353e1d4-7ad5-4126-a2ec-84de99e8946d)



![image](https://github.com/user-attachments/assets/6a48699f-5413-4d6d-a442-5dfcae09da6b)
***
### viewbag 실습
```
namespace ViewDataEmpty
{
    public class Program
    {
        public static void Main(string[] args)
        {
            var builder = WebApplication.CreateBuilder(args);
            builder.Services.AddControllersWithViews();
            var app = builder.Build();

            app.UseStaticFiles();
            app.UseRouting();

            app.MapControllerRoute(
                name: "dafault",
                pattern: "{controller=Home}/{action=UseViewBag}/{id?}");

            app.Run();
        }
    }
}
```
```

@{
    ViewData["Title"] = "UseViewBag";
}

<h1>UseViewBag</h1>
<p></p>
<span>첫번째 데이터 : </span> @ViewBag.data1
<br />
<span>두번째 데이터 : </span> @ViewBag.data2
<br />
<span>세번째 데이터 : </span> @ViewBag.data3
<br />
```
```

@{
    ViewData["Title"] = "Index";
}

<h1>Index</h1>

<h3>@TempData["person1"]</h3>
<h3>@ViewData["person2"]</h3>
```
## 실행 결과
![image](https://github.com/user-attachments/assets/4a91e9a4-deed-40ea-9ad1-42e5797f4f93)
***
