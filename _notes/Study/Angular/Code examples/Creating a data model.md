

### **Back to RouteGuard** : - [[Implementing token for login]]

---


### **Interface**:

- In typescript, we can create a data model using what is called an `interface`.
- It is basically a data type that can hold the structure to act as a data model.
- An interface is a TypeScript feature used to define the structure or contract that an object must adhere to. It allows you to specify the properties and their types that an object should have. 
  Interfaces are particularly useful in Angular for defining data models, ensuring a consistent structure for objects used within the application.
	- ***Defining Interfaces for Data Models:***
		In Angular applications, you often work with data models, such as representing user information, product details, etc. Interfaces help define the structure of these models. 
		
	- ***Type Safety:***
		When you define an interface for a data model, TypeScript enforces that any object implementing that interface must have the specified properties with the correct types. This helps catch potential errors during development and provides better code readability.
		
	- ***Services and Components:***
		Interfaces are commonly used in Angular services and components, especially when dealing with data retrieval from APIs. For instance, a service might fetch data from an API, and the interface defines the expected structure of that data.

	- ***Component Input and Output:***
		Interfaces are also used when defining the input and output properties of Angular components. This helps in providing clear contracts for how components should be used and how they communicate with the outside world.

- In summary, interfaces in Angular play a crucial role in defining clear contracts for the shape of data and objects within your application, promoting type safety and making your code more maintainable.

<br><br>

***Defining an Interface***:
```js
//inside our dataModel.ts or dataModel.model.ts
	export interface loginUserDetails{
	    fullName : string | undefined;
	    email : string | undefined;
	}
```


<br><br>
***Using an interface***:

```js
import { loginUserDetails } from 'src/app/Data-Models/UserClasses';


export class LoginComponent {
	  loginData : loginUserDetails = {
		    fullName : "",
		    email : ""
	  }
	  ....
	  ....
}
```

>[!tip] You need to set a default value when you use an interface in ur component class. Otherwise the properties inside will be undefined. If you use it in HTML without setting any default value, then it will give error in HTML.

---

### **Class**:

- We can always use a `class` as a data model. 
- Remember that class in a reference type and if you use a class as a data model, it will need to be instantiated in the component that you want to use it. For eg,:
```ts
export class UserModelforIOEx1 {
    name : string | undefined;
    department : string | undefined;
}
```

- Inside the component class:
```js
import {UserModelforIOEx1} from 'src/app/Data-Models/UserClasses';

export class InputExampleParentComponent {
	userData : UserModelforIOEx1 = new UserModelforIOEx1();
	...
	...
}

```

>[!tip] If you use a class as your data model, you don't need to assign a default value but you need to use the `new` keyword to create an object. Because what it does it that it calls the constructor by default and assigns null to all the properties anyways.














