</br></br>

### **Back to Index** : - [[Index- Angular Topics]]

---
</br>


### **ngModel**:

- The `ngmodel` directive binds the value of HTML controls (input, select, textarea) to application data. 
- With the `ngModel` directive you can bind the value of an input field to a variable created in Angular. The binding goes both ways. If the user changes the value inside the input field, the Angular property will also change its value.

- The `ngmodel` directive is not part of the Angular Core library. It is part of the `FormsModule` library. You need to import the FormsModule package into your Angular module. 
  So we need to have `FormsModule` imported in order to use `ngModel`.

```ts
import { FormsModule } from '@angular/forms';
```

- Lets see a small example for this:

```html
<input type="text" class="form-control" name="fullName" [(ngModel)]="loginData.fullName">
```

- In the above example, we have a textbox where we have used the `ngModel` to bind the data with the data model `loginData.fullName` 
- This will be a 2-way binding, and hence we use the `[()]` brackets.
- This data model as we know is initialised in the component ts file.

```ts
  loginData : loginUserDetails = {
    fullName : "",
    email : ""
  }
```

</br></br>

---

### **ngModelChange**:

- When `[(ngModel)]` is called, it basically does a 2 way binding. When the data model value gets changed in the `ts` file, then it gets reflected in the UI element.
- Also when anything gets changed in the UI, it changes the data model in the ts file. This happens because `ngModel` internally fires the `ngModelChange`.

```html
	<input type="text" class="form-control" name="stringData" 
		[ngModel] = "stringData" (ngModelChange)="sendtoParentEmitter($event)">
```

- Lets assume a scenario, where we want to send a value from child component to parent though `@Output`, we would want to trigger the `emit` when the changes happen in the model `stringData`.
- In this scenario, we would use the `ngModelChange` where we will be calling the `sendtoParentEmitter` function and inside that function we will need to explicitly assign the value of the model like below.
  And then we emit the data to the parent component.
  
```ts
	sendtoParentEmitter(e : any){
	    this.stringData = e;
	    this.sendToParent.emit(this.stringData);
	}
```


---

</br></br>

***IMPORTANT***:

- Another important thing to keep in mind is this; we have used the name attribute in the input tag. This is very important because if we do not use the `name` attribute whenever we are using the `ngModel`, then it will not bind the input value to the component properly, specially if we are using this input tag inside a form element.
- The reason behind this is, the “form” tag, stores and uses the values like a “key-value” pair and the “name” tag acts as a “key” to the input values.
  We will see the usage of this inside a form in the next sessions. 
	
- There is work around to this and to get rid of the error caused due to non-usage of the name tag.
  By using something called 
```html
  ngModelOptions = “{standalone : true}”
```
	
	
- This makes sure that whatever value you enter in the form, still in the backend, the form remains empty and the values you enter in the input tags are not carried by the form element. 
  You can send those values in any model individually to the component which we are not going to discuss in this section.
  
- Hence it is a good practice to use the `name` tag in the input elements whenever we are using `ngModel`.
