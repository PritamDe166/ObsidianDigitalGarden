
#### Back to Index : [[Index- Dot net core]]

---


### **Creating an Asp.net core app through terminal in macOS**:

- Since we are using macOS, it will be a little different than windows installation. In windows we can just install the dot net core framework with the visual studio and proceeding.
- For our purposes we are going to be using `VS Code` as our editor. and we have also installed the `dot net SDK` and the `C# dev kit`.
  We can check the dot net version installed by using the below command. 
```cmd
dotnet --version
```

**<br>**


---

<br>

### **Create First Asp.net Core app**

- Now lets move to creating our application.
	- We have created a folder and we have opened the terminal at the folder.
	- Now in order to create our application we use the below command. Note that the `web` keyword in the below command refers to an `empty web app`.
```cmd
dotnet new web -n MyDotnetCore1
```

We can create any type of dot net core application like console, mvc etc. using the keywords. 
	  The list of keywords can be found in the below link:<br>
	  <a href="https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-new">
	  Keywords for creating new Dotnet Core application</a>
	  

- Now once the application is created, we will navigate inside the folder using the below command.

```cmd
cd MyDotnetCore1
```

<br>

- Now we can open the code in the VS Code editor using the below command.
```cmd
code .
```

<br>

- Then we can use the below commands to build and run our application.
```cmd
dotnet build
dotnet run
```

We can then navigate to the localhost where the app is hosted. eg. `http://localhost:5018`

<br>

---



