<br>

### **Back to Index** : - [[Index- Angular Topics]]



---

<br>

### **Form Introduction**:

- Forms as we know are used to take user inputs and perform operations with that.
- Forms may consist of textboxes, input fields and submit buttons.
- Lets check a basic form example.

```html
<form #valChangedForm = "ngForm">
                    <div class="form-group">
                        <label for="fullName">Full Name :</label>
                        <input type="text" class="form-control" 
	                        #fullName = "ngModel" 
	                        name="fullName" id="fullName" [(ngModel)]="employeeDetails.fullName">
                    </div>
                    <br><br>
                    <div class="form-group">
                        <label for="age">Age :</label>
                        <input type="text" class="form-control" 
	                        #age = "ngModel" 
	                        name="age" id="age" [(ngModel)]="employeeDetails.age">
                    </div>
                    <br><br>
                    <div class="form-group">
                        <label for="department">Department :</label>
                        <input type="text" class="form-control" 
	                        #department = "ngModel" 
	                        name="department" id="department" [(ngModel)]="employeeDetails.department">
                    </div>
                    <br><br>
                    <button class="btn btn-lg btn-primary mb-2" 
	                    type="submit" (click)="valChanged(valChangedForm)">Value Changed
	                </button>
                
</form>
```


<br>

***Explanation***:

- In the above code we can see a few important points. 
	- We have a `form` tag. Inside the form tag we have a couple of textboxes or input tags and a button.
	- In the `form` tag, we see that we have written something as `#valChangedForm = "ngForm"`.
	  This is very important as this is how we give an id to a form. The `ngForm` directive will assign the id `valChangedForm` to the entire form which can be accessed anywhere in the component html file. We will see more about it in the detailed sessions.
	

---
<br>

### **Form Building Blocks**:

- The important points that we need to understand when dealing with forms are the concepts of :

  [[FormGroup]] <br>
  [[FormControl]] <br>
  [[FormModel]]
		

---


<br>


### **Form States**:

- Before we see the forms types and their examples let's take a look at the various states in a form:
<br><br>

***STATE***:
- There are various states of a form which can be very useful in tracking the various types of states in a form.
	- Value Changed    : [[Form State - Value Changed]]
	- Validity                  : [[Form State - Validity]]
	- Visited                   : [[Form State - Visited]]

