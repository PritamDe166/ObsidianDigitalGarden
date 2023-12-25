

### **Back to Index** : - [[Growing the Application one by one]]

---

#### ***Page topics:***

1. [[#**Setup a navbar **]]
2. [[#**Explanation of the above code **]]


---

### **Setup a navbar:**

- For our `navbar` we will be checking a sample bootstrap navbar that can be used in any application we make. 
- That `navbar` will contain all the necessary elements like `links`, `dropdowns` etc.
- _Firstly_ lets create a component for `navbar` using the terminal with the below command.
````cmd
	ng g c navbar/navbar
````

- Lets check the below code that we have written in the `navbar.component.html` page.
 <br>
````html
<nav class="navbar navbar-expand-lg navbar-dark bg-dark">
  <div class="container">
    <a class="navbar-brand" routerLink="home">Angular Concepts</a>
    <div class="collapse navbar-collapse" id="navbarNavDropdown">
      <ul class="navbar-nav">
        <li class="nav-item">
          <a class="nav-link" routerLink="inputOutput">Input/Output Example</a>
        </li>
        <!--In order to make the drop down work, we have installed ng-bootstrap using the terminal. 
          And then we have included the "ngb" directives like "ngbDropdown", "ngbDropdownMenu", "ngbDropdownItem" etc. 
          as we see below-->
        <li ngbDropdown class="nav-item dropdown">
          <a ngbDropdownToggle class="nav-link dropdown-toggle" id="navbarDropdownMenuLink" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
            Forms
          </a>
          <div ngbDropdownMenu class="dropdown-menu" aria-labelledby="navbarDropdownMenuLink">
            <a ngbDropdownItem class="dropdown-item" routerLink="templateDriven">Template Driven</a>
            <a ngbDropdownItem class="dropdown-item" routerLink="reactive">Reactive Forms</a>
          </div>
        </li>
      </ul>
    </div>
    <div class="nav-item mr-3 nav-link p-3">
      <button class="btn btn-outline-danger my-2 my-sm-0" (click)="logout()">Logout</button>
    </div>
  </div>
</nav>
````


---

### **Explanation of the above code:**

1. In this example we are using `bootstrap` css library to create our navbar.
    <br>
2. We will have `links`, on click of which the particular view will be loaded or we can say we would load a particular component in the view. This will be controlled by the `routerLink` attribute that we see the `<a>` tag. 
 <br>
	This is how the `routes` are defined. We can find more details of routing in this link : [[Routing Concepts]]
 <br>	
3. In order to achieve the dropdown in the navbar, we have used `ng-bootstrap`. The details are written in the above code about what are the elements we have used to achieve this.