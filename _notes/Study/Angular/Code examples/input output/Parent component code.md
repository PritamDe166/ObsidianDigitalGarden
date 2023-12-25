
### **Back to Index** : - [[@Input and @Output Operator]]

---


### **Parent Component**:

- Lets take a look at the parent component html and ts.

```html
<br>
<div class="row justify-content-evenly">
    <div class="col-md-5 ">
        <div class="card">
            <div class="card-header">
              Parent Component section
            </div>
            <div class="card-body">
              <div class="card">
                <div class="card-body">
                  <form #userForm = "ngForm">
                      <div class="form-group">
                        <label for="name">Name</label>
                        <input type="text" class="form-control" 
                          name="Name" id="name"
                          [(ngModel)] = "userData.name"
                        >
                      </div>
                      <div class="form-group">
                        <label for="department">Department</label>
                        <input type="text" class="form-control" 
                          name="Department" id="department"
                          [(ngModel)] = "userData.department"
                        >
                      </div>
                      <div class="form-group">
                        <label for="testString">test</label>
                        <input type="text" class="form-control" 
                          name="testString" id="testString"
                          [(ngModel)] = "test1"
                        >
                      </div>
                      <br>
                      <button type="submit" class="btn btn-primary" (click)="bindData(userForm)">Submit</button>
                  </form>
                </div>
              </div>              
            </div>
          </div>
    </div>
    <div class="col-md-5">
        <app-input-example-child [testStringfromParent] = "test1" [userDetailsfromParent] = "userData"></app-input-example-child>
    </div>
</div>

```


</br></br>
- Now lets see the `.ts` file:

```ts
import { Component} from '@angular/core';
import {UserModelforIOEx1} from 'src/app/Data-Models/UserClasses';
import {FormsModule } from '@angular/forms';

@Component({
  selector: 'app-input-example-parent',
  templateUrl: './input-example-parent.component.html',
  styleUrls: ['./input-example-parent.component.css']
})
export class InputExampleParentComponent {

  userData : UserModelforIOEx1 = {
    name : "",
    department : ""
  }

  test1 : string = "";

  //constructor
  constructor(){
  }

  bindData(form : any){
    //console.log(this.userData);
    //this.userData = {...this.userData, name : this.userData.name};
  }
}

```


