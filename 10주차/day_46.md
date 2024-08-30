## 10주차 마지막날
## 퀴즈 ( 사칙연산 )
```
//Index

@model Sumary;

@{

    ViewData["Title"] = "Home Page";

}



<div class="text-center">

    <h1 class="display-4">Welcome</h1>

</div>

<div class="container">

    <div class="row">

        <div class="co-sm-4">

            <form class="d-grid" asp-action="Sumary" asp-controller="Home" method="post">

                <label>숫자 1 :</label>

                <input asp-for="num1" class="form-control"/>

                <label>숫자 2 :</label>

                <input asp-for="num2" class="form-control" />

                <input type="submit" value="사칙연산" class="btn btn-outline-primary" />

                <br />

                @if (ViewBag.sum != null)

                {

                    <p>sum : @ViewBag.sum</p>

                    <p>difference : @ViewBag.dif</p>

                    <p>product : @ViewBag.pro</p>

                    <p>divide : @ViewBag.div</p>

                }

            </form>

        </div>

    </div>

</div>


//controller

using System.Diagnostics;

using Microsoft.AspNetCore.Mvc;

using TagHelper_Form.Models;



namespace TagHelper_Form.Controllers

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

        public IActionResult Sumary(int num1, int num2)

        {

            ViewBag.sum = num1 + num2;

            ViewBag.dif = num1 - num2;

            ViewBag.pro = num1 * num2;

            ViewBag.div = (double)(num1 / num2);

            return View("Index");

        }



        [ResponseCache(Duration = 0, Location = ResponseCacheLocation.None, NoStore = true)]

        public IActionResult Error()

        {

            return View(new ErrorViewModel { RequestId = Activity.Current?.Id ?? HttpContext.TraceIdentifier });

        }

    }

}


//model
namespace TagHelper_Form.Models
{
    public class Sumary
    {
        public int num1{ get; set; }
        public int num2{ get; set; }
        public int sum {  get; set; }
        public int dif {  get; set; }
        public int pro { get; set; }
        public double div { get; set; }
    }
}
```
## 현재 시간 출력
```
//program.cs



namespace Quiz

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

------------------------------------------------------------------------------
//Date


@{
    ViewData["Title"] = "Date";
}

<h1>Date</h1>
<p>현재 날짜는: @DateTime.Now.ToString("yyyy-MM-dd") 입니다.</p>
--------------------------------------------------------------------------------
//Index

@{
    ViewData["Title"] = "Home Page";
}

<div class="text-center">
    <h1 class="display-4">Welcome</h1>
</div>
<div class="text-center">
<a href="/Home/Date" class="btn btn-success">현재 시간 확인</a>
</div>
```
## 헤더 푸터 꾸미기
```
@{

	ViewData["Title"] = "Home Page";

}

<header>

<div class="row bg-info">

	<div class="col-lg">Header</div>

</div>

</header>



<div class="text-center">

	<h1 class="display-4">Welcome</h1>

</div>



<footer>ehdus5940@naver.com</footer>

```
## bmi 구하는 머시기 만들기
```
//controller

using System.Diagnostics;

using bmiquiz.Models;

using Microsoft.AspNetCore.Mvc;



namespace bmiquiz.Controllers

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

		public IActionResult PIBW(PIBW model)

		{

			if (ModelState.IsValid)

			{

				double pibw = 0;

				if (model.height > 0)

				{

					if (model.Gender == Gender.남자)

					{

						pibw = (model.weight / (model.height * model.height)) * 22;

					}

					else

					{

						pibw = (model.weight / (model.height * model.height)) * 21;

					}



					ViewBag.PIBW = pibw;



					if (pibw < 90)

					{

						ViewBag.Message = "저체중 입니다.";

					}

					else if (pibw >= 90 && pibw <= 110)

					{

						ViewBag.Message = "정상 입니다.";

					}

					else if (pibw > 110 && pibw <= 120)

					{

						ViewBag.Message = "과체중 입니다.";

					}

					else if (pibw > 120 && pibw <= 130)

					{

						ViewBag.Message = "경도비만 입니다.";

					}

					else if (pibw > 130 && pibw <= 160)

					{

						ViewBag.Message = "중정도비만 입니다.";

					}

					else if (pibw > 160)

					{

						ViewBag.Message = "고도비만 입니다.";

					}

				}

			}

			return View();

		}



		[ResponseCache(Duration = 0, Location = ResponseCacheLocation.None, NoStore = true)]

		public IActionResult Error()

		{

			return View(new ErrorViewModel { RequestId = Activity.Current?.Id ?? HttpContext.TraceIdentifier });

		}

	}

}

---------------------------------------------------------------
// model
namespace bmiquiz.Models
{
    public class PIBW
    {
        public int height { get; set; }
        public int weight { get; set; }
        public Gender Gender { get; set; }
    }
    public enum Gender
    {
        남자, 여자
    }
}
----------------------------------------------------------------------
//view
@model PIBW
@{
	ViewData["Title"] = "PIBW";
}
<div class="container">
	<div class="row">
		<div class="col-sm-4">
			<h1>PIBW 테스트</h1>
            <form asp-action="PIBW" method="post">
			<label for="height">키 : </label>
			<input asp-for="height" class="form-control" />
			<label for="weight">몸무게 : </label>
			<input asp-for="weight" class="form-control" />
			<select asp-for="Gender" class="form-control" asp-items="Html.GetEnumSelectList<Gender>()">
				<optioin value="">성별(남자/여자)</optioin>
			</select>
			<input type="submit" value="BMI계산" class="btn btn-outline-secondary"/>
			</form>
			<br />
			@if(ViewBag.PIBW != null)
			{
				<p>@ViewBag.Message</p>
			}
		</div>
	</div>
</div>
```
