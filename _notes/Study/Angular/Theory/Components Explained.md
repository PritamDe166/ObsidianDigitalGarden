
### **Back to Index** : - [[Index- Angular Topics]]

---

### _Topics in this page_:

- [[#_Intro_]]
- [[#_Why to use it_]]
- [[#_Creating a component_]]
	- [[#Manually]]
	- [[#Automatically]]


---

### _Intro_:

- Components are the building bricks of every angular application. When we see any UI we see many things such as a navbar, menu, login form, etc. These can be divided into separate components to make up a complete application.
 <br>
- It includes classes, and methods and can have a template associated with it.
 <br>
- Bind from class → template and template → class

---

### _Why to use it_:

- Organised code
- Break up the UI into manageable parts
- Contains methods, properties
- Promotes reusability and readability.

---

### _Creating a component_:

#### Manually:

- We can create a folder and let's name it components
- We need to create a `.ts` file and let's name it `user.component.ts`.
- Firstly we need to import the “component” from the “angular/JSON” package, so at the top of the `.ts` file, we write:

````ts
import { Component } from “@angular/core”;
````


- Next, we have to mention the `template URL`, the `selector` and the `styleUrls`
 <br>
- Then we need to create the component class:
````ts
export class UserComponent {
}
 ````

- This class will hold all the variables, methods, and events for that component.
We will also need to create an html file for the component.

Now that we have created the component, we need to make sure that the component reference and name is present in the `app.module.ts`. 
 <br>
> We need to import the component reference to this file and also mention the component name in the declarations array as seen below:

 <br>
````ts
@NgModule({
  declarations: [
    AppComponent,
    NavbarComponent,
    LoginComponent,
    HomeComponent,
    ParentRouterOutletComponent,
    TemplateDrivenComponent,
    ReactiveFormsComponent
  ]
````


### Automatically:

- We can do all these automatically through the below command in the terminal:
 <br>
````cmd
ng g component components/../user
````

 <br>
- This will generate `.ts`, `.html` and `.css` files in the mentioned folder. It creates a class for the component and also refers to it in all the required files.


---


### Back to Top : [[#_Topics in this page_]]
