
### Back to Forms : [[Forms Explained]]

---

### **Theory**:

- `FormGroup` tracks the states and values of a group of form controls. 
- The form itself is also a managed group of input controls and hence that also gets tracked using a `formgroup`. 
- But there can be other `FormGroups` which consist of a group of `formControls` such as a group of email ids or a group of addresses.
	
- There can also be FormGroups nested inside other FormGroups. So for clarity we can call the form’s `FormGroup` as the root FormGroup.
	
- These form building blocks are instances of classes that define the `FormModel`. More about `FormModel` here : [[FormModel]].

<br>




