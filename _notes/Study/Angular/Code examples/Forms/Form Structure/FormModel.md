
### Back to Forms : [[Forms Explained]]

---

### **Theory**:

- This a data structure that represents the HTML form in the component class.
- The structure of the `FormModel` represents the form and input elements inside the template.
It can be vaguely compared with the DOM that gets formed for an HTML page.
- In most cases, each input element within the HTML form has a corresponding `FormControl` in the `FormModel`.
<br><br>
- FormModel also does the below: 
	- It retains the state such as dirty/touched etc.
	- It retains the value of any input element as the user types input any input element.
	- It also tracks all the FormGroup and nested FormGroup within the form along with their states and values.

<br><br>

***Some important points:***

- We `SHOULD NOT` confuse the `FormModel` with the `data-model` used for the data-binding.
We can use the `Form-model` contents anytime to know the state/value of a `FormControl` or a `FormGroup`.
<br><br>

- **Question:** Will the `FormModel` be the same for both the `template-driven` forms and `reactive` forms?  
<br>
  **Answer :** ***YES***. <br>
	Ultimately the `FormModel` is a representation containing the information related to a form. Hence it would be the same for both the form approaches. `The difference lies in the manner in which they are created.`


---

### **How do we access and see the `FormModel`in the `component.ts`**:

- We can pass the form using its ID in the `submit` method and then in that method we get an input parameter of type `ngForm`. In that we can see the form Model with all the states of the overall form as well as the individual form controls.
  Lets see the below code:

```html
<form #valChangedForm = "ngForm">
            .....
            .....
    <button [disabled]="valChangedForm.pristine" 
	    class="btn btn-lg btn-primary mb-2" 
	    type="submit" 
	    (click)="valChanged(valChangedForm)">Value Changed
	</button>
</form>
```

<br><br>

```ts
valChanged(valChangedForm : NgForm){
    console.log(valChangedForm.form.value);
    console.log(valChangedForm);
}
```

<br><br>

**How FormModel looks in console:**

```DOM
>> Object { _rawValidators: [], _rawAsyncValidators: [], _onDestroyCallbacks: [], callSetDisabledState: "always", submitted: false, _directives: Set(3), ngSubmit: {…}, form: {…}, __ngContext__: 5 }​
	__ngContext__: 5
	_directives: Set(3) [ {…}, {…}, {…} ]
	_onDestroyCallbacks: Array []​
	_rawAsyncValidators: Array []
	_rawValidators: Array []
	callSetDisabledState: "always"
    >> form: Object { _pendingDirty: false, _hasOwnPendingAsyncValidator: false, _pendingTouched: false, … }
		_composedAsyncValidatorFn: null
		_composedValidatorFn: null
		_hasOwnPendingAsyncValidator: false
		
		>> _onCollectionChange: function _onCollectionChange()​​

		>> _onDisabledChange: Array []
		_parent: null
		_pendingDirty: false
		_pendingTouched: false
		_rawAsyncValidators: null
		_rawValidators: null
		
		>> controls: Object { fullName: {…}, age: {…}, department: {…} }
			>> age: Object { _pendingDirty: true, _hasOwnPendingAsyncValidator: false, _pendingTouched: true, … }
			>> department: Object { _pendingDirty: true, _hasOwnPendingAsyncValidator: false, _pendingTouched: true, … }
			>> fullName: Object { _pendingDirty: true, _hasOwnPendingAsyncValidator: false, _pendingTouched: true, … }
<prototype>: Object { … }
		errors: null
		pristine: false
		status: "VALID"
		>> statusChanges: Object { closed: false, isStopped: false, hasError: false, … }
		touched: true
		>> value: Object { fullName: "anad", age: "12", department: "IT" }
		>> valueChanges: Object { closed: false, isStopped: false, hasError: false, … }
		>> <prototype>: Object { … }
		>> ngSubmit: Object { closed: false, isStopped: false, hasError: false, … }
		>> submitted: true
		>> <prototype>: Object { … }
```


- In the above code we can see that the `FormModel` contains various properties including the form `states`, `validity`, `errors`,`controls` and each controls have the individual control objects which again contains the `states`, `validity`, `value` etc.
	- So using this `FormModel` we have access to a very extensive data related to each form which can be utilised in both HTML and ts files.