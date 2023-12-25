
### Back to Forms : [[Forms Explained]]

---

### **Theory**:

- `FormControls` are the individual user controls that are present in a form. 
- A group of `FormControls` can be clubbed together and this grouping will be called as a `FormGroup`. 
- Like a `form` itself, each individual `FormControl` can also have various states like `dirty`,`pristine` etc. which can be accessed by assign the `FormControl` with an `ID`. 
	- We can assign an ID to a `FormControl` using the `ngModel` directive. Lets see the below example.

```html
<form #valChangedForm = "ngForm">
	<div class="form-group">
		<label for="fullName">Full Name :</label>
		<input type="text" class="form-control" 
		#fullName = "ngModel" name="fullName" id="fullName" [(ngModel)]="employeeDetails.fullName">
	</div>
	Pristine : {{fullName.pristine}}, 
    Dirty : {{fullName.dirty}}
```



- In the above code we see that the we have assigned the id `fullName` to the input textbox with the help of the `ngModel` directive.
- Another important attribute is the `name` attribute as this will dictate the name of the `FormControl` when the `FormModel` is generated.
