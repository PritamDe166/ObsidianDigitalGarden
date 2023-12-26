
### **Back to Index** : - [[@Input and @Output Operator]]

<br>

---

### **ngOnChanges()**:

- As discussed, this event is triggered when any incoming changes are detected. The changes will be reflected, but lets say we want to do something whenever we detect a new change has come in the child component. This is where we need to use `ngOnChanges` event.
<br><br>

- Lets see the below code:

```ts
import { Component, Input, OnChanges, OnInit, SimpleChanges } from '@angular/core';

export class InputExampleChildComponent implements OnChanges{

	ngOnChanges(changes: SimpleChanges): void {
	    console.log('i m here');
	}
```

- The above code has been written in the child component. So now, every time we change the textbox value in the parent component, and the `@Input` variable in the child component is changed, then the `ngOnChanges` in called.
<br><br>

- Another thing that we notice is the input parameter that is present in this event and thats `SimpleChanges`. This will contain the details about the incoming changes whenever the `ngOnChanges` is called.
<br><br>

- We will need to import and implement the `ngOnChanges` if we want to use it, like any other lifecycle events.

#### Important example:

- Now that we have understood the basic concept of `ngOnChanges`, lets take a look at an example where we try to send an object from parent to child and we also want the `ngOnChanges` to be triggered.

- In the parent we have an object whose properties are bounded to the textboxes in the parent. 

```html
<div class="form-group">
	<label for="name">Name</label>
	<input type="text" class="form-control" name="Name" id="name" [(ngModel)] = "userData.name">
</div>
<div class="form-group">
	<label for="department">Department</label>
	<input type="text" class="form-control" name="Department" id="department" [(ngModel)] = "userData.department"
>
</div>
```


```ts
import {UserModelforIOEx1} from 'src/app/Data-Models/UserClasses';
....
....

export class InputExampleParentComponent {

	userData : UserModelforIOEx1 = {
	    name : "",
	    department : ""
	}
	...
	...
```

- So we see that the textboxes are bound to the variable `userData` which is of type `UserModelforIOEx1` object. 
  And the properties are bound to the textboxes using the `[(ngModel)]` directive.
  <br><br>

- So when we change the textbox values, this object will hold the values. We will need to pass this data to the child. So we create an `@Input` variable in the child component with the same type.

```ts
import {UserModelforIOEx1} from 'src/app/Data-Models/UserClasses';

export class InputExampleChildComponent implements OnChanges{

  @Input() userDetailsfromParent : UserModelforIOEx1;
  
  constructor(){
    this.userDetailsfromParent ={
      name : "",
      department : ""
    }
  }

  ngOnChanges(changes: SimpleChanges): void {
    console.log('i m here');
  }
....
....
}
```

<br>

- The variable in the child component is `userDetailsfromParent`. So in the parent component we will bind both in the child selector as:
```html
	<div class="col-md-5">
        <app-input-example-child [userDetailsfromParent] = "userData"></app-input-example-child>
    </div>
```
<br><br>

- In this case we will notice that even when the child component is receiving the data in the object, but the `ngOnChanges` isn't getting triggered. 
  This is because, even when the properties inside the object change, the change detector doesn't detect any changes in the object itself and hence the `ngOnChanges` isn't called.

- We can easily do that using the below code:
```ts
	bindData(form : any){
	    this.userData = {...this.userData, name : this.userData.name};
    }
```

- This will make sure that the `ngOnChanges` is called.


