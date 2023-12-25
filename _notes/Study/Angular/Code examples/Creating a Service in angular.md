
### **Back to RouteGuard** : - [[RouteGuard explaination]]

### **Back to Index** : - [[Index- Angular Topics]]

---

### **Creating a service file**:

- Like a component, we can create a service file from the console using the command:
```console
ng g s services/login-auth
```

- So this command will create the file `login-auth.service.ts`.  
- _Its very important to note that for a file to be acting as a service, it has to be injected to the root._ When you create a service though the above command, it will be automatically injected to the root. If you manually create it, makes sure to include the below:

```ts
	import { Injectable } from '@angular/core';
	
	@Injectable({
	  providedIn: 'root'
	})
	
	export class LoginAuthService {
		.....
		.....
	}
```


</br></br>

---

### **Using a service in a component**:

- In order to import a service in a component, first we need `import` it.
- Then we need to do the `dependency injection` which is basically injecting it in the constructor and create a reference to the service class to be used across the component.

```ts
import { LoginAuthService } from 'src/app/Services/login-auth.service'

....
export class LoginComponent {
	constructor(private loginAuth : LoginAuthService){
	}
}
//Use the reference "loginAuth" to call the functions in the service class

this.isLoginValidated = this.loginAuth.validateUserDetails(this.loginData);

```


- These are the essential steps to use any service.
