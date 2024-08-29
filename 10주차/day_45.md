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
