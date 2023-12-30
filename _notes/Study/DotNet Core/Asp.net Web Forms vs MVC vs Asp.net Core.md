
#### Back to Index : [[Index- Dot net core]]

---


### **Asp.net Web Forms vs MVC vs Asp.net Core**:


**Asp.net Web Forms**

- ASP.NET Web Forms has been available since the inception of the .NET Framework in 2002. Subsequently, Microsoft introduced ASP.NET MVC in 2009, followed by ASP.NET Core in 2016. When discussing ASP.NET Web Forms, it is important to note its significant performance drawbacks. The framework exhibits slower performance primarily due to server events and view state.

- ASP.NET Web Forms inherently strives to make the web stateful rather than stateless. Consequently, each page must store its state, which is maintained in the form of view state. The view state object needs to be transferred between the client and server for every request. While this may suffice for simple web applications, it becomes a considerable drawback for medium to larger applications due to the increasing weight of view state. The heavyweight view state has to be transmitted between the client and server for each request, contributing to overall slower performance.

- Moreover, in ASP.NET Web Forms, the server page lifecycle must be executed for every request. This entails a series of server events, making the process complex and heavyweight. This complexity is another factor contributing to the framework's slower performance. Additionally, ASP.NET Web Forms poses challenges for unit testing, adding another layer of difficulty and further detracting from its overall usability.
</br></br>



**Asp.net MVC**

- With all these considerations in mind, ASP.NET MVC was introduced in 2009. ASP.NET MVC utilises the Model-View-Controller (MVC) pattern, providing a clean separation of concerns. This separation enables independent testing of models, views, and controllers, allowing for unit testing of controllers, models, and views.

- However, ASP.NET MVC has its drawbacks. It is built on top of components developed earlier for ASP.NET Web Forms, such as system.web.dll. This reliance on existing components, like the mentioned DLL, results in somewhat slower performance and a lack of support for cross-platform deployment. Essentially, hosting ASP.NET MVC applications on operating systems other than Windows becomes challenging or even impossible due to its tight coupling with the .NET Framework.

- ASP.NET MVC is an integral part of the .NET Framework, making it problematic for hosting on alternative operating systems. To address these challenges, there arose a need to enhance performance, embrace cloud friendliness, and achieve cross-platform compatibility. These became the design goals for ASP.NET Core.

</br>


**Asp.net Core**

- ASP.NET Core's first version was released in 2016, and the recent version is 6, denoted as ASP.NET Core 6. In the future, I will ensure the release of lectures covering newer updates of ASP.NET Core, such as versions 7 or 8. ASP.NET Web Forms and ASP.NET MVC primarily support Windows on the host, making it challenging or even impossible to use other operating systems on the server, particularly Linux. However, ASP.NET Core was designed as cross-platform from the beginning, built from scratch, as it works based on .NET Core, which itself is cross-platform.

- ASP.NET Web Forms is not cloud-friendly because it was developed at a time when cloud computing was not prevalent. Although ASP.NET MVC, being a newer release, is not 100% cloud-friendly due to its dependence on some components of the .NET Framework available only for Windows, ASP.NET Core has first-class support for clouds like `Microsoft Azure`. This allows you to host your application on Microsoft Azure without needing any server infrastructure on your development centre.

- From its inception, ASP.NET Web Forms is not open source, 
	- whereas ASP.NET MVC and ASP.NET Core are open source. However, ASP.NET Core has gained more popularity in the open-source community compared to ASP.NET MVC because the .NET Framework itself is not open source, while .NET Core is. Both ASP.NET MVC and ASP.NET Core are free for production-level applications.

- ASP.NET Web Forms follows an event-driven programming approach, where, for instance, clicking a button triggers a server-side click event. 
	- In contrast, ASP.NET MVC and ASP.NET Core support the Model-View-Controller (MVC) pattern. Additionally, in ASP.NET MVC, you can optionally add the `Dependency Injection pattern`, but ASP.NET Core has built-in support for Dependency Injection. More details about Dependency Injection will be covered in a later section. Furthermore, ASP.NET Core is highly unit-testable and is a modular framework.




