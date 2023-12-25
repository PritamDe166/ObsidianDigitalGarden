
### **Back to Index** : - [[@Input and @Output Operator]]

---

- As we discussed the `@Output` decorator is used to send data from a child to a parent. This works a little differently then `@Input`.
- Lets see a basic example where we are sending a string through `@Output`
</br></br>

***In the child component***:

```html
	<div class="form-group">
		<label for="stringData">Data to be sent to parent: </label>
		<input type="text" class="form-control" name="stringData" id="stringData" 
                [ngModel] = "stringData" (ngModelChange)="sendtoParentEmitter($event)">
	</div>
```

- In the above code, we have a textbox which we are binding to the variable `stringData` using the `[ngModel]`. We also have the `(ngModelChange)` which will call the method `sendtoParentEmitter` which will be called when there is any change in the textbox and this is where we are going to emit our changes.
  More about `ngModel` can be found here: [[ngModel and ngModelChange Directive]]

</br>

```ts
import { Component, Input, Output, EventEmitter } from '@angular/core';

export class InputExampleChildComponent {

	@Output() sendToParent = new EventEmitter();
	
	stringData : string = '';
	
	sendtoParentEmitter(e : any){
	    this.stringData = e;
	    this.sendToParent.emit(this.stringData);
	}
....

}
```


- In the above code in our `component.ts` file,
	- Firstly we have imported the `Output` from `@angular/core`
	- Then we create a `@Output` object which points to the `EventEmitter` interface.
	- Then we declare the variable `stringData` where we will be our model for the textbox data.
	- Next we have created the function `sendtoParentEmitter` which will be called when there are any changes in the textbox. Inside this function we will be :
		- Assigning the incoming parameter in the function to the variable `stringData`.
		- Then we will be `emitting` the data to the parent component using the emit function. 


</br></br>

***In the parent component***:

```html
	<app-input-example-child [testStringfromParent] = "test1" [userDetailsfromParent] = "userData"
        (sendToParent)="parentRecieveEmitter($event)"
    >
    </app-input-example-child>
```

- In the above code, we have to bind the output object to an event in the parent to capture and bind the incoming data to a model in the parent. so we use `(sendToParent)="parentRecieveEmitter($event)"` in our child selector in parent html.
	- In our case, when any value is emitted from the child, it will call the function `parentRecieveEmitter` in the parent's component.

- We can see the differences between how we handle the `input` and `output` in the child selector tag in our parent.

</br>

```ts
export class InputExampleParentComponent {

  dataFromParent : string = '';

  parentRecieveEmitter(e : any){
    this.dataFromParent = e;
  }

```


- In the parent component ts file, we see that we have a model  `dataFromParent` to bind the data incoming from the child.
- Then we have the function `parentRecieveEmitter` which will be called when the child emits any value. Here we will be :
	- Assigning the model `dataFromParent` with the the value incoming in the input parameter of the function.



