
### **Back to Index** : - [[Growing the Application one by one]]

<br><br>


---

#### ***Page topics:***

1. [[#**Setting up the Routing **]]
2. [[#**Setting Route paths **]]
3. [[#**Setting our `router-outlet` **]]
4. [[#**Active Router Links **]]
5. [[#**Understanding `RedirectTo` and `pathmatch` **]]
6. [[#**WildCard **]]
7. [[#**Route Guards **]]
8. [[#**router.Navigate([''])**]]


---

### **Setting up the Routing:**

1. The first step in setting up the routing will be to setup our `app.routing.module.ts`. This is the page where our routing will be controlled. Here we can see a sample `app.routing.module.ts` file where we have setup a few routing links.
   <br>
2. We see below that we have imported the `RouterModule` and `Routes`. We have `@NgModule`, where we will be setting it up like we did in the below code.
    <br>
3. Next important thing to remember is to have a variable which will be an array of type `Routes`. This will contain a collection of json objects which will act as our routing link collection.
 <br>
```ts
//imports section
import { Component, NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';
import { HomeComponent } from './Home/home/home.component';
import { TemplateDrivenComponent } from './Forms/template-driven/template-driven.component';
import { ReactiveFormsComponent } from './Forms/reactive-forms/reactive-forms.component';
import { InputExampleParentComponent } from './InputOutputExample/input-example-parent/input-example-parent.component';


//Defining all the routes in the json array of type Routes
const routes: Routes = [
  {path: '', component: HomeComponent},
  {path: 'home', component: HomeComponent},
  {path: 'templateDriven', component: TemplateDrivenComponent},
  {path: 'reactive', component: ReactiveFormsComponent},
  {path: 'inputOutput', component: InputExampleParentComponent}
];

//Route module where we need to see the "exports" property 
@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})

//class
export class AppRoutingModule {

}
```



---

### **Setting Route paths:**

1. In the above code we have a variable `routes` where we will have all the route objects. 
   Each of the json object for route has 2 mandatory attributes: `path` and `component`. 
    <br>
2. 
   `Default path`:
   We will need to give a name for the `path` attribute. In the above example we see that we have the value as `''`. This means the default value. This will be loaded once the application is loaded.
   In the other json objects we see that we have provided a name in the `path` attribute. 
    <br>
   `routerLink`:
   This will be referenced everywhere, like we can see in the `navbar` where we have referenced this name in the `routerLink` attribute.
   See it here : [[Navbar example]].

   _Note:_ 
	   In the above example, in the `<a>`, we can use `href` also instead of `routerLink`, but it behaves like a `page refresh` which defeats the purpose of an angular application. Hence we should also use `routerLink`.
    <br>
3. Next attribute is `component` where we will mention the component class name which we want to load for that route.
   For example, we will load `TemplateDrivenComponent` when any link is clicked which has the value `templateDriven` in their `routerLink` attribute.

---

### **Setting our `router-outlet`:**

1. The next important thing is to setup our `router-outlet`. This is where the routes will be loaded whenever links are clicked.
   <br>
2. Consider this as a blank section or placeholder where the content will be loaded whenever we navigate to a route. Remember that we are working with a single page application. So clicking on different routes will not navigate to different pages.
   <br>
3.  The way we have done the setup in our example application is: 
   
- We have created a component named `parent-router-outlet.component` which will act as our `router-outlet` for all our routes.
  So we load this component in the `app.component.html`.

- Then inside the  `parent-router-outlet.component`, we mention the tag 
`<router-outlet></router-outlet>`. This will make sure all the routes are loaded in this component.
<br>
```html
<router-outlet></router-outlet>
```

---

### **Active Router Links:**

- Now let's see another point. We want to make sure that when we click on a nav menu item that directs it to a route, it looks active in UI.
	
- We can use something here called `routerlinkactive` and `routerlinkactiveoptions`. Let's see the code below: 

```html
<a class="nav-link" routerLink="lifecylehooks" routerlinkactive ="active" routerLinkActiveOptions="{exact: true}">Lifecycle Hooks
</a>
```


- The `routerLinkActive` will ensure the router link is active. 
  
- Now when do we want to make it as active? 
  This, we provide in the `routerLinkActiveOptions` where we pass `{exact: true}`. This makes sure that when it's able to find the exact route mentioned in the `routerLink`, only then it will make the routerLink as active.


---

### **Understanding `RedirectTo` and `pathmatch`:**

> [!tip] Understanding the need:

- Lets take a look at the below routes :
```ts
const routes: Routes = [
  {path: '', component: HomeComponent},
  {path: 'home', component: HomeComponent},
  {path: 'templateDriven', component: TemplateDrivenComponent},
  {path: 'reactive', component: ReactiveFormsComponent},
  {path: 'inputOutput', component: InputExampleParentComponent}
];
```

- In our default route, we are saying the we will navigate to _HomeComponent_. 
  It will navigate to _HomeComponent_ , also when the route name is _home_.

- Now lets look at the below 2 Urls:
```html
http://localhost:4200/

http://localhost:4200/home
```

- Both these urls will lead to loading the _HomeComponent_. 
- Our requirement is that when we use the first URL, it should still navigate to _HomeComponent_, but at the same time it should display the proper route i.e. _home_, in the Url

> [!tip] Implementing redirectTo and pathmatch:

- In order to implement this we use the `pathMatch` and `redirectTo`.
  Lets look at the below code.
```ts
const routes: Routes = [
	  {path: '', redirectTo:'home', pathMatch:'full'},
	  {path: 'home', component: HomeComponent},
	  {path: 'templateDriven', component: TemplateDrivenComponent},
	  {path: 'reactive', component: ReactiveFormsComponent},
	  {path: 'inputOutput', component: InputExampleParentComponent}
];
```

- In the above code, lets take a look at the default route, we are saying that when it detects a URL with a default route, it has to be redirected to the route name: _home_. 
  And when it looks for `home` in the route list, it has to find a _full_ match, because that is the value that we have assigned to the `pathMatch`. 

> [!note]
> You can see more details about this `pathMatch` in the below URL:
> 
> https://stackoverflow.com/questions/42992212/in-angular-what-is-pathmatch-full-and-what-effect-does-it-have 
> 


---

### **WildCard:**

- WildCard is where we would want to handle the scenario where the route mentioned in the url doesn't match any of the routes in the list.
- To implement the scenario, we will create a component where we will display a error message whenever we don't find a route.
- Now lets look at the below routes in our `app-routing.module.ts`.
```ts
const routes: Routes = [
	  {path: '', redirectTo:'home', pathMatch: 'full'},
	  {path: 'home', component: HomeComponent},
	  {path: 'templateDriven', component: TemplateDrivenComponent},
	  {path: 'reactive', component: ReactiveFormsComponent},
	  {path: 'inputOutput', component: InputExampleParentComponent},
	  {path: '**', component: PageNotFoundComponent}
];
```


- See the last route where we have the value `**` in the `path`. So this where how we manage our wildcards.


---


### **Route Guards:**

- In Angular, a route guard is a mechanism to control navigation to and from certain routes. 
  It allows you to perform actions or checks before a route is activated, preventing navigation or allowing it based on certain conditions.

- Let us consider this scenario point by point.
	- When we open our application we want it to be navigated to login page url. When the authentication is successful, we want it to be navigated to home page.
	  
	- So on the login button we will authenticate the credentials based on our requirements and then we have made use of a behaviour subject to store the user credentials. 
	  
	- **Aim:** We need to make sure that if we are trying to access any of the routes i.e. home, about, contact us etc. it should not allow us to navigate to that route. Instead it should navigate us back to the login page. 
	  ***Apart from the login page, all the other components should not be accessible with out login in.***

_Angular provides several types of route guards_: 
	Check the details here : [[RouteGuard explaination]]



---

### **router.Navigate([''])**:

- This is a way navigate to any route.
- We can see an example where we have used this to navigate inside the application in `login`.  And we used to navigate out of the application during `logout`.
- In order to use this we will first need to import the `Router` module from angular core.
```js
	import { Router } from '@angular/router';
```

- We can then do dependency injection and create a reference to this `Router` module and then use the `navigate()` method.
```js
  constructor(private router: Router){
  }

  loginFn(formsdata : any){
    ...
      this.router.navigate(['home']);
  }
```


- As we can see that the `navigate` function, it accepts array of routes. So here we can mention the route names where we want to navigate.
