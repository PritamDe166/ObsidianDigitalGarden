
### **Back to Routing concepts** : - [[Routing Concepts]]


---


### **Route Guard Concepts:**

- In Angular, a route guard is a mechanism to control navigation to and from certain routes. It allows you to perform actions or checks before a route is activated, preventing navigation or allowing it based on certain conditions. 

- _First and foremost_, we will need to generate a route guard. So just like we do it for components:

```cmd
ng g g routeGuardExample
```

- We will be asked which type of guard we will like to create.

- ***Lets see all the options one by one:***

---


#### CanActivate:

- In the above command the route guard that will be generated will be a `functional` routeGuard. 
  There are 2 ways in which we can generate and use a routeGuard. They can be `functional` and `class`. 
  
```cmd
ng g g routeGuardExample --functional = true //for functional routeGuard
ng g g routeGuardExample --functional = false //for class routeGuard
```



> [!tip] Note that with Angular 16, the `CanActivate` function has been deprecated and so we would be using the `functional` routeGuard 

---

### ***Setting up login setup for testing RouteGuard:***

- Lets set up our login page, so that when an user logs in, we setup a token and keep it in `localStorage`. 
- Based on that we will make sure that we implement routeGuard on every route.
- Lets discuss the steps here : [[Implementing token for login]].

---

### **Implementing the _RouteGuard_**:

- Now that we have a logic to create a token with successful login, now lets see how to setup the `routeGuard` to make sure that:
	- Only when the token is available in our localStorage, we can navigate to any of the routes. 
	- In case the localStorage doesn't have the token, then the routeGuard will return false and redirect to the login page.

```js
import { inject } from '@angular/core';
import { CanActivateFn, Router } from '@angular/router';
import { tokenKey } from 'src/app/Data-Models/ContantsFile';


export const routeGuardExampleGuard: CanActivateFn = (route, state) => {  
  const router = inject(Router);

  if(localStorage.getItem(tokenKey)){
    return true;
  }
  else{
    router.navigate(['login']);
    return false;
  }  
};
```

- In our routeGuard, we have written the logic discussed above.
- Now lets see the app routing module looks like:

```js
const routes: Routes = [
  {path: '', redirectTo:'home', pathMatch: 'full'},
  {path: 'login', component: LoginComponent},
  {path: 'home', canActivate : [routeGuardExampleGuard] , component: HomeComponent},
  {path: 'templateDriven', canActivate : [routeGuardExampleGuard], component: TemplateDrivenComponent},
  {path: 'reactive', canActivate : [routeGuardExampleGuard], component: ReactiveFormsComponent},
  {path: 'inputOutput', canActivate : [routeGuardExampleGuard], component: InputExampleParentComponent},
  {path: '**', component: PageNotFoundComponent}
];
```

- As we see above we have added the `canActivate : [routeGuardExampleGuard]` with our routes where we want to add a guard to make sure that users can directly navigate to the route, only if the routeGuard logic returns true.

