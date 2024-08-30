## 10주차 마지막날
## 퀴즈 ( 사칙연산 )
````
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
## ㅇㅁㅇㄹ
