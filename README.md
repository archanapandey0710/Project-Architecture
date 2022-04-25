Architecture Steps:

Api Architecture
1. Create Blank Solution from File->New>Project->New Solution.

2. Crate Folder as per structure.

3. Create Generic Enum Files :
   1. Create a Class Library inside SharedService 
   
4. Add Generic Repo Files:
   1. Create Class Library inside Shared Service
   2. Add Entity Framework Core from NuGet Package
   
5. Add Gateway :
    1. Click File -> New Project  ->asp.net mvc core api Project 
	
6. Add Reference Project (Enum,Helper,Repo) to the CommonService.Repo Project
    1. Right Click on Dependencies->Add Reference -> select the respective project by checking check box and add.
	 
7. Add Entity Framework and Create Database Context using Database First Approach:
     1. Install below packages:
		 1. Install-Package Microsoft.EntityFrameworkCore.SqlServer
		 2. Install-Package Microsoft.EntityFrameworkCore.Tools –Pre
		 3. Install-Package Microsoft.EntityFrameworkCore.SqlServer.Design   
		 4. Install-Package Microsoft.EntotyFramework.Relational
	   
8. Create Database Context File using below syntax:   
   Scaffold-DbContext "Server=LENOVO-PC;Database=Sample;Trusted_Connection=True;" Microsoft.EntityFrameworkCore.SqlServer -OutputDir Context -Context "CommonDbContext" -DataAnnotations
   
9. If we want to update  database and context then use the below "force" below commands:
    Scaffold-DbContext "Server=LENOVO-PC;Database=Sample;Trusted_Connection=True;" Microsoft.EntityFrameworkCore.SqlServer -OutputDir Context -Context "CommonDbContext" -DataAnnotations --force
	
10. Configuration of connection string in CommonService.API project:
     1. Add ConnectionStrings in appsettings.json file inside CommonService.API Project
	      "ConnectionStrings": {
              "CommonConnection": "Data Source=solodev.database.windows.net;Initial Catalog=BillingService;User ID=solouser; Password=Platinum$star555",
            },
	 2. Install Entity Framework Packages:
		  1. Install-Package Microsoft.EntityFrameworkCore
		  2. Install-Package Microsoft.EntityFrameworkCore.SqlServer
		  3. Install-Package Microsoft.EntityFrameworkCore.Tools –Pre
		  4. Install-Package Microsoft.EntityFrameworkCore.SqlServer.Design
		   
11. Change CommonDbContext File whenever add or update it:
      1. replace DbContext to GenericDataContext	
      2. Remove paremeter less constructor	  
	  
12. Install Automapper in CommonService.Service Project:
     1. Install-Package AutoMapper.Extensions.Microsoft.DependencyInjection
		
13. Install Automapper in CommonService.API Project:
      1. Install-Package AutoMapper.Extensions.Microsoft.DependencyInjection
14. Implement Swagger in Gateway Project:
    1. Install-Package Swashbuckle.AspNetCore.	  
	2. Install-Package Microsoft.AspNet.WebApi.Client.
	 
15. mark Uncheck SSL from Gateway Project if it is Enable .