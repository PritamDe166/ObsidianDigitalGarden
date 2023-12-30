
#### Back to Index : [[Index- Dot net core]]

---


### **`Kestral` and other servers**:


- `Kestrel` is the default http server for asp.net core application.
- ASP.NET Core applications need a server to handle incoming requests and send responses. 
- `Kestrel` serves as the default cross-platform HTTP server for ASP.NET Core applications, functioning as both a `development server` and a `production application server` capable of handling requests from the actual internet. 


>[!success] However, most of the cases in the real world, you will use the kestrel as an application server and development server only.

</br></br>


**Reverse proxy Servers**:

- In production, you will be using `reverse proxy servers`.
- During development, the developers use Kestrel as a development server, meaning you will be writing some ASP.NET Core code, and you will be testing and running the application by using the default server called Kestrel.

- After completion of the development, you require to push the code into the production server which can receive the request from the internet anywhere in the world. So there you will be using reverse proxy servers such as `IIS`, `nginx`, or `apache` as `Reverse proxy servers`. The architecture looks like this.

</br>

![[Screenshot 2023-12-26 at 10.52.46 PM.png]]



***Explanation of the architecture***:

_With Kestral:_

- With `Kestrel`, the http request will be received from local network or internet. 
- The kestrel will receive that request and it will forward that request to the application code. The kestrel will receive the request and fills the information in the form of an object, and that object is called as `http context`.
- So the kestrel prepares a `http context` object which contains the details of the request and sends that http context to the application code. 
  The application code can receive that context and can process based on that and can provide the response or result back to the kestrel. Then the kestrel sends the same response back to the internet or the client. 
  So this is the general process that happens with kestrel.

***NOTE***:</br>
- `Kestrel` doesn't support some of the advanced features that are required on the internet these days, such as `load balancing` and `URL rewriting`. 
- These types of features are expected on production servers, but they are not supported by Kestrel by default.

>[!tip] Most of the websites today use a `reverse proxy server`, meaning that the actual request from the client will be received by a reverse proxy server such as `IIS`, `nginx`, or `apache`.


</br>

_Reverse proxy servers:_

- The `reverse proxy servers` offer some of the advanced features on internet such as `load balancing`, `url rewriting`, `authentication`, `caching` etc. 
- And these servers transfer the same request to the actual application server that is kestrel. 
- In that way even though the kestrel can actually receive the request from internet it won't do that in the real-world cases. 
- In most of the production scenarios we prefer a `reverse proxy servers` because of these advanced features. And that `reverse proxy server will transfer the request to the kestrel`. And then as usual the kestrel receives the request and prepares `http context` and that context object contains the details of the request such as `request body` or `request headers` or the `session` or `cookies` etc. 
- And then the application code receives the request along with the context and can execute some code and can provide the response back to the kestrel. And the kestrel as usual sends the same response back to the reverse proxy server. And then the same response will be sent back to the actual client who sends the request. So in the real production scenarios this is the process what happens.

---
</br></br>


***NOTE*** </br>
- You can simulate the features of a reverse proxy server during development as well by using a dummy reverse proxy server called IIS express. 
- IIS express simulates IIS, meaning it acts as a reverse proxy server which can receive the request and forward the same to Kestrel. Of course, during development, it is just an option whether to use IIS express or not.

</br></br>

- Now how do we know that that kestral server launches by default as soon as the application launches.
- When we run the application using the `dotnet run` terminal command, we see that the `hosting` log is generated in the terminal like this:
```cmd
❯ dotnet run
Building...
	info: Microsoft.Hosting.Lifetime[14]
	      Now listening on: http://localhost:5018
	info: Microsoft.Hosting.Lifetime[0]
	      Application started. Press Ctrl+C to shut down.
	info: Microsoft.Hosting.Lifetime[0]
	      Hosting environment: Development
	info: Microsoft.Hosting.Lifetime[0]
	      Content root path: /Users/pritam/Coding/DotNet Projects/Dotnet core empty web/MyDotnetCore1
```

- This is the launching of the `kestral` hosting server which makes the application available at `localhost:5018` to recieve request from the browser.
- Post that when we sent the request for a route from the browser by typing the route url like `http://localhost:5018/` and that returns the result `Hello World!!`, because in our default code we have the output for this route as `Hello World`. 
  Suppose we mention another route like `/home` and return something, like `Hello Home!!`, we will get the response once we enter that URL `http://localhost:5018/home`.

</br></br>

***POINTS TO REMEMBER***:</br>
- So the order of execution in our development server is this:
	- When we run the application, the `kestral` server gets launched by default and makes the application code available to receive requests in the `localhost` port, which is basically hosting the API to make it available to receive HTTP requests and provide response.
	- Now when we enter the URL in the browser, we will get the response accordingly.
	  </br></br>
- Always try to visualise the Asp.net Core app as being an API like architecture, with or without a view. We can write the view in `Razor pages` or `Blazor` or other frontend languages like `Angular`, `React` etc. 
</br></br>
- In Production, the application will be hosted though the `reverse proxy servers` and we will have the URL always available to receive requests and send responses.