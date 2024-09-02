## 개강했다,,!
오늘은 sql express를 사용 해 봤다.
![image](https://github.com/user-attachments/assets/49207971-a95d-46c2-81f2-1af0a94b1742)



![image](https://github.com/user-attachments/assets/b40f4556-b48b-4688-86ca-58111b72db0c)



sql developer랑 사용하는건 비슷한데 뭔가 뭔가 뭔가 어색하다.
***
## visual studio로 sql express에 데이터베이스를 추가하고 테이블을 추가했다.
```
using Microsoft.EntityFrameworkCore;

namespace EF8_001
{
	public class Person
	{
		public int ID { get; set; }
		public string NAME { get; set; }
		public int AGE { get; set; }
		public string JOB { get; set; }
	}
	public class PersonDbContext : DbContext
	{
		public DbSet<Person> Person { get; set; }

		protected override void OnConfiguring(DbContextOptionsBuilder optionsBuilder)
		{
			optionsBuilder.UseSqlServer("Server = (local)\\SQLEXPRESS; " +
						"Database = MyDb; " +
						"Trusted_Connection = True;" +
						"Encrypt=False");
		}
		protected override void OnModelCreating(ModelBuilder modelBuilder)
		{
			modelBuilder.Entity<Person>()   //Primary key 지정
				.HasKey(p => p.ID);

			modelBuilder.Entity<Person>()   //Varchar2(30) 30크기를 정할 때
				.Property(p => p.NAME)
				.HasMaxLength(30);

			modelBuilder.Entity<Person>()
				.Property(p => p.JOB)
				.HasMaxLength(30);
		}
	}
	internal class Program
	{
		

		static void Main(string[] args)
		{
			using (var context = new PersonDbContext())
			{
				// 데이터베이스와 테이블 생성
				//context.Database.EnsureDeleted(); //기존의 테이블이 있을경우 삭제를 단행하는데 DB자체를 지우는 명령어라 타 테이블도 삭제됩니다.
				//조심해서 사용해야할 필요가 있습니다.
				context.Database.EnsureCreated();   //테이블 또는 DB를 만드는 명령어인데 기존에 존재하는 파일이 있다면 아무 작업도 하지 않습니다.
				Console.WriteLine("데이터베이스 테이블이 생성되었습니다.");
			}
		}
	}
}
```
```
using Microsoft.EntityFrameworkCore.Migrations;

#nullable disable

namespace EF8_001.Migrations
{
    /// <inheritdoc />
    public partial class InitEF8_001 : Migration
    {
        /// <inheritdoc />
        protected override void Up(MigrationBuilder migrationBuilder)
        {
            migrationBuilder.CreateTable(
                name: "Person",
                columns: table => new
                {
                    ID = table.Column<int>(type: "int", nullable: false)
                        .Annotation("SqlServer:Identity", "1, 1"),
                    NAME = table.Column<string>(type: "nvarchar(30)", maxLength: 30, nullable: false),
                    AGE = table.Column<int>(type: "int", nullable: false),
                    JOB = table.Column<string>(type: "nvarchar(30)", maxLength: 30, nullable: false)
                },
                constraints: table =>
                {
                    table.PrimaryKey("PK_Person", x => x.ID);
                });
        }

        /// <inheritdoc />
        protected override void Down(MigrationBuilder migrationBuilder)
        {
            migrationBuilder.DropTable(
                name: "Person");
        }
    }
}
```
![image](https://github.com/user-attachments/assets/7bce04f3-a474-48f1-a6c4-d6f7dfb4ac02)

***
## web mvc_crud
![image](https://github.com/user-attachments/assets/4db27958-b093-459e-8f34-8d568855da78)



![image](https://github.com/user-attachments/assets/44b5db5b-2167-4c83-bdd0-1a042ebcba71)



![image](https://github.com/user-attachments/assets/376f44dd-0cf6-4b75-bef3-188697919099)


