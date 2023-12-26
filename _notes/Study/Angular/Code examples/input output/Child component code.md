

### **Back to Index** : - [[@Input and @Output Operator]]

---

- Lets see the child component html and ts code.

```html
<div class="card">
    <div class="card-header">
       Child Component Section
    </div>
    <div class="card-body">
        <form>
            <div class="form-group">
                <label for="name">Name from Parent</label>
                <input type="text" class="form-control" 
                    name="Name" id="name" [(ngModel)] = "userDetailsfromParent.name">
            </div>
            <div class="form-group">
                <label for="department">Department from Parent</label>
                <input type="text" class="form-control" 
                    name="Department" id="department" [(ngModel)] = "userDetailsfromParent.department">
            </div>
            <div class="form-group">
                <label for="testString">Test String from parent</label>
                <input type="text" class="form-control" 
                    name="testString" id="testString" [(ngModel)] = "testStringfromParent">
            </div>
        </form>
    </div>          
 </div>

```

<br><br>
- Now lets see the ts code:

```ts
import { Component, Input, OnChanges, OnInit, SimpleChanges } from '@angular/core';
import {UserModelforIOEx1} from 'src/app/Data-Models/UserClasses';

@Component({
  selector: 'app-input-example-child',
  templateUrl: './input-example-child.component.html',
  styleUrls: ['./input-example-child.component.css']
})
export class InputExampleChildComponent implements OnChanges{

  @Input() userDetailsfromParent : UserModelforIOEx1;

  @Input() testStringfromParent : string = '';

  constructor(){
    this.userDetailsfromParent ={
      name : "",
      department : ""
    }
  }

  ngOnChanges(changes: SimpleChanges): void {
    console.log('i m here');
  }
}

```
