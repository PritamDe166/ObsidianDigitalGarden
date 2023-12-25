
### **Introduction**:

- ASP.NET Core is a versatile, high-performance, `open-source` framework for developing web applications. 
- By leveraging ASP.NET Core, you gain the ability to create web applications and services of varying scales, ranging from small to medium and complex projects. 
- Additionally, this framework allows you to build REST API services that serve as robust backends for both web applications and mobile applications. With its `cross-platform capabilities`, ASP.NET Core offers a comprehensive solution for modern web development, providing flexibility and scalability across a diverse range of projects.


---

### **Key Features**:

- **Cross-Platform**
	- Asp.net core apps can be hosted on windows, Linux and Mac. 
	- 
	  
</br>

- **Can be hosted on different servers**
	- After completing the development of your ASP.NET Core application, you need to host it. This means you are required to install it on your server machine to start receiving requests from clients and providing responses. 
	- The choice of the operating system on the server machine is crucial. ASP.NET Core primarily supports three operating systems: `Windows, Linux, and Mac`. In most cases, developers use Windows or Mac on their development machines and Linux on the server machine.
	- On the server machine, there must be software capable of receiving requests and providing responses; this is also known as reverse proxies. 
	- ASP.NET Core defaults to supporting Kestrel as the application server and other options as reverse proxies. These reverse proxies include `IIS, Nginx, and Docker`. 
	  `Docker`, in particular, supports various operating systems, allowing you to run either Windows or Linux for your ASP.NET Core application on the Docker platform.

</br>

- **Open Source**
	- It is open source, which means the source code of ASP.NET Core is available on `GitHub` for free. The benefit of this is that you will receive frequent updates for ASP.NET Core.

</br>

- **Cloud-enabled**
	- ASP.NET Core is developed with the cloud in mind. This means it supports `Microsoft Azure Cloud` out of the box.


---


### **Types of projects in Asp.net core**

- **Asp.net Core MVC**:
	- Most web applications are developed using `ASP.NET Core MVC` itself. 
	- This should not be confused with ASP.NET MVC, which was available earlier in the .NET Framework. 
	- Whenever you use the `Model-View-Controller (MVC)` pattern in ASP.NET Core, it is referred to as ASP.NET Core MVC.

</br>

- **Asp.net Core WEB API**:
	- In case you only create controllers with models, but no views, it is referred to as `ASP.NET Core Web API`. 
	- Generally, ASP.NET Core Web API is used to create `RESTful services`. 
	  This enables it to receive requests and provide data as a response, focusing solely on the data and not the views. 
	- This approach allows the frontend to be developed using any web application or mobile application frameworks. 
	  For example, you can create the frontend using frameworks like `React` or `Angular` for web applications, or `Xamarin or Ionic` for mobile applications. 
	  `In all these scenarios, the Web API can function as a backend`.

</br>

- **Asp.net Core RAZOR PAGES**:
	- In addition to that, for simple and page-focused scenarios, Razor Pages are available.

</br>

- **Asp.net Core BLAZOR**:
	- If the development team wishes to utilise the C# language exclusively, both on the `server side` and the `client side`, then the preferred choice would be ASP.NET.

>[!tip] Blazor, out of all these four flavours, the first two are the most commonly used in real-world project development.


