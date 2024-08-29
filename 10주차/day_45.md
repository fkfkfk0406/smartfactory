## 목요일,,?? 너무 빠른 시간
## 복습겸 퀴즈겸 학습~~~!!
```
﻿TempData 사용하기

ViewBag 사용하기



---------------------------------------

두 데이터를 컨트롤러(MyController.cs)에서 만들고



string[] books = { "C#프로그래밍", "Java 정복", "HTML5", "CSS 하루만에하기" } --> TempData



List[] foods = {"된장국", "김치찌게", "소금빵", "두루치기"}  --> ViewBag



Output.cshtml에 출력해보세요.

```
## 풀이 
```
namespace dataquiz

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

                pattern: "{controller=Home}/{action=Output}/{id?}");



            app.Run();

        }

    }

}

----------------------------------------------------------
@{
	ViewData["Title"] = "Output";
	var foods = ViewBag.foods as List<string>;
	var books = TempData["books"] as string[];

}

<div class="text-center">
	<h1>Output</h1>
	<hr />
	@{
		foreach (var item in books)
		{
			<h3>@item</h3>
		}
	}
	<hr />

	@{
		foreach (var item in foods)
		{
			<h3>@item</h3>
		}
	}
</div>
```
## view import
```
namespace WebApplication6
{
    public class Program
    {
        public static void Main(string[] args)
        {
            var builder = WebApplication.CreateBuilder(args);

            // Add services to the container.
            builder.Services.AddControllersWithViews();

            var app = builder.Build();

            // Configure the HTTP request pipeline.
            if (!app.Environment.IsDevelopment())
            {
                app.UseExceptionHandler("/Home/Error");
                // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
                app.UseHsts();
            }

            app.UseHttpsRedirection();
            app.UseStaticFiles();

            app.UseRouting();

            app.UseAuthorization();

            app.MapControllerRoute(
                name: "default",
                pattern: "{controller=Home}/{action=Index}/{id?}");

            app.Run();
        }
    }
}
```
```
@model IEnumerable<Student>
@{
	ViewData["Title"] = "Home Page";
}

<div class="text-center">
	<h1 class="display-4">Main Page</h1>

	@{
		foreach (var item in Model)
		{
			<p>@item.Id</p>
			<p>@item.Name</p>
			<p>@item.HP</p>
		}
	}

</div>
```
```
namespace WebApplication6.Models
{
    public class Student
    {
        public int Id { get; set; }
        public string Name { get; set; }
        public string HP { get; set; }
    }
}
```
## 실행 결과

![image](https://github.com/user-attachments/assets/6a883072-facd-442a-b392-6d51564f6d35)
***
## tag helper
```
using System.Diagnostics;
using Microsoft.AspNetCore.Mvc;
using TagHelplersApp.Models;

namespace TagHelplersApp.Controllers
{
	public class HomeController : Controller
	{
		private readonly ILogger<HomeController> _logger;

		public HomeController(ILogger<HomeController> logger)
		{
			_logger = logger;
		}

		public IActionResult Index()
		{
			return View();
		}

		public IActionResult Privacy()
		{
			return View();
		}
        public IActionResult Contact()
        {
            return View();
        }

        [ResponseCache(Duration = 0, Location = ResponseCacheLocation.None, NoStore = true)]
		public IActionResult Error()
		{
			return View(new ErrorViewModel { RequestId = Activity.Current?.Id ?? HttpContext.TraceIdentifier });
		}
	}
}
```
```
@{
    ViewData["Title"] = "Home Page";
}

<div class="text-center">
    <h1 class="display-4">TagHelpers</h1>
</div>


<div>
    @*Link 만들기 *@

    <a href="/Home/Contact">Contact Page 1</a> <br />

    @Html.ActionLink("Contact Page 2", "Contact", "Home") <br />

    <a href="@Url.Action("Contact", "Home")"> Contact Page 3</a> <br />

    <a asp-controller="Home" asp-action="Contact">Contact Page 4</a>

</div>
```
## 실행 결과

![image](https://github.com/user-attachments/assets/6cc6705a-4cbc-4fee-839d-8f5a8d24d689)




![image](https://github.com/user-attachments/assets/a53b1191-6b0e-47ab-859d-35a8a0ee9818)

## 부트스트링
```
@model Student
@{
	ViewData["Title"] = "Home Page";
}

<div class="text-center">
	<h1 class="display-4">Welcome</h1>
	<p>Learn about <a href="https://learn.microsoft.com/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
</div>

<div class="container">
	<h1>부트 스트링을 공부해 봅시다</h1>
	<p>텍스트를 입력합니다.</p>
</div>
<div class="container">
	<h1>My First Bootstrap Page</h1>
	<p>This is some text.</p>
</div>

<div class="container p-5 my-5 border">
	<h1>부트 스트링을 공부해 봅시다</h1>
	<p>텍스트를 입력합니다.</p>
</div>
<div class="container p-5 my-5 bg-danger border">
	<h1>부트 스트링을 공부해 봅시다</h1>
	<p>텍스트를 입력합니다.</p>
</div>
<div class="container p-5 my-5 bg-primary border">
	<h1>부트 스트링을 공부해 봅시다</h1>
	<p>텍스트를 입력합니다.</p>
</div>
```
## 실행결과

![image](https://github.com/user-attachments/assets/07f84e72-52be-427a-a3cf-1e4eb8e9ac3d)

## 나머지 여러가지를 실습 해봤다.
```
@model Student
@{
	ViewData["Title"] = "Home Page";
}

<div class="text-center">
	<h1 class="display-4">Welcome</h1>
	<p>Learn about <a href="https://learn.microsoft.com/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
</div>

<div class="container">
	<h1>부트 스트링을 공부해 봅시다</h1>
	<p>텍스트를 입력합니다.</p>
</div>
<div class="container">
	<h1>My First Bootstrap Page</h1>
	<p>This is some text.</p>
</div>

<div class="container p-5 my-5 border">
	<h1>부트 스트링을 공부해 봅시다</h1>
	<p>텍스트를 입력합니다.</p>
</div>
<div class="container p-5 my-5 bg-danger border">
	<h1>부트 스트링을 공부해 봅시다</h1>
	<p>텍스트를 입력합니다.</p>
</div>
<div class="container p-5 my-5 bg-primary border">
	<h1>부트 스트링을 공부해 봅시다</h1>
	<p>텍스트를 입력합니다.</p>
</div>

<div class="row bg-info">
	<div class="col-lg">.col-sm-3</div>
	<div class="col-lg">.col-sm-3</div>
	<div class="col-lg">.col-sm-3</div>
	<div class="col-lg">.col-sm-3</div>
</div>

<table class="table">
    <thead>
        <tr>
            <th>Firstname</th>
            <th>Lastname</th>
            <th>Email</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>John</td>
            <td>Doe</td>
            <td>john@example.com</td>
        </tr>
        <tr>
            <td>Mary</td>
            <td>Moe</td>
            <td>mary@example.com</td>
        </tr>
        <tr>
            <td>July</td>
            <td>Dooley</td>
            <td>july@example.com</td>
        </tr>
    </tbody>
</table>
```
## 실행결과

![image](https://github.com/user-attachments/assets/3810b7f3-241c-4f32-ae48-552570bd1926)
