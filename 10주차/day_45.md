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
