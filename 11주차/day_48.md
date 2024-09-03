## 개강 2일차,, 종강하고싶다.
## 어제 한거 복습 후 개인 프로젝트 !
```
﻿﻿1단계 프로그램   



ADDR_ID  NAME         HP          

1         홍길동    010-1111-1111

2         강호동    010-2222-2222

3         유재석    010-3333-3333



C# 을 이용하여 다음과 같은 프로그램을 만들어 주세요.



콘솔 메뉴를 만든 후 번호를 누르면 해당 작업을 수행하여 주세요.



------------------------------------------------------------

1. 데이터 삽입

2. 데이터 삭제

3. 데이터 조회

4. 데이터 수정



메뉴 : 1



ID를 입력해 주세요 : 1

이름을 입력해 주세요 : 홍길동

전화번호를 입력해 주세요 : 010-1111-1111



데이터가 정상적으로 입력되었습니다.

-----------------------------------------------------------------

1. 데이터 삽입

2. 데이터 삭제

3. 데이터 조회

4. 데이터 수정



메뉴 : 3 



ADDR_ID  NAME         HP         

1         홍길동    010-1111-1111
```
## 문제 풀이
```
using System.Collections.Generic;

using System.ComponentModel.DataAnnotations.Schema;

using System.ComponentModel.DataAnnotations;

using System.Reflection.Emit;

using Microsoft.EntityFrameworkCore;



namespace ConsoleApp81

{

	public class ADDBOOK

	{

		[Key]

		[DatabaseGenerated(DatabaseGeneratedOption.Identity)]

		public int ADD_ID { get; set; }

		[MaxLength(100)]

		public string NAME { get; set; }

		[MaxLength(100)]

		public String HP { get; set; }

	}

	public class ADDBOOKDbContext : DbContext

	{

		public DbSet<ADDBOOK> AddBook { get; set; }



		protected override void OnConfiguring(DbContextOptionsBuilder optionsBuilder)

		{

			optionsBuilder.UseSqlServer("Server = (local)\\SQLEXPRESS; " +

						"Database = ExamDb; " +

						"Trusted_Connection = True;" +

						"Encrypt=False");

		}



		protected override void OnModelCreating(ModelBuilder modelBuilder)

		{

			modelBuilder.Entity<ADDBOOK>()   //Primary key 지정

				.HasKey(p => p.ADD_ID);



			modelBuilder.Entity<ADDBOOK>()   //Varchar2(30) 30크기를 정할 때

				.Property(p => p.NAME)

				.HasMaxLength(30);



			modelBuilder.Entity<ADDBOOK>()

				.Property(p => p.HP)

				.HasMaxLength(30);

		}

	}



	internal class Program

	{

		static void Main(string[] args)

		{

			using (var context = new ADDBOOKDbContext())

			{

				context.Database.EnsureDeleted();

				context.Database.EnsureCreated();



				int choice = 0;



				do

				{

					Console.WriteLine("1. 데이터 삽입");

					Console.WriteLine("2. 데이터 삭제");

					Console.WriteLine("3. 데이터 조회");

					Console.WriteLine("4. 데이터 수정");

					Console.WriteLine("5. 종료");

					Console.Write("메뉴 : ");

					choice = Int32.Parse(Console.ReadLine());



					switch (choice)

					{

						case 1:

							InsertData(context);

							break;

						case 2:

							DeleteData(context);

							break;

						case 3:

							RetrieveData(context);

							break;

						case 4:

							UpdateData(context);

							break;

						case 5:

							Console.WriteLine("프로그램을 종료합니다.");

							break;

						default:

							Console.WriteLine("잘못된 입력입니다.");

							break;

					}

				} while (choice != 5);

			}

		}



		private static void InsertData(ADDBOOKDbContext context)

		{

			var addBook = new ADDBOOK();



			Console.Write("이름을 입력해 주세요: ");

			addBook.NAME = Console.ReadLine();

			Console.Write("전화번호를 입력해 주세요: ");

			addBook.HP = Console.ReadLine();



			context.AddBook.Add(addBook);

			context.SaveChanges();

			Console.WriteLine("데이터가 정상적으로 입력되었습니다.");

		}



		private static void DeleteData(ADDBOOKDbContext context)

		{

			Console.Write("삭제할 ID를 입력해 주세요: ");

			int id = Int32.Parse(Console.ReadLine());



			var entry = context.AddBook.FirstOrDefault(e => e.ADD_ID == id);

			if (entry != null)

			{

				context.AddBook.Remove(entry);

				context.SaveChanges();

				Console.WriteLine("데이터가 정상적으로 삭제되었습니다.");

			}

			else

			{

				Console.WriteLine("해당 ID를 찾을 수 없습니다.");

			}

		}



		private static void RetrieveData(ADDBOOKDbContext context)

		{

			var list = context.AddBook.ToList();

			Console.WriteLine("ADDR_ID  NAME         HP");

			foreach (var item in list)

			{

				Console.WriteLine($"{item.ADD_ID}    {item.NAME}    {item.HP}");

			}

		}

		 

		private static void UpdateData(ADDBOOKDbContext context)

		{

			Console.Write("수정할 ID를 입력해 주세요: ");

			int id = Int32.Parse(Console.ReadLine());



			var entry = context.AddBook.FirstOrDefault(e => e.ADD_ID == id);

			if (entry != null)

			{

				Console.Write("새로운 이름을 입력해 주세요: ");

				entry.NAME = Console.ReadLine();

				Console.Write("새로운 전화번호를 입력해 주세요: ");

				entry.HP = Console.ReadLine();



				context.SaveChanges();

				Console.WriteLine("데이터가 정상적으로 수정되었습니다.");

			}

			else

			{

				Console.WriteLine("해당 ID를 찾을 수 없습니다.");

			}

		}

	}

}
```
