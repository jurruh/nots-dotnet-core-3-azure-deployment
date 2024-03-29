# Azure Deployment
Prerequisites:
- Azure Account with some credits
- Visual Studio 2019 connected with an Azure Account
- .NET Core 3.0

## Step 1. Create a new Project
First create a ASP.NET Core Web aplication Project with individual user account authentication.

![](/img/1.1.gif)

To follow up with this tutorial add the follwing code to Startup.cs. This makes sure the database migrations are executed when te application is started.

```
public void Configure(IApplicationBuilder app, IWebHostEnvironment env, ApplicationDbContext applicationDbContext){

// somewhere in the method

applicationDbContext.Database.Migrate();
```
## Step 2. Publish to Azure
After the project is created we can publish it directly from visual studio to Azure from the Solution Explorer. In this tutorial we publish it as an Azure App Service.

![](/img/2.1.gif)

After the project is published we receive a publicly available url with an error because .NET Core 3.0 is currently not enabled by default.


By now the project should also be visible in the Azure Dashboard at App Services -> YOUR_PROJECT_NAME.


## Step 3. Enabling .NET Core 3.0
We can enable .NET core 3.0 at Development Tools -> Extensions -> ASP.NET Core 3.0 (x86) Runtime

![](/img/3.1.gif)

After the extension is enabled we need to restart the application. After the restart is finished the application should work.

![](/img/3.2.gif)


## Step 4. Creating a database

Now we have to create a Database on Azure, a Basic database plan fits our needs.

![](/img/4.1.gif)

## Step 5. Connecting the App with the database

After the database is created we can add it to our project. This can be done in the publish section of visual studio. Make sure the given connection string name is the same as configured in Startup.cs

![](/img/5.1.gif)


