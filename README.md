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
 ```sh
  dotnet tool install --global dotnet-aspnet-codegenerator
   ```
* Create a new folder: "Model". Now we move to create some models that we need!
 
