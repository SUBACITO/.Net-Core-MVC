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
<h1>The Student entity<h1>
  
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

 
