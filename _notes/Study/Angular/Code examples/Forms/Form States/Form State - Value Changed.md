
### Back to Forms : [[Forms Explained]]

---

### **Value Changed - Explanation**:

- The statuses for tracking if the value of a certain form group or form control has changed. 
  
1) **Pristine**: If the input field value is unchanged
2) **Dirty** : if the input element's value has changed.

>[!tip] For all these states, if all the input elements are untouched, then the form also will be pristine. And if any one of the input elements in a form is dirty, then the entire form is dirty.


---

</br></br>

### **Code Example**:

- Lets see a basic code example of how we have accessed the states of a form and its controls:

```html
	<form #valChangedForm = "ngForm">
			<div class="form-group">
				<label for="fullName">Full Name :</label>
				<input type="text" class="form-control" 
				#fullName = "ngModel" 
				name="fullName" id="fullName" [(ngModel)]="employeeDetails.fullName">
			</div>
			Pristine : {{fullName.pristine}}, 
			Dirty : {{fullName.dirty}}
			<br><br>
			<div class="form-group">
				<label for="age">Age :</label>
				<input type="text" class="form-control" 
				#age = "ngModel" name="age" id="age" [(ngModel)]="employeeDetails.age">
			</div>
			Pristine : {{age.pristine}}, 
			Dirty : {{age.dirty}}
			<br><br>
			<div class="form-group">
				<label for="department">Department :</label>
				<input type="text" class="form-control" 
				#department = "ngModel" name="department" 
				id="department" [(ngModel)]="employeeDetails.department">
			</div>
			Pristine : {{department.pristine}}, 
			Dirty : {{department.dirty}}
			<br><br>
			<button [disabled]="valChangedForm.pristine" 
				class="btn btn-lg btn-primary mb-2" 
				type="submit" (click)="valChanged(valChangedForm)">Value Changed
			</button>
    </form>
```

