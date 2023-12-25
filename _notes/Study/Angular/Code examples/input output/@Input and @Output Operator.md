
### **Back to Index** : - [[Index- Angular Topics]]


---

### **Quick Theory**:

- As we know that the variables/attributes are local to the components only. If we want to transfer some value between the parent and child then we need to notify the components that the values are incoming from out or outgoing from outside. 

- When we have two related components in a parent-child relationship, we need ways to transfer data between them. Here is where we have `@input` and `@output`.

>[!tip] Always remember when you are talking about “@input” and “@output”, we need to think of it from the child component point of view. 
	- When we are sending any value to a child component, we need to use the “@input”.
	- When we are sending a value out of a child component, we need to use the “@output” and “Event Emitter”.



---

</br>

### **Setting up the parent-child in component**:

- We have created 2 components `input-example-parent` and `input-example-child` components.
- Lets find the code for both the parent and child components here:  [[Parent component code]] and [[Child component code]]

---

</br></br>

### **Intro**:

- As we know that the variables/attributes are local to the components only. If we want to transfer some value between the parent and child then we need to notify the components that the values are incoming from out or outgoing from outside. 
- When we have two related components in a parent-child relationship, we need ways to transfer data between them. Here is where we have `@input` and `@output`.


---

</br>

### **@input Decorator**:

- See the details here: [[@Input decorator]]

---

</br>

### **ngOnChanges()**:

- This is a very important lifecycle event that helps us to track any kind of incoming changes to a component.
- As we know that `ngOnChanges` will be called just after the `constructor` is called as soon as a component is loaded. 
- Post that it will be called whenever any incoming changes are detected through an `@Input`.
- Lets see the detailed info here : [[ngOnChanges details]]


</br>

---

### **@Output Decorator**:

- This decorator is used whenever we want to send data from a child to a parent. For this, we need to have an event emitter in the child and another method in the parent to catch the data. 

- See the details here : [[@Output decorator]]