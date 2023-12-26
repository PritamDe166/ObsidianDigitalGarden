
#### Back to Index : [[Index- Dot net core]]

---

<br>

### **Structure of the web app**:

- As we have seen, we have created a empty web application using the terminal commands, refer [[Installation and new project]].
- We see that we have generated an application where we have the following files:
	- Program.cs
	- MyDotnetCore1.sln
	- MyDotnetCore1.csproj
	- appsettings.json
	- appsettings.Development.json
	- Properties
		- launchSettings.json
	- obj
	- bin

</br>

- Remember that the Asp.net Core application basically act like `APIs` with or without `views`, i.e. It works on the HTTP `request` and `response`.
- The entry point of the application, either console or web is the `program.cs`. We do not explicitly need to mention the `static void main` because at the time of compilation, it will automatically generate it. So the `program.cs` in our web application will look like below:
</br>

```cs
var builder = WebApplication.CreateBuilder(args);
var app = builder.Build();

app.MapGet("/", () => "Hello World!");

app.Run();
```


</br>

- If we create a console app, also the `program.cs` will also be generated and there also we do not need to mention the `static void main`. We will look at the console app details later.


---

</br>

### **Analysing the `program.cs` in the asp.net core web app**:

- Lets analyse the default generated code one by one.

```cs
var builder = WebApplication.CreateBuilder(args);
var app = builder.Build();

app.MapGet("/", () => "Hello World!");

app.Run();
```

<br></br>


1) The initial statement visible here is `CreateBuilder`. 
- This function generates a builder specifically designed for web applications, known as the `Web Application Builder`. 
</br></br>

- ***So, what capabilities does this builder possess?*** </br>
	The Web Application Builder is responsible for loading 
	- _the configuration environment_  : for example API URLs or server names and configuration is your configuration settings such as connection strings Etc.
	- _default services of a web application_ 

</br></br>

2) Upon invoking the `CreateBuilder`, an instance of the `web application Builder` is obtained, denoted by the variable `builder`. 
- Through this variable, one can conveniently access: 
	- `configuration settings`
	- `services` 
	- `environment variables`

```cs
builder.Environment
builder.Services
```


</br></br>

3) After configuring your Builder, you need to invoke the `Build()` method. 

- This method generates an instance of a web application, which is stored by the variable `app`. 
- Consequently, this "app" variable serves as a reference to the web application object, allowing you to customise the application's `middlewares`. 
	A more in-depth explanation of middleware and their functionality will be provided in the dedicated section on middleware. 
- However, for now, concentrate on the fundamental concept conveyed by this statement: 
	- Upon receiving a request at the localhost:port number, the expected response should be `hello world`. 

</br></br>

4) To initiate the server, the `run()` method must be called; neglecting to do so will prevent the server from starting. 
- Now we execute our application by the terminal commands.
```cmd
dotnet build
dotnet run
```

- This action initiates the internal Kestrel server, automatically launching the browser to run the URL at localhost with a random port number, displaying the corresponding response.