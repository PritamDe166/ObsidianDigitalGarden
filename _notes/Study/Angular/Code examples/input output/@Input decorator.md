

### **Back to Index** : - [[@Input and @Output Operator]]
</br>

---


- Whenever we are sending data from parent to child we use the input decorator. We can think of this as whenever the child component is taking anything from the parent component, `we use the input directive in the child component`.

- Lets see an example where we are transferring a simple string in the child component.

</br>

***In the child component `.ts` file***:

```ts
import { Component, Input } from '@angular/core';
...

export class InputExampleChildComponent implements OnChanges{
  
  @Input() testStringfromParent : string = '';
  
}
```


- So we have a variable `testStringfromParent` which is basically the `input` and will store the details when it is passed from the parent.

</br>

***In the parent component***:

- In the parent HTML where we mention the `child component selector` we will mention the input variable from the child component and as well the value in the parent component which will be passed to the input variable in the child component.
- Lets see the below example.

_Parent Html_:

```html
	<div class="form-group">
        <label for="testString">test</label>
        <input type="text" class="form-control" name="testString" id="testString" [(ngModel)] = "test1">
    </div>
......
......
......
	<div class="col-md-5">
        <app-input-example-child [testStringfromParent] = "test1"></app-input-example-child>
    </div>
```

_Parent `.ts`_:

```ts
	test1 : string = "";
```

</br>

_Explanation_:

- The target that we are trying to achieve here is this:
	  Lets start with a textbox in the parent component and we use `[(ngModel)]` to bind it to a variable `test1`. We want to make this variable and its value available to the child component.

- This will be achieved when we use the `[testStringfromParent] = "test1"` in the selector of the child that we use in parent html.

</br></br>

***Child component `.ts`***:

_In the child component `ts`:_

```ts
import { Component, Input } from '@angular/core';
....

export class InputExampleChildComponent {

  @Input() testStringfromParent : string = '';
...

}
```

- Firstly we will need to import the `Input` from the `@angular/core`.
- Then we have declare a variable of type string, with the `@Input` decorator. This will be bound with the parent component value through the `selector` that we have mentioned in the parent component html.

_In the child html_:

- In the child html, we have another textbox where we will populate the values incoming from the parent using the `[(ngModel)]`.

```html
	<div class="form-group">
		<label for="testString">Test String from parent</label>
		<input type="text" class="form-control" name="testString"[(ngModel)] = "testStringfromParent">
	</div>
```


- When the values get changed in the parent textbox, the variable its bound to `test1` will get changed immediately due to `change detection`. 
  As soon as it gets changed, the `@Input` variable in the child component, i.e. `testStringfromParent` will also gets changed and hence the value gets available in the child component.
