<div align="center">
  <a href="...">
    <img src="..." alt="Logo" width="80" height="80">
  </a>

  <h3 align="center">.Net-Core MVC</h3>

  <p align="center">
    This project is created for learning purpose!
    <br />
  </p>
</div>

## Need to know before starting!
I am working with dotnet 8.0 and using Visual studio code!
## Let's go!
* Using command line from Visual studio code to create your project
  ```sh
  dotnet new mvc -o YourNameProject
  code -r YourNameProject
   ```
* Trust the HTTPS development certificate by running the following command:
  ```sh
  dotnet dev-certs https --trust
   ```
* Some computer is not working with nuget, try to these steps:
  ```sh
  dotnet nuget add source "https://api.nuget.org/v3/index.json" --name "nuget.org"
   ```
    Then:
       ```
        dotnet tool install --global dotnet-aspnet-codegenerator
       ```
  * Add Microsoft.EntityFrameworkCore.SqlServer:
  ```sh
  dotnet add package Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore --version 8.0.4
   ```
  * Add Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore:
  ```sh
   dotnet add package Microsoft.EntityFrameworkCore.SqlServer --version 8.0.4
  ```
* Create a new folder: "Model". Now we move to create some models that we need!
<div><h1>The Student entity<h1></div>
  
```sh
using System;
using System.Collections.Generic;

namespace ContosoUniversity.Models
{
    public class Student
    {
        public int ID { get; set; }
        public string LastName { get; set; }
        public string FirstMidName { get; set; }
        public DateTime EnrollmentDate { get; set; }

        public ICollection<Enrollment> Enrollments { get; set; }
    }
}
```
* Create the database context!
In the project folder, create a folder named Data.
In the Data folder create a SchoolContext class with the following code:
```sh
using ContosoUniversity.Models;
using Microsoft.EntityFrameworkCore;

namespace ContosoUniversity.Data
{
    public class SchoolContext : DbContext
    {
        public SchoolContext(DbContextOptions<SchoolContext> options) : base(options)
        {
        }
        public DbSet<Student> Students { get; set; }
    }
}
```
<div><h1>Connection to SQL SERVER<h1></div>

Open file program.cs, we need to add some configuration to make sure that's our connection is correct!
This is a default file.
```sh
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

```
Now we add some new lines below ```var builder = WebApplication.CreateBuilder(args); ```.
```sh
if (builder.Environment.IsDevelopment())
{
     builder.Services.AddDbContext<SchoolContext>(options =>
        options.UseSqlServer(builder.Configuration.GetConnectionString("MyTestConnection")));
}
else
{
    builder.Services.AddDbContext<MvcMovieContext>(options =>
        options.UseSqlServer(builder.Configuration.GetConnectionString("DefaultConnection")));
}
```
Open the appsettings.json file and add a connection string as shown in the following markup (i am using local, so i often use with '.'):
```sh
"ConnectionStrings": {
    "MyTestConnection": "Server=.;Database=MovieDb;Integrated Security=True;TrustServerCertificate=true"
  },
```


 
